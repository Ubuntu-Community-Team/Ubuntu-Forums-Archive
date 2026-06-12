---
title: "Re: Help me setup Debian and Tiny Core dual boot"
date: 2017-01-11
forum: Ubuntu/Debian BASED
---

### Post by linuxyogi on 2017-01-11
```
# parted -l
Model: ATA Samsung SSD 750 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  25.0GB  25.0GB  primary  ext4         boot
 2      25.0GB  110GB   84.5GB  primary  ext4
 3      110GB   120GB   10.5GB  primary  ext4


```

Partition sda3 (10.5GB) is my Tiny Core partition. I tried installing Tiny Core's grub but got "Operating system not found". Then I restored Debian's grub by running the Debian live cd.

When I run update-grub2 under Debian it doesn't detect my Tiny Core installation.

How do I manually add Tiny Core's entry to Debian's grub ?

Never done this before so please be patient.

Using Debian Jessie and TinyCore-current.

Boot info  [http://paste.ubuntu.com/23782040/](http://paste.ubuntu.com/23782040/)

---

### Post by oldfred on 2017-01-11
Do not know Debian nor tinycore.

But it looks like TinyCore uses Syslinux boot loader which is a Windows type boot loader that has boot code in the PBR or partition boot sector.
You then may be able to just chain to it like Windows. Add a boot stanza to 40_custom.

       sudo nano /etc/grub.d/40_custom

> menuentry "TinyCore on sda3" {

 set root=(hd0,3)
insmod chain
chainloader +1  

 }

sudo update-grub

---

### Post by linuxyogi on 2017-01-11
Menu entry for Tiny Core appeared and I was able to boot to it but X won't start. startx says command not found.

[Here]("http://forum.tinycorelinux.net/index.php?topic=13294.0") is a solution but its complicated. Can you please have a look and tell me what to do ?

---

### Post by oldfred on 2017-01-11
That user seemed to have part of system on another partition, so required a boot parameter to find the second partition.

Do you get syslinux boot menu?
Do not know syslinux well enough to know what boot parameters may be required. 
 [http://syslinux.zytor.com/wiki/index.php/SYSLINUX](http://syslinux.zytor.com/wiki/index.php/SYSLINUX) 

What video do you have? 
In grub boot parameters often needed for nVidia or AMD.

---

### Post by linuxyogi on 2017-01-11
I am using GeForce GTX 650. Just tried Slitaz it wont even start X. These tiny distros are quite difficult to install. I am giving up. Thanks for your reply.

---

