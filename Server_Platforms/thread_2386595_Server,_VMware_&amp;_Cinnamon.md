---
title: "Server, VMware &amp; Cinnamon"
date: 2018-03-07
forum: Server Platforms
---

### Post by deepblue73 on 2018-03-07
Hi,

I installed Ubuntu 17.10 desktop, then installed Cinnamon and started to happily use my Ubuntu with the desktop environment I like. After a while it bothered me to have all that Gnome stuff installed on my system which I don't even use. I decided to perform a Server installation and then install Cinnamon on top of it. Don't ask me why, I just wanna do it.

I wanted to test this on VMware at first. I always try to keep an identical VMware version of my actual system anyway.
I installed the server, performed updates, installed cinnamon but when I try to login in my first attempt, I am getting "Failed to load session" error message. On subsequent attempts, Cinnamon load only in Software Rendering mode.

I tried a couple of different things to fix that problem, which didn't help at all. I thought the problem would be related with the VMware drivers. I tried the following.
1- Installing open-vm-tools before installing Cinnamon Desktop Envoirment.
2- Installing open-vm-tools after installing Cinnamon Desktop Envoirment.
3- Installing regular vmware-tools  before installing Cinnamon Desktop Envoirment.
4- Installing regular vmware-tools after installing Cinnamon Desktop Envoirment.
None did help.

Then I installed the ubuntu-desktop pack to see if it will make a difference and it did. Now I was able to login to Cinnamon without that "Software Rendering mode". Of course this was only to test what's gonna happen. I am not gonna use an installation like this. But obviously, I need something from that huge ubuntu-desktop package collection, to be able make my initial goal work.

Please help me to drill down the problem so I can login to Cinnamon Desktop Envoirment, not the software rendering mode and without installing that huge ubuntu-desktop package collection.

Thanks...

---

