---
title: "RAID 1 with 3TB HDDs and GTP filesystem"
date: 2013-01-27
forum: Server Platforms
---

### Post by chrisp1001 on 2013-01-27
Hello,

this is my config:

Ubuntu server 12.10

2x 3 TB HDDs for data storage
2x 160GB HDDS for operating system

The mainboard supports RAID 1 this is why I want to use it's internal raid controller. I've set up the two raid arrays in the BIOS.
After that I started the ubuntu server installation. During the HDD setup the installer asked if it should recognize the Serial ATA RAID arrays - yes, of course.
However the partition manager only shows one array (the one with the two 160GBs HDDs as /dev/mapper) and the other two 3TB disks are shown seperately.

I suppose that there's a problem with the GTP filesystem...

So how can I set up the RAID 1 for the two 3TB disks?

Thanks for any help

Chris

---

### Post by darkod on 2013-01-27
Use software raid instead of the bios fakeraid. If not using proper HW raid card, SW raid is better than the fakeraid.

I would use the desktop live cd first to prepare the partitions from the live session, but it's not necessary. I just prefer it that way.

Write new gpt tables on the 3TB disks with parted, you can write msdos table on the small disks or also gpt, as you wish. If using gpt for the OS disks note that you need a small 1MiB partition with NO filesystem and the bios_grub flag set. This is needed on gpt disks so that grub2 can install properly.

Create the partitions with the sizes you want, and set the raid flag on them in parted.

During the server OS installation, go into the Configure SW raid menu and set up the md devices from the prepared partitions. They will appear in the main partitions list as separate devices.

Use these devices to set your /, and other mount points as you wish, and their filesystem.

That's it. It will work much better and flexible compared to fakeraid. For example you can later grow the array with bigger or more disks without losing the data, while with fakeraid you would have to destroy the array and the data, and create another array.

---

### Post by TheFu on 2013-01-27
+1 for everything Darko said.

I would discourage MB RAID use.  It is not very flexible and you will likely loose access to anything on those disks when/if a new MB is needed, plus the performance won't be anywhere as good as a real-RAID card provides, so you might as well use the fantastically flexible software RAID built into Linux.

BTW, I'm using SoftwareRAID on 2x2TB HDDs now and used SoftwareRAID5 for almost 6 yrs prior to that with only loose cables causing problems. I did move between physical machines AND update OSes with the RAID data intact. [http://blog.jdpfu.com/2010/02/12/software-raid-migration](http://blog.jdpfu.com/2010/02/12/software-raid-migration) it was a non-event. I like non-events when it comes to storage. ;)

---

### Post by chrisp1001 on 2013-01-27
Thanks, guys. I'll have a look at software RAID. :)

---

### Post by tgalati4 on 2013-01-27
It's also possible that your motherboard BIOS needs an upgrade to support 3TB drives and report them properly so that Linux can see them.  

But I agree, unless you have a true RAID controller (with an internal battery for preserving cache writes), you might be better served with softraid.  True RAID controllers come with server-class machines and have a separate BIOS from the motherboard--that often needs updating to work with larger drives.

---

### Post by oldfred on 2013-01-27
I do not know about RAID, but they did away with the alternative installer and RAID did not make the cut with a gui installer.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuServer)

Does not seem clear if server install has RAID or not as it has same notes as Desktop.
> 

[LIST]
[*]There are several options for installing using software RAID.  You can: 
[LIST]
[*][install using the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the 'debian-installer' directory on the mirrors; 
[*]install using the desktop CD and migrate the disks to RAID post-install; 
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade. 
[/LIST]
[/LIST]


---

### Post by darkod on 2013-01-28
I don't think raid is removed from the server ISO, and since this is the server forum I assume the OP is interested in the server version.

With the 12.10 desktop live cd you should be able to install SW raid too, only few extra steps would be needed. You would have to boot into the live session first, install the mdadm package, create the md devices in terminal before hand, and then click the Install icon on desktop.

If I've got it right, since mdadm remains added during that session, it should recognize and show the md devices in the installer where you can use them just the same as standard partitions.

Not sure if after install you will have to chroot into the installation and add mdadm and maybe update initramfs.

---

### Post by chrisp1001 on 2013-01-28
The server installer does support setting up software RAID.
The system is now running on it and working brilliant. Many thanks, guys!

---

