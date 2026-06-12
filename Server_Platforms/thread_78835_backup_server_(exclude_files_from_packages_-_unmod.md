---
title: "backup server (exclude files from packages - unmodified)"
date: 2005-10-19
forum: Server Platforms
---

### Post by mirda on 2005-10-19
Hi,

I want to backup my server somehow. I searched the internet but could't find any solution, which backups only files, that are not taken from packages or these which are different.

I need fast recovery and minimum size of backup. I thought about this backup strategy:

1) dpkg --get-selections > list.txt
2) find files that are not from ubuntu packages or files that are from some package but were modified. Backup these.

and this recovery strategy:

a) install ubuntu
b) dpkg --set-selections < list.txt
c) copy over files from step 2

but I don't know how to do "step 2". any help? thanks...

---

