---
title: "blinking cursor on console... can't login there, but ssh works and system is running"
date: 2011-05-23
forum: Server Platforms
---

### Post by Underpants on 2011-05-23
I built a 11.04 server system in vmware workstation a few days ago, set it up for something and now I have a strange problem. :(

It boots without problem. I can login via ssh, the services run and everything is OK from the outside. But on the console there's just a fast blinking cursor on the screen, no login or anything to that affect. Just blank and a blinking cursor. 

What can I check? or provide for more help?

---

### Post by tapi0n on 2011-05-23
I actually experienced the same thing a couple of weeks ago. But didn't want to look for a solution and since I had a 9.04 near me I just used that. 

Maybe check [http://ubuntuforums.org/showthread.php?p=10761345](http://ubuntuforums.org/showthread.php?p=10761345) since there seem to be some trouble with 11.04 an vmware

---

### Post by david.garceau on 2011-05-23
Sounds weird but make sure the hdd isnt full.

---

### Post by Underpants on 2011-05-23
vmware workstation is installed on a windows machine. Ubuntu 11.04 server is the guest. Disks are nowhere near full.

---

### Post by Underpants on 2011-05-23
Looks like the boxed kernel boots OK. Upgrading to whatever the latest is, borks it.

---

### Post by Underpants on 2011-05-23
This is the installed kernel right now. Upgraded vmware tools, still broken.


2.6.38-8-generic

---

### Post by david.garceau on 2011-05-24
> **Underpants said:**
> vmware workstation is installed on a windows machine. Ubuntu 11.04 server is the guest. Disks are nowhere near full.

Are you sure that the virtual disk is not full though? Only reason why i keep insisting is because i had the same problem a couple weeks ago.

---

### Post by Underpants on 2011-05-24
> **david.garceau said:**
> Are you sure that the virtual disk is not full though? Only reason why i keep insisting is because i had the same problem a couple weeks ago.

Yes. I am positive. 

There is an official bug report:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830)

---

