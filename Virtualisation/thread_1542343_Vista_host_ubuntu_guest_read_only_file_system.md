---
title: "Vista host ubuntu guest read only file system"
date: 2010-07-30
forum: Virtualisation
---

### Post by olymacfoogal on 2010-07-30
Hi all,

vbox version 3.1.6

I have Ubuntu 10 running as a guest on Vista. I wanted to switch to using Ubuntu as my host so I decided to dual boot Ubuntu and Vista so I could keep Vista with Ubuntu as a second option in case things went bad.

Following dual boot advice I opened computer management and selected shrink volume on my only drive. It checked for shrinkable volume. I hit cancel as I wanted to check delete a few files in ubuntu in vbox but found that I didn't have permission to delete any of my files!
Read-only file system.

I tried to reboot my vbox machine but now I can only have a maintenance shell as root. I can go into my files but have nowhere to back them up to as I cannot access the network nor can I use the windows shared folder that usually gets mounted. Any ideas on how to recover either the whole virtual harddrive or just my files out of there!

Many thanks for any help
Oly

---

### Post by Meow27 on 2010-07-30
what is your host system running? from what i gather you are on ubuntu (host) 

open up a terminal, type 
```
sudo nautilus
```
(DONT DELETE ANYTHING!)
go to where your VM image is located, right click, click properties.

on the new window, click the permissions tab 

for all groups or for just you (this should be a little straight forward) change the permissions to read and write


hope this helps a bit

---

