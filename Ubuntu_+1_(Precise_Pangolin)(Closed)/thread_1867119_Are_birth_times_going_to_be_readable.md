---
title: "Are birth times going to be readable?"
date: 2011-10-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by qyot27 on 2011-10-22
I just noticed that coreutils 8.13 is in Precise's repo, meaning that using stat on a file will display the Birth time field, barring any patches that disable that field anyway.  Are the other system structures necessary to make sure these values are written/displayed through ext4 (or other birth time/creation time supporting filesystems) also falling into place for 12.04?


EDIT: Even though I had trouble making this work on Natty, on Oneiric it is possible to retrieve the information through a longer process:  *ls -i* to grab the file's inode number, and then *sudo debugfs -R 'stat <#>' device* to display the timestamps, under which crtime is listed, like this:
```
 ctime: 0x4ea142dc:3348eca4 -- Fri Oct 21 06:01:00 2011
 atime: 0x4ea1437b:79580700 -- Fri Oct 21 06:03:39 2011
 mtime: 0x4ea142dc:2ab28f64 -- Fri Oct 21 06:01:00 2011
crtime: 0x4ea14287:4a8c1180 -- Fri Oct 21 05:59:35 2011
```
Just being able to stat files to get that info would be far simpler, though.

---

