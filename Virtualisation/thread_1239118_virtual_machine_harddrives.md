---
title: "virtual machine harddrives"
date: 2009-08-13
forum: Virtualisation
---

### Post by Dachurro on 2009-08-13
[CENTER][SIZE=4]**[COLOR=Red]_to go to question skip bold part_[/COLOR]**
[/SIZE][/CENTER]
**ok recently(by recently i mean about 2 month ago) my computers cd drive stopped working(and i mean completly, as in it wont even boot up a disk when turned on. and i already checked my bios) and around that time my windows instlation completly crashed( accidentaly formated ](*,)) so i was left with an empty computer but after hours of turning it on and off by some chance my drive worked :P and i just happened to have a ubuntu 8.10 install disk. so i installed ubutntu at first i didnt like it the resolution was off and the wifi didnt workhad to do alot of googling to get it right then slowly i started to like it more and more now im attached to my ubuntu but i still need windows for some tasks that ubuntu cant do( meaning programs that dont run on ubuntu)**

what i want to do is install windows to a virtual machine and then copy the content to a partition on my hard drive so i have windows or is there any other way of installing windows xp with out the disk i have an iso backed up in my external harddrive 
BTW i love the pencil animator yes i know random :P

---

### Post by jocampo on 2009-08-13
Hi

You can not copy/paste partitions like you do with Windows folders. You need to use a software for that. And copy a VM partition and move that to a physical drive is not so simple either.

If you want to use Windows and Ubuntu at the same time, you have two choices.

1. Dual Boot
the good: faster than a VM
the bad:you need to boot into Windows anytime you want to use it

2.VirtualBox or virtual machine
the good: you can run both at same time
the bad: performance won't be the same, in especial if you do not have enought RAM or your disk is slow.

And yes, in order to install or setup XP you need your CD. But If you use a virtual machine, you can "clone" your vdi file and there is no need to run the setup again.

---

### Post by Dachurro on 2009-08-14
ok sorry to be a bother but what do you mean by *"clone" your vdi file *i have installed windows to a virtual machine but what would cloning do and how so

---

### Post by jocampo on 2009-08-14
well, I thought you wanted to re-install your XP virtual machine. Cloning that is one of the ways via VirtualBox.

---

