---
title: "samba rar problems"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gompa on 2012-04-19
when trying to unrar someting from my samba ubuntu 12.04 server with my 12.04 desktop i get a crc error: 
```
Cannot find volume /home/gompa/.cache/.fr-vB7DgA/modern.r00
modern.avi - CRC failed
```
but i can unrar things from my widows desktop just fine
and if i extract it localy en open it from the samba server it works fine to

is this a bug or am i missing someting ?

---

### Post by Gompa on 2012-04-19
does nobody else have this problem?

i found it only happens with rars consisting from more than 1 part

it also happens when trying to extract files from a windows pc with a ubuntu 12.04 desktop as client

---

### Post by Gompa on 2012-04-20
after some searching i found 2 existing bugs i think they are related but i'm not sure:
from 9.10: [link ]("https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/365706")
and from 10.10: [link]("https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/639883")

i have the fealing it could be a bug or something verry basic iam forgetting

---

### Post by cariboo on 2012-04-20
Can you unrar the files from the command line?

---

### Post by Gompa on 2012-04-20
thank you for your reply

if i go to the mount directory : ~/.gvfs/downloads
and extract it from there with unrar e it works
but when i try it in Nautilus it opens with File Roller and gives the crc error

i read somewhere that it could be a ram error so i ran memtest but passes without errors

---

### Post by Gompa on 2012-04-21
ok ill go out on a limb here and say its a bug in the file rollers cache
i can recreate the same problem with a fresh install of 12.04 x64

but i have no idea how to fix this

---

