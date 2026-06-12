---
title: "Ubuntu and OEM"
date: 2010-04-11
forum: The Cafe
---

### Post by drvista on 2010-04-11
Hello , I am an Ubuntu User and I really like it. Ubuntu gaining OEM support makes my happy but that not enough for ubuntu to triumph and fix bug number 1 . :) ....
If ubuntu want to gain OEM support it has to offer some OEM tools and my prefered one is an idea from Windows world !
if you buy a laptop with windows and got your system dead you can simply press f8 and choose either to do a Sytem restore or repair using a system image or do start up repair
both recovery options are vital specially for new users who don't care that their system got dead because they did something wrong or had an error .
ubuntu would not use system restore ..because it's LAME but we can have our own design of fixing things such as why when i choose the recovey boot from grub i don't find the choice of Revert last synaptic install chnanges or undo last packages changes either install or remove ......
and why we don't have create a system backup under  system > Administator and create a small disk volume that will have a compressed copy of our system that can be flashed back  to our / partition when we got anything wrong ...and add this option to recovery menu we already have but it's now only helpful for geeks not noobs who just want their system works with out reinstalling !!!
imagine the situation of Me a non tech guy in a meeting and my ubuntu netbook don't boot because of a package i installed the last night .. yes that happens sometimes ... what can I do .. all the other folks use windows and don't know any thing about linux .. having a rescue option would be helpful even if you think that linux is stable and yes it's but that is because linux users are geeks and know what they do. and they don't do wrong turns and if they do they can fix but what about non tech guys out their ?????
please vote for my idea at 
[http://brainstorm.ubuntu.com/idea/24397/](http://brainstorm.ubuntu.com/idea/24397/)

---

### Post by kellemes on 2010-04-12
Ubuntu should not get killed because of some update..
As long as it does, it's just not good enough.

---

### Post by Khakilang on 2010-04-12
I think there is a software restore somewhere in Ubuntu Software Centre. Wait I minute I got to go and find and download and install it not that all user are aware of doing that. So a system restore is a good idea. Isn't the Ubuntu live CD help out also?

---

### Post by c00lwaterz on 2010-04-12
if there is system restore in ubuntu then it's a good news. :guitar:

---

### Post by drvista on 2010-04-12
Ubuntu neither window should be killed for update but sometimes it happens. and if ubuntu is going to be released to the masses on OEM computers there should be  a backaup of the OEM ubuntu disk image so when the system is corrupted the User can restore the OEM version without hassel to reinstall
and this is only for noob users that don't know how to fix the coruptrd dependency and just want their system to work again as they bought it or may be had installed out of repositories applications that made their system unstable for many reasons easy way to get the default ubuntu install with tweaks for that system and oem applications is a good idea and dont tell me a normal user should have ubuntu install cd with him wall the time and an internet connection to download the packages he needs post install and when he is in a seminar and the system is not working he should get an emergency repair for his system
and you can think of it as a safety net for new users to experiment and try out every tool out there and when it fails they only have something they go for before asking in forums

---

### Post by 3rdalbum on 2010-04-12
I agree with you, there should be a system restore distro that performs the same function as what you find on OEM Windows machines.

What most people don't realise is that you pay the Windows tax TWICE - once for the current version of Windows that is preinstalled, and another time for an earlier version of Windows that works as a system image restorer. If your machine came with XP, then your system image restorer will work from 2000 or 98. If your machine came with Windows 7, then your system image restorer might even use Vista.

---

### Post by drvista on 2010-04-12
the problem is that it's just a 10kbyte script will do that with out the need for a prev version of any other os but i really not that geek to do it automatically though manually i can 
sudo tar -czvpf rootfs.tgz /
and to restore 
sudo tar -xzvpf rootfs.tgz /
but it need to be done as a shell script with a progress bar and some tweaks for real life situations
then add this script to /usr/share/recovery-mode/options/

---

