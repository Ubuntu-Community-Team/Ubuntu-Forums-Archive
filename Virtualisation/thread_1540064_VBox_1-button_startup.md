---
title: "VBox: 1-button startup"
date: 2010-07-27
forum: Virtualisation
---

### Post by Warthaug on 2010-07-27
I'm sure there is a way to do this, but haven't been able to figure it out.

I use vbox to run a virtualized WinXP in ubuntu 10.04.  Since I only have one guest system, I was wondering if there was a way to start the XP guest without having to first start the vbox manager?  Basically, I'm looking for a command-line startup that I could simply run using an icon.

Anyone know of an easy way to achieve that (the command line startup)?

Thanx

Bryan

---

### Post by Warthaug on 2010-07-27
Go figure - a few hours after posting this I figured out the google search terms that let me find my answer.  Its really easy; just setup a launcher, using the following command:
```
VBoxManage startvm <your virtual machine name>
```
In my case, my virtual machine is called 'WinXP', so I use:
```
VBoxManage startvm WinXP
```
Works like a charm! :D

Bryan

---

### Post by Ginsu543 on 2010-07-27
This was very helpful. Thanks!

---

### Post by TheFu on 2010-07-28
On case-sensitive file system hosts, like Linux, the different versions OSS or proprietary have different capitalization of the VBoxManage / vboxmanage commands.

I believe the OSS version is all lowercase.

---

### Post by Warthaug on 2010-07-29
> **TheFu said:**
> On case-sensitive file system hosts, like Linux, the different versions OSS or proprietary have different capitalization of the VBoxManage / vboxmanage commands.

I believe the OSS version is all lowercase.

It may be.  I'm running the proprietary version, and thus use the VBoxManage command.  I've never used the OSS, as I need USB, etc, support.

Bryan

---

### Post by JKyleOKC on 2010-07-29
I've carried that idea a step farther. Launchers for Xubuntu allow a menu of applications, so mine launches VBox itself as the top item, with a menu of five FMs using "startvm" to launch any of the five VMs I have on this system (each is for a specific major application). Works perfectly!

---

