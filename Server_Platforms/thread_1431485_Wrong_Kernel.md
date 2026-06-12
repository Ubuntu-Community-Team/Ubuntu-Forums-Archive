---
title: "Wrong Kernel?"
date: 2010-03-16
forum: Server Platforms
---

### Post by L0neRanger on 2010-03-16
I've recently upgraded from Ubuntu 9.04 Server edition to Karmic Koala 9.10 server.

Earlier when I ran uname -r it showed: ***KernelVersion*-server**

Now the current version I've upgraded to shows **2.6.31-20-generic-pae**

Should the Ubuntu server edition be using a generic-pae kernel?

---

### Post by jfparis on 2010-03-16
That might be ok. It all depends on what kind of hardware you are running you server on.

You might tell us a little bit more about it.

---

### Post by Dayofswords on 2010-03-16
maybe its just me..
[SIZE="1"]and hey, what do i know[/SIZE]
but a fresh install of server things sounds better than upgrading..

---

### Post by L0neRanger on 2010-03-17
> **Dayofswords said:**
> maybe its just me..
[SIZE="1"]and hey, what do i know[/SIZE]
but a fresh install of server things sounds better than upgrading..
I wasn't able to do a fresh install because of this:

[http://ubuntuforums.org/showthread.php?t=1430630](http://ubuntuforums.org/showthread.php?t=1430630)

If you have any suggestions/comments for me, it'd be greatly appreciated.

---

### Post by L0neRanger on 2010-03-17
> **jfparis said:**
> That might be ok. It all depends on what kind of hardware you are running you server on.

You might tell us a little bit more about it.
We'll that's what I'm really skeptical about. How Ubuntu Server edition can use a server kernel till 9.04 and suddenly decide that I need a generic-pae when I upgrade to 9.10?

BTW This is the hardware I'm running my server on:[B]
AMD Athlon XP 2000+ 32bit
512MB DDR
ECS K7VTA3 V.6 Motherboard
Four 36GB SCSI 10K drives on Adaptec 2940 PCI-Fast SCSI Host Adapter[/B]
*yada yada yada*

Can provide more information if you think it's necessary, but I think the processor info should be enough.

Do you see any reason why it would be using a generic-pae kernel instead of a server one?

---

### Post by L0neRanger on 2010-03-17
> **jfparis said:**
> That might be ok. It all depends on what kind of hardware you are running you server on.

You might tell us a little bit more about it.
And One more thing I'm not comfortable about - what's point of having a server install if it goes ahead and uses a generic kernel?

Isn't there a scheduler difference as in the Server kernel uses deadline whereas the generic kernel uses CFQ?

Also concerned about other performance issues.

---

### Post by L0neRanger on 2010-03-17
Looks like I'm not the first person with this issue.

[http://ubuntuforums.org/showthread.php?t=1316336](http://ubuntuforums.org/showthread.php?t=1316336)

Bug? Feature request?

---

### Post by KiLaHuRtZ on 2010-03-17
Just install it manually...

```
sudo apt-get install linux-image-server
```

---

### Post by L0neRanger on 2010-03-17
> **KiLaHuRtZ said:**
> Just install it manually...

```
sudo apt-get install linux-image-server
```
Tried to do that but I get a message saying that the it is installed and it is the newest version.

Now trying to change the default boot options so that the box boots into the server kernel every time it boots.

Will let everyone know what happens.

---

### Post by L0neRanger on 2010-03-17
When I do,

```

root@ubuntu-server:/boot/grub# dpkg --list | grep linux-image
rc  linux-image-2.6.24-26-server               2.6.24-26.64                      Linux kernel image for version 2.6.24  on x86
ii  linux-image-2.6.28-18-server               2.6.28-18.60                      Linux kernel image for version 2.6.28  on x86
ii  linux-image-2.6.31-20-generic              2.6.31-20.58                      Linux kernel image for version 2.6.31  on x86
ii  linux-image-2.6.31-20-generic-pae          2.6.31-20.58                      Linux kernel image for version 2.6.31  on x86
ii  linux-image-generic                        2.6.31.20.33                      Generic Linux kernel image
ii  linux-image-generic-pae                    2.6.31.20.33                      Generic Linux kernel image
ii  linux-image-server                         2.6.31.20.33                      Linux kernel image on Server  Equipment.

```It shows that generic, generic-pae and server versions of 2.6.31-20 (the latest) are installed.

But the grub.cfg just shows the generic-pae and generic parts of this kernel.
```

root@ubuntu-server:~# grep "menuentry" /boot/grub/grub.cfg
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.28-18-server" {
menuentry "Ubuntu, Linux 2.6.28-18-server (recovery mode)" {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {

```

What am I doing wrong here?

---

### Post by KiLaHuRtZ on 2010-03-17
Try re-installing?

```
sudo apt-get purge linux-image-server && sudo apt-get install linux-image-server
```

---

### Post by Queue29 on 2010-03-17
> **KiLaHuRtZ said:**
> Try re-installing?

```
sudo apt-get purge linux-image-server && sudo apt-get install linux-image-server
```

I was having the same problem, and this worked for me. Thanks

---

### Post by L0neRanger on 2010-03-17
> **KiLaHuRtZ said:**
> Try re-installing?

```
sudo apt-get purge linux-image-server && sudo apt-get install linux-image-server
```

Doesn't work for me. Here's the output:

```
root@ubuntu-server:/home/silver# apt-get purge linux-image-server && apt-get install linux-image-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-server*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 32.8kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 28821 files and directories currently installed.)
Removing linux-image-server ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  linux-image-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,406B of archives.
After this operation, 32.8kB of additional disk space will be used.
Selecting previously deselected package linux-image-server.
(Reading database ... 28818 files and directories currently installed.)
Unpacking linux-image-server (from .../linux-image-server_2.6.31.20.33_i386.deb) ...
Setting up linux-image-server (2.6.31.20.33) ...
root@ubuntu-server:/home/silver#

```It say's after the operation 32.8kB disk space will be freed. And when it tries to install fresh it says 32.8kB of disk space will be used.

Is the linux-image-server just 32kB?

I find this hard to believe. :confused:

---

### Post by L0neRanger on 2010-03-17
> **Queue29 said:**
> I was having the same problem, and this worked for me. Thanks
Can you please provide me with an output after you ran that in the terminal?

---

### Post by FuturePilot on 2010-03-17
I think they dropped the -server kernel for the 32bit version. Now it uses the -generic-pae kernel. There's nothing wrong; this is normal. The linux-image-server package is just a metapackage that now depends on -generic-pae.

---

### Post by L0neRanger on 2010-03-17
> **FuturePilot said:**
> I think they dropped the -server kernel for the 32bit version. Now it uses the -generic-pae kernel. There's nothing wrong; this is normal. The linux-image-server package is just a metapackage that now depends on -generic-pae.
That's sad but I guess that solves the issue. I didn't know this nor did I find any documentation, yet.

I still don't understand how one person, Queue29, seems to have solved this problem. Must be some other version instead of Ubuntu Server 9.10 or some other architecture.
[ ]("http://ubuntuforums.org/member.php?u=342869")

---

### Post by L0neRanger on 2010-03-20
Just updating everyone,

I've downloaded the latest copy Ubuntu Server 9.10 and it installed perfectly.
No problems so far.

---

### Post by Queue29 on 2010-03-20
> **L0neRanger said:**
> That's sad but I guess that solves the issue. I didn't know this nor did I find any documentation, yet.

I still don't understand how one person, Queue29, seems to have solved this problem. Must be some other version instead of Ubuntu Server 9.10 or some other architecture.
[ ]("http://ubuntuforums.org/member.php?u=342869")

Yea, I'm using 8.04 LTS. It started out with a server kernel, and then one of the major updates gave it a generic kernel, and couldn't fix it until I found the instructions posted above (+ reboot). 

```

mry@AtomBozo:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"
mry@AtomBozo:~$ uname -a
Linux AtomBozo 2.6.24-27-server #1 SMP Fri Mar 12 01:45:06 UTC 2010 i686 GNU/Linux


```

---

