---
title: "Sources.gz not in gzip format"
date: 2007-04-24
forum: Repositories &amp; Backports
---

### Post by x1a4 on 2007-04-24
Hi,

A Sources.gz file in the Ubuntu repositories seems to be corrupt.  

Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources [385kB]
99% [7 Sources gzip 0]   
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
  Sub-process gzip returned an error code (1)
Fetched 7B in 1s (4B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
Exit 100

---

