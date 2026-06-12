---
title: "easy hard drive access"
date: 2007-11-28
forum: The Cafe
---

### Post by retlaw on 2007-11-28
I am a Mac user from way back (sys7.0). I am accustomed to 2 or 3 scsi hard drives in a chain and the ability to seamlessly mount, read, and write to any drive on the chain. I have tried periodically to use Ubuntu and fail miserably each time. The Sudo and permissions issues make the Ubuntu system unusable for me. Can someone tell me sraight out if I am wasting my time here. I would prefer to stay open source rather than  proprietary. But I want free use of my machine and all its drives. Do I simple 'buy a Mac?' Does the new Darwin based mac os still permit free access to my drives?

Sorry if this is not an appropriate posting. Any thoughst are appreciated.

Thanks,
Dennis:)

---

### Post by omegamike3 on 2007-11-28
are you wanting to use this old machine with the scsi drives or are you more just asking as a general question? meaning, are you planning on buying a new system anyways or already have one?

---

### Post by koenn on 2007-11-28
I don't remember how it was on pre-OSX Mac, but in Linux, you hardly ever see the actual disks.
The filesystem starts from / and usually spans all disks, whether its a single IDE or multiple scsi drives. 
what you do is 'mount' disks (or more correctly :partitions) to subdirectories, 
eg you could have disk1 mounted to /, disk2 mounted to /var, and disk 3 mounted to /home, and you'd access any file on disk 3 with a simple "cd /home" or by browsing to home in a file manager. 
That's the usual approach, but you can also mount any drive to any partition, eg you can mount a cd rom, a usb memory stick, an extra hard drive (internal or external, scsi, sata usb or ide, ...) to your /media directory, or to /mnt, or to /home/yourname/my_extra_disk ... pretty much anywhere you like.

---

### Post by ssam on 2007-11-28
how recently have you tried ubuntu?

you should have a go with the gutsy live cd. open up a nautilus window (gnome equivilant to finder). it should list all the partitions it find on the side bar.

with an installed system you can either have the drives mounted via fstab rules, or any that are not listed in fstab will be shown in nautilus as above. the fstab lets you choose exactly where in the file system the disks are mounted and gives you lots of options, but if you are opposed to editing config text files it may not be for you.

to avoid get the partitions listed in the fstab, make sure to set them to 'don't use' in the ubuntu installer (at the manual partitioning bit).

ubuntu's default security model is pretty close to MacOS X.

---

