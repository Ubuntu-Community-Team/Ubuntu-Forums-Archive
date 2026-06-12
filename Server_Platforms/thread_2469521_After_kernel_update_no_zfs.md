---
title: "After kernel update no zfs"
date: 2021-12-01
forum: Server Platforms
---

### Post by mattiash on 2021-12-01
I had an updates for my Ubuntu server 20.04.3 which is my storage server, with an zfs array. It said that it also was a new kernel (5.15.5-76051505-generic). After the required reboot, the zfs disks are not not mounted. When I try to activate the dkms it says that zfs is not loaded. 

```

# systemctl status zfs-import-cache
&#9679; zfs-import-cache.service - Import ZFS pools by cache file
Loaded: loaded (/lib/systemd/system/zfs-import-cache.service; enabled; vendor preset: enabled)
Active: failed (Result: exit-code) since Wed 2021-12-01 22:21:43 CET; 3min 40s ago
Docs: man:zpool(8)
Process: 1343 ExecStart=/sbin/zpool import -c /etc/zfs/zpool.cache -aN (code=exited, status=1/FAILURE)
Main PID: 1343 (code=exited, status=1/FAILURE)

```
```

# systemctl status zfs-import-scan
&#9679; zfs-import-scan.service - Import ZFS pools by device scanning
Loaded: loaded (/lib/systemd/system/zfs-import-scan.service; disabled; vendor preset: disabled)
Active: inactive (dead)
Docs: man:zpool(8)

```
```

# /sbin/modprobe zfs
modprobe: FATAL: Module zfs not found in directory /lib/modules/5.15.5-76051505-generic

```

If I check /lib/modules/5.15.5-76051505-generic/kernel/
There is no zfs modules found.
It seems like kernel 5.15 doesn't come with zfs modules installed?!?!
How do I solve this? :(

---

### Post by LHammonds on 2021-12-02
Reboot and tell it to load the prior kernel.  It will likely be corrected in the next kernel update.

LHammonds

---

### Post by mattiash on 2021-12-02
> **LHammonds said:**
> Reboot and tell it to load the prior kernel.  It will likely be corrected in the next kernel update.

LHammonds

I wish it was that easy. For some reason the datasets was not mounted, I had to manually mount them. I havn't dared to reboot the server just yet. I am copying all the data to another system that luckily had space enough to host this panic moving. Only 6 TB of data...

Also sure this a home system but still this is not ok. Would this happen in a production environment I would have ditched Ubuntu the next day.

---

### Post by darkod on 2021-12-02
Out of curiocity, are these the standard kernels we are talking about? Because the number you stated is unlike the kernels I have usually seen. Usually they don't have that long number in the middle of the name. I have to admit though that due to various reasons I still haven't installed 20.04 on my home server, so I don't know if that is how kernels are "marked" now.

My point being if you added kernels manually, the more advanced ones still not in the official repos, then maybe other manual steps are needed after the new kernel is added.

---

### Post by kevdog on 2021-12-02
Did you try to regenerate the initramfs?

---

### Post by Doug S on 2021-12-02
> **darkod said:**
> Out of curiocity, are these the standard kernels we are talking about? Because the number you stated is unlike the kernels I have usually seen.Good catch. It looks as though it might be a System76 kernel, but not sure. I am not aware of any falvour of Ubuntu using a 5.15 series kernel by default yet, even 22.04 development.

---

### Post by kevdog on 2021-12-02
Do ubuntu kernels utilize dkms or is the zfs module built into the kernel?

---

### Post by mattiash on 2021-12-03
Well all I can say about the kernel was that I logged in to check something else and I saw that the OS wanted to me restart it. So the kernel was automatically installed.
I did not reinstall zfs or rebuilt the initramfs, panic took hold and I booted using 5.13, manually mounted the datasets. I am in the process of moving 6 TB of off the zfs array.
After that I will try to experiment a bit more. I say that one of the datasets had a folder inside the pool folder.
I had a plan of switching to Debian to be able to run ZoL 2.x instead, but I think I'll wait and get this back to the rock solid system it has been since April 2020 (before that 18.04 and before that 16.04). With 14.04 I tried to use BTRFS that bit me hard, scared me for ever using BTRFS on a server again. Oh well.

---

### Post by darkod on 2021-12-03
We all get the part where the system asked you to reboot. No doubt about it.

My point was that depending how kernels were installed (and as Doug said the 5.15 is not standard kernel for 20.04) then some manual actions might be needed for zfs or other stuff once new kernel is installed.

Things are rather automatic when using the "standard" kernels. But once you go away from that, maybe because you need a newer kernel or what ever, then what happens during kernel update is not so clear any more.

---

### Post by LHammonds on 2021-12-04
I don't use ZFS so I am not familiar with it.  But I do know that ZFS is not installed by default on Ubuntu Server 20.04 LTS.  That has to be added with "apt install zfsutils-linux"

The kernel versions I've had on a long-running 20.04 LTS server are as follows:

```

5.4.0-26-generic  5.4.0-48-generic  5.4.0-64-generic  5.4.0-80-generic
5.4.0-29-generic  5.4.0-51-generic  5.4.0-65-generic  5.4.0-81-generic
5.4.0-31-generic  5.4.0-52-generic  5.4.0-66-generic  5.4.0-84-generic
5.4.0-33-generic  5.4.0-53-generic  5.4.0-67-generic  5.4.0-86-generic
5.4.0-37-generic  5.4.0-54-generic  5.4.0-70-generic  5.4.0-88-generic
5.4.0-39-generic  5.4.0-56-generic  5.4.0-71-generic  5.4.0-89-generic
5.4.0-40-generic  5.4.0-58-generic  5.4.0-72-generic  5.4.0-90-generic
5.4.0-42-generic  5.4.0-59-generic  5.4.0-73-generic  5.4.0-91-generic
5.4.0-45-generic  5.4.0-60-generic  5.4.0-74-generic
5.4.0-47-generic  5.4.0-62-generic  5.4.0-77-generic

```

None of them are the 5.15 flavor.  5.15 is bleeding edge and thus, not recommended for a production server.

LHammonds

---

### Post by mattiash on 2021-12-04
Sure it is? I mean zfs installed on 20.04? I do not remember installing it rather I started using the tools installed.
@darkod This was a first for me getting a kernel automatically installed. I logged in to the server and it said it needed a restart.

Oh well, I am moving all the data off the zfs array (takes forever....) I will redo the server. If I have the patience to wait for 22.04 (said to come with ZoL 2.x)  is still in the clouds...

---

### Post by LHammonds on 2021-12-04
> **mattiash said:**
> Sure it is? I mean zfs installed on 20.04? I do not remember installing it rather I started using the tools installed.
I am about 90% sure.  I have installed a lot of 20.04 servers but only with the legacy installer (Debian-based) and not the live installer version (not Debian-based).

I looked over my old thread called [Differences between live and legacy]("https://ubuntuforums.org/showthread.php?t=2443047") and did not see the zfs package installed on either variation.

I usually only install Ubuntu in virtualized platforms (like vmware, nutanix, virtualbox and proxmox) so I'm not sure if the installer behaves differently on a bare metal install with detected RAID arrays and whatnot...in regards to the packages it will install that are different from default.

EDIT:

Related articles:
[ZFS on UbuntuWiki]("https://wiki.ubuntu.com/ZFS")
[ZFS built into Ubuntu 16.04 by default]("https://arstechnica.com/gadgets/2016/02/zfs-filesystem-will-be-built-into-ubuntu-16-04-lts-by-default/")

Everything I am reading says that Ubuntu supports ZFS by default but to manage it, you have to install the utilities.

LHammonds

---

### Post by darkod on 2021-12-04
The point few of us are trying to make here, is that there is virtually no chance that 20.04 installed 5.15 for you, if you were using only regular mainline kernels. It is not there yet and it hasn't reached 5.15.

Maybe at some point you started adding new kernels yourself to check some advanced features that didn't exist in the current kernel yet, etc. Or used some packages like earlier ukuu that was making it possible to add newer kernels still not in the general repos for the ubuntu version you are using.

If you had/have something like that, then one thing can lead to another and a kernel update might not cover all zfs modules or what ever that are needed, in the same way that the 5.4 kernel would do.

Take into account that Ubuntu/Canonical didn't test or release 5.15 for 20.04, not as mainline kernel. And also like it was mentioned here, the downside of latest kernels like 5.15 will be that it is still possible to have bugs or not being polished enough so that you can depend that the upgrade will take care for everything for you, like a 5.4 would do...

This is the point I was trying to make. But of course we have no knowledge of your server and how it actually ended up with 5.15 at all. It should be on 5.4 or somewhere there. :)

PS. I stand corrected by Doug. It should be on 5.11 when using the HWE stack. As I said I am still pending to install 20.04 on my server so I had no clear idea how far the HWE stack will take you.

---

### Post by Doug S on 2021-12-04
I agree with everything LHammonds and darkod have said.

> **darkod said:**
> But of course we have no knowledge of your server and how it actually ended up with 5.15 at all. It should be on 5.4 or somewhere there. :)If one is using the HWE stack on 20.04, then the kernel version is around 5.11.0-41.

I wonder if you have some kernel PPA added to your sources stuff?

EDIT 1: I am aware of one other poster running the same kernel, [Reference - post #9]("https://bugs.launchpad.net/ubuntu/+source/thermald/+bug/1945221"). I wonder if this is [some sort of system76 thing]("https://support.system76.com/articles/system76-driver/").

EDIT 2: I did more searching/reading. POP-OS seems to have gone to kernel 5.15 for LTS 20.04. Odd, as it is too soon for such a thing. Users are having issues. One of many [references]("https://www.reddit.com/r/pop_os/comments/r609ma/so_i_guess_were_not_mentioning_the_fact_that_lts/").

---

### Post by ameinild on 2021-12-04
> **LHammonds said:**
> I don't use ZFS so I am not familiar with it.  But I do know that ZFS is not installed by default on Ubuntu Server 20.04 LTS.  That has to be added with "apt install zfsutils-linux"


This is correct, but ZFS is composed of more parts. Another part of ZFS is the kernel module, which is indeed included in the default Ubuntu kernels, but may not be with mainline kernels - [see here]("https://launchpad.net/ubuntu/focal/amd64/linux-image-generic/5.4.0.91.95") (under the section "Provides").

So it makes perfect sense that a custom kernel 5.15 doesn't have the ZFS module by default, even if zfsutils is installed.

As others have said, you must have done something to have kernel 5.15 installed. Either added a PPA, or installed some custom kernel packages, that are now updated. Have you tried loading a standard kernel from the boot menu (5.4.0 or 5.11.0-hwe)?

---

### Post by mattiash on 2021-12-05
How 5.15 got installed I have no clue, I have not added any ppas, This is the heart of my setup everything is dependent that the storage-server is up. I have very careful what I install I check what is about to be installed.
Problem solved now, back on 5.13, zfs is working and all the datasets is there to use for all the services.

Thanks for all the input!

---

### Post by the7erm on 2021-12-05
> **mattiash said:**
> I had an updates for my Ubuntu server 20.04.3 which is my storage server, with an zfs array. It said that it also was a new kernel (5.15.5-76051505-generic). After the required reboot, the zfs disks are not not mounted. When I try to activate the dkms it says that zfs is not loaded. 

How do I solve this? :(

I had to press up & down arrow keys while booting to bring up the grub menu then select advanced & then loaded an old kernel.

It's so much fun to reboot and see something like this, run mod probe like it says then exit and still have issues.
[ATTACH=CONFIG]289593[/ATTACH]

I loaded up synaptic and did a search for 5.15.5 found `linux-modules-5.15.5-76051505-generic` then checked the `installed files` tab.  After copy & pasting that into an editor so I could do a quick ctrl+f to find zfs.  I discovered zfs isn't even listed.  While in for `linux-modules-5.13.0-7620-generic` it is.


Removing isn't an option because I kinda need the system76 drivers.
```
sudo apt remove linux-image-5.15.5-76051505-generic
...
The following packages will be REMOVED:
  linux-generic linux-image-5.15.5-76051505-generic linux-image-generic linux-modules-5.15.5-76051505-generic linux-system76 system76-driver
  system76-driver-nvidia

```

Which brings me to the question is your computer a system76 by chance?  Did you install their drivers?  If so I think we need to let them know this might be an issue.

It's a little frustrating that I run Ubuntu 20.04.3 LTS so this sort of thing doesn't happen.

---

### Post by the7erm on 2021-12-05
> **kevdog said:**
> Did you try to regenerate the initramfs?

`grub-update` didn't help.  Once I was able to get into a shell I ran that tried to reboot.  Still had to select an old kernel.  `5.13.0-7620-generic` to be exact.

---

### Post by MAFoElffen on 2021-12-06
I have been following this thread and reading it's progress, and I am sort of lost. Darkod and a few others have asked if this was a System76 Machine... The Op said he needed System76 modules, but really didn't answer directly if it was..

I have a to ask again: Is this Sysem76 hardware?

---

### Post by kevdog on 2021-12-07
Does Ubuntu not offer dkms with its kernels to insert the latest zfs modules into the kernel?

---

### Post by the7erm on 2021-12-10
> **MAFoElffen said:**
> I have been following this thread and reading it's progress, and I am sort of lost. Darkod and a few others have asked if this was a System76 Machine... The Op said he needed System76 modules, but really didn't answer directly if it was..

I have a to ask again: Is this Sysem76 hardware?

For me yes it is.  I think I'm going to get a frameworks laptop next time ...

---

### Post by MAFoElffen on 2021-12-11
So it is System76, which came with POP!OS... which on Linux Kernel 5.15.5-76051505-generic, it was reported on POP!OS, that it was a bad build, and was missing the ZFS modules in the build...

What does you system say if you do
```

uname -a
lsb_release -a

```
It seemed that other POP!OS users had that problem also... But also noted that in Ubuntu, on Ubuntu's 'released' kernels that they were there... Which Ubuntu has not released a Kernel build for 5.15.x yet.

---

