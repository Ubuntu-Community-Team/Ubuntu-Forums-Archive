---
title: "[SOLVED] filesharing between host and vm"
date: 2008-03-12
forum: Virtualisation
---

### Post by gawdin on 2008-03-12
how do i set up gutsy and xp to share files with each other when gutsy is the host OS and xp is the guest OS using virtualbox? all the related topics I found were never answered so hopefully this one is

---

### Post by gawdin on 2008-03-12
ok I solved it real easy

first bridge the connection and setup vbox0

this can be found under the help>contents then 
-innotek Virtualbox user manual
--virtual networking
---host interface networking and bridging on linux hosts
----(your distro, mine was ubuntu)

once you bridge the connection set it as adapter 1 under the settings>network tab assuming adapter 0 is being used to get out to the internet like mine was

when running the VM click devices>shared folders then add /home/usrname as the folder path and usrname as the folder name
make sure permanent is checked

for a VM of XP right click my computer and click map network drive give it a drive letter and type \\VBOXSVR\usrname where usrname is your username on linux

---

### Post by Achetar on 2008-03-12
Actually, you can also have it access just specific files using the 'Shared Folders' Settings. I have it set to access my internet using the network connection, and my home folder using the shared folders

---

