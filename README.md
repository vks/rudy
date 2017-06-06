# Rudy

Rudy is a Judy array implementation in Rust. Judy arrays are highly efficient
word-to-word or word-to-bit maps that adapt well to different data.
The reference Judy array implementation provides a word to word map (JudyL),
set of words (Judy1), string to word (JudySL) and fixed length byte
array to word map (JudyHS). Judy arrays use a compressed 256-radix trie.

The initial Rudy implementation will implement JudyL as RudyMap and Judy1
as RudySet. Because zero sized types can be represented by a RudyMap, it
will be trivial to represent RudySet<T> as a wrapper around a
RudyMap<T, ()>. Future iterations may include JudySL and JudyHS support.

# Differences between Judy and Rudy

Rudy appears to be the first implementation to use generics in the core
library. The [judy-template](https://github.com/mpictor/judy-template)
bindings for C++ allow for automatic conversion to and from words, but
not use of values that need larger storage. Using generics allows for
lower memory usage for smaller types and the usage of larger types,
with possible impact to performance.

# Status

- [x] General library structure
- [ ] Top-level root nodes (Leaf1, Leaf2, VecLeaf)
- [ ] JPM
- [ ] Insertion
- [ ] Get
- [ ] Remove
- [ ] Memory used
- [ ] Shrink
- [ ] Iterators
