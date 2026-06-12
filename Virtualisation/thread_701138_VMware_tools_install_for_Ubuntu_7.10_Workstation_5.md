---
title: "VMware tools install for Ubuntu 7.10 Workstation 5.5 - detected x.org execution abort"
date: 2008-02-19
forum: Virtualisation
---

### Post by optimizer on 2008-02-19
Hi all,

This is for anyone that has VMware and has installed Ubuntu 7.10 guest.
I have Workstation 5.5, Win XP host, and i'm trying to do a VMware tools install for Ubuntu 7.10 and I'm getting an error "x.org detected".

I tried the install in Gnome, but it failed.
I read that you can install if you use a workspace for the install, so I switched to a workspace ctrl-alt space/F1, and logged in there and as root and tried it, but it still detects x.org

vmware-install.pl

It runs through the install questions, where I just accept all the defaults until

then it asks to run the config script, and I allow it to, and it asks:

vmhgfs module build for my system, and I enter: n (I've entered yes on other attempts but it provides a default folder for compiling but it cant find the folder and repeats the question, so I have to abort)
then
vmxnet module build for my system, and I enter: n
then I get the error

Detected x.org
problem extracting version of x.org
execution aborted


I'm still a newbie.
I suppose the X gnome system is still running (I have just switched away from its workspace), so I wonder if that is something to do with it.
I suppose I don't know how to get out of X and back into it if I needed to.

Anyway, I wonder if anyone else has had the intall tools issue on Ubuntu 7.10 and knows how to fix it.

Thanks

---

