---
title: "Problem with autofs on guest Ubuntu 13.04 system"
date: 2013-09-12
forum: Virtualisation
---

### Post by xeddog on 2013-09-12
I have a small home network that consists of three linux machines.  One machine is running Ubuntu_GNOME 13.04 (hostname G-man), another is running Xubuntu 12.04 (hostname Intrepid), and the third is Ubuntu 12.04 (hostname Stealth).  The machine Stealth is a virtualbox host for 4 different guest vms but I am only having issues with one.  That one is a Ubuntu 13.04 (hostname Weirdo).  I am trying to establish nfs mounts between all four of these machines using autofs, and almost all of it is working.  The nfs between the real machines (G-man, Intrepid, and Stealth) has been in place for quite a while now, and I am trying to get the vm Weirdo added to the mix.

The problem is this.  The nfs mounts are working from the real machines including the vm Weirdo.  So, for example, from G-man I have nfs mounted Intrepid, Stealth, _and Weirdo_.  I can see all files, and open/close them without issue.

But Weirdo just will not cooperate.  I cannot get any of the nfs mounts to work at all.  As a matter of fact, even opening a terminal, cd to /media (this is the directory I use for the mount points), and issue a simple "ls" command, the terminal is hung.   Nautilus does almost same thing if I navigate to /media.  It will let me see the sub-directories (all are mount points) only ONCE, but I cannot navigate into any of them.  If I navigate away from /media and then comeback to it, I will not see any of the sub-directories.  At least I can then navigate to any other folder and nautilus will work, but the /media folder seems to be off limits.

I have changed the VB network config on Weirdo from NAT mode to Bridge.  All networking seems to be working as I can use Firefox for Internet, all machines can ping each other by name or address, and there are no other network related issues that I have found.  All of the directory structure seems to be correct and have all of the correct permissions, etc. (I had to find this out by booting into recovery mode and selecting root terminal).  I have checked and double checked and triple checked the config files, but no joy yet.  Those config files are all in /etc - auto.direct, auto.master, exports, and hosts.  I am about 99% certain that they are all correct so I don't want to post them just yet.  

So initially I am asking is if anyone knows about anything different that has to be done to get this working on a vm that would be different from a real machine.   I don't think there should be with networking set as Bridge in the vm, but  . . . ????  If not, then I can post the config files from two of the machines and go from there.


Thanks,

X

P.S.  I'm not sure if this is significant, but there is also one more machine on the network (actually there are several, but this is the only one that I think is significant.).  It is my wife's Windows 7 machine.  From Weirdo, I can use the browse network option, find her computer, and access her system via smb.

---

### Post by xeddog on 2013-09-13
Well crap!  I gave up last night and shutdown all of my computers as I usually do.  I came in this morning and booted all of my machines, which was done multiple times yesterday, and everything is working perfectly.  I just think computers hate me.

X

---

