---
title: "Virtualization and hardware"
date: 2010-01-10
forum: Virtualisation
---

### Post by wulf-dieter on 2010-01-10
My machine runs XP un one harddisk and ubuntu 9.10 on another hardisk.
My harddisk "D" holds all production data and data needed for production - so I can open a file using xp/ubuntu lets say word/open office manipulate it, save it and afterwards open it from the other side read it etc without any problems.

Using Suns Virtual box in which I ran XP under Ubuntu I do not have direct access to my production hard drive "D".

I need certain established software for my translation work that only run under windows. All these essentials should go into a virtualizing system (box/ware) but the virtual system must have direct access to drive "D".

Can anybody help me to use as little windows as possible?:)

Wulf

---

### Post by jocampo on 2010-01-10
Create a folder on D and share it via samba or netbios. You should be able to see it from your VBox/XP machine; of course, the drive should be mounted and active when running your virtual machine.

---

### Post by fouadatmeh on 2010-01-10
Hello,
The above should work, but there are ways to do it ( so you can choose the one that suits you best) ...
1- use the shared folders feature (where you select folders from the host and share them to the guest)..
2- add the physical partition as a separate harddisk in the guest machine.. (I remember vmware having an easy way to do that, and virutalbox lets you do it through the command line using VboxManage)

I prefer you use jocampo's method or method number 1 as they are safer, but method 2 provides the guest with raw access to the partition (which can ruin the partition if something wrong happens!)...

---

