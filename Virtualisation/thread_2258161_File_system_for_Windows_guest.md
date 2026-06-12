---
title: "File system for Windows guest"
date: 2014-12-25
forum: Virtualisation
---

### Post by jonnyrobbie on 2014-12-25
I want to have Ubuntu as a main OS and Windows virtualized (using VirtualBox).  Linux uses ext4 fs so that's what I'd like to format most of my partitions to. The question is if I have to reserve a NTFS partition for virtualized Windows, or if the virtual HDD VirtualBox creates can be on a ext4 partition even though Windows itself needs NTFS, because VBox takes care of that.  Thank you

---

### Post by Morbius1 on 2014-12-25
This one:
> or if the virtual HDD VirtualBox creates can be on a ext4 partition even  though Windows itself needs NTFS, because VBox takes care of that.
The XYZ.vdi file it creates to represent the virtual HDD can be on ext4 or any other fileystem but within the VBox environment it will be seen as NTFS.

---

