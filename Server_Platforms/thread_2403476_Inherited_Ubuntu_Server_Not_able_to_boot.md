---
title: "Inherited Ubuntu Server Not able to boot"
date: 2018-10-11
forum: Server Platforms
---

### Post by dinok2 on 2018-10-11
Gents,
I am having a critical issue with one of our Ubuntu Servers that is pretty old now. I want to say this is a ver. 16x Server.
Has been running for years without issue. Routine reboot gave the below errors:

run-init: /sbin/init: No such file or directory
Target filesystem doesn't have requested /sbin/init.
run-init: /sbin/init: No such file or directory
run-init: /etc/init: Permission denied
run-init: /bin/init: No such file or directory
/bin/sh: 0: Can't open ro
[	17.445318] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00007f00
[	17.445318]


I have limited information on this box as far as past in concerned. It runs as a VM on Hyper-V and rely on it heavily for redmine and Docker. 
I am at a loss as far as how to get it too boot back up. Please help. Thank you.

Some notes on the box:

If i press "e" when grub loads and this is the linux section:

linux    /vmlinuz-3.8.0-34-generic root=/dev/mapper/docker--a-root ro

---

### Post by dinok2 on 2018-10-12
Update:
[FONT=Roboto][FONT=Arial][COLOR=#000000]I have successfully loaded a 16x server live .iso to get into "Repair broken system"[/COLOR]
[COLOR=#000000]Changed the resolv.config to hit the outside world[/COLOR]
[COLOR=#000000]i have also changed the repo's to point to the correct legacy repositories[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]i can:[/COLOR]
[COLOR=#000000]Sudo apt-get update successfully[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]what i cant do and what i think will fix the issue:[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]sudo apt-get install init[/COLOR]
[COLOR=#000000]I get a "unable to locate package"[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]im assuming i need to mount /dev/sda1 /mnt[/COLOR]
[COLOR=#000000]and sudo chroot /mnt[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]but if i try to chroot into /mnt i get [/COLOR]
[COLOR=#000000]failed to run command &#8216;/bin/bash&#8217;: No such file or directory [/COLOR]
[/FONT]
[/FONT]

---

### Post by darkod on 2018-10-12
1. What do you mean with legacy repositories? Ubuntu 16.04 LTS is still in full support (until Apr 2021) so you can use the standard repos. Please be careful when changing repos especially when that step was not needed.

2. You can try to boot it in recovery mode without any CD/DVD. When booting it up it will show the grub menu shortly. Select the recovery mode option and boot it. During the process it will show you small menu where you can select to activate networking (otherwise the recovery mode will have no network active), and then after that go to "drop to root shell".

Once in the shell you can check if those directories mentioned really exist or not (/sbin/init, /etc/init, /bin/init).

---

### Post by TheFu on 2018-10-13
I used to run a redmine server.  Never touched hyper-v or docker.

What level are your skills? 
What do the system logs show?
When you say you did a chroot, please be exact. To do it correctly, there are about 6 steps.

To see which release is installed, look at /etc/lsb-release. The answer is important.

---

### Post by oldfred on 2018-10-13
> linux    /vmlinuz-3.8.0-34-generic root=/dev/mapper/docker--a-root ro 				

kernel 3.8 was standard with Raring, but may have been one of the updates to 12.04, but do not remember or have notes.
       13.04 	  	Raring Ringtail 		18 April 2013 		October 2014 	3.8 
But both 12.04 & 13.04 are EOF - end of life.
Or backup, and new install will be required.

---

