---
title: "Questions from a noob.."
date: 2008-07-29
forum: Virtualisation
---

### Post by Konan128 on 2008-07-29
So i want to run windows xp with Vmware workstation.. Which kind of partitions and file systems should i use and can someone help me out on how to do it.. i just formatted to ubuntu ext3 and i don't know if this is what i need to run windows.. I have linux installed on the master 20 gb hard drive and im looking to run windows on my 160 gig slave.. any help? Sorry im such a noob just got linux today and have been tweaking with it all day.. Thanks :D

---

### Post by Ebritno on 2008-07-29
I havnt yet made a windows virtual machine on a linux os, but i have made a linux and an winxp on a winxp os, using workstation, so if they are somewhat similar (which they may or may not be) id think all you would have to do was.... 
1.file>new>virtualmachine
2.Click Custom configuration
3.Workstation 6.5
4.location of your disc or iso
5.Closest related os (windows Xp)
6.Input the virtual machine name and its save location
7.Number of processors (one)
8.allocated ram (recommended atleast 256mb from my experience)
9.Select NAT
10.Recommended selection
11.create new disk
12.Recommended selection
13. 2gb-8gb disk space allocation/split in 2gb pieces
14. Finish

EDIT:Found this link on the fourm...may prove a better help than me
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

Hope it helps

---

### Post by KatBuntu on 2008-07-29
Well, there are some differences between the installation of a virtual machine and the installation of a -let's say-"physical machine". The virtual machine run side by the physical machine, since it uses the physical resources and it needs a host SO to manage them, in this case you have not to create a physical partition for your virtual machine. 
The VMware program allows to choose the format to use for a new virtual hard drive.

---

