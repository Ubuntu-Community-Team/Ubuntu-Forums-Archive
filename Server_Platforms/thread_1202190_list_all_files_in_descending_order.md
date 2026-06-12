---
title: "list all files in descending order"
date: 2009-07-02
forum: Server Platforms
---

### Post by pzdc on 2009-07-02
Hello,
ubuntu server 8.04

how do I list all files in the system in descending order from all directories? somehow 50% of my allocated quata is used and I can't figure it out where all the space went :(

find / ...........

---

### Post by x22 on 2009-07-02
big files mean big directories: try this in the root directory

"du | sort -nr >DUs &"

then look in the biggest directories

or you could try this

"ls -lR |sort -k 5 -nr >ls-rS &

also in the root directory

---

