---
title: "Foxpro and wine"
date: 2009-05-20
forum: Wine
---

### Post by klakin on 2009-05-20
I am having a problem with I run foxpro 5 on kubuntu 8-10.
It launches fine and runs, our application works fine.  It works fine on tables that are stored locally.
The problem is when I use CIFS to mount a windows 2003 share.
The table never updates on the local machine.  If the table changes on the server it is never updated on the client until you unmount and mount the drive.
The problem seems to be in the CIFS mounting:
sudo mount -t cifs //10.10.10.11/d /mnt/tmp/ -o user=******,gid=sbtusers

thank you

---

