---
title: "Best file system for small cluster of ubuntu servers"
date: 2015-04-24
forum: Server Platforms
---

### Post by abraxas334 on 2015-04-24
I am trying to work out which file system to use for a small computing cluster (say 1 head node) and 6 compute nodes, running ubuntu server. Also what would be a sensible partitioning on a the raided headnode?
Any thoughts and ideas would be greatly appreciated.

---

### Post by nerdtron on 2015-04-24
Computing cluster? What application are you going to deploy? are they going to be read intensive or write intensive? 

how about files? 
few files but big file sizes?
thousands of files with small files? - try XFS for this

---

