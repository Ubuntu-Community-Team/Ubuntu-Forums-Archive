---
title: "quest for a command that does mkdir -p and copies a file"
date: 2019-12-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-08
in cp, i cannot find am option to do, what i often need to do, which is to copy one file (or a few files) from a node in a tree to the same node (relative) in a sparse tree that represents a portion of the source tree.  in some cases i am providing the full path of both the source file and the destination.  so the latter represents the exact target point.  in other cases i don't have the target path and would need to construct it based on the equivalency of the trees, which would be the source and destination apex directories if copying the entire tree.  but so often i only want to copy one file or a few of them.  a tool i have found usable is tar.  running tar at each apex, one building the tar stream over a pipe, and the other extracting from that stream, then naming the file path on the source tar building the stream, gets the proper path created.  but this "solution" does not provide features like no-clubber or backing up re[laced file.

i think i may have to implement my own copy program  any alternative suggestions?

---

