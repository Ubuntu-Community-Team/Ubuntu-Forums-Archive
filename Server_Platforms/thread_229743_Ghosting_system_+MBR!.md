---
title: "Ghosting system +MBR?!"
date: 2006-08-04
forum: Server Platforms
---

### Post by Chris Tucker on 2006-08-04
Ok, so ive got a server i remotely maintain (for free, i get asked why a lot but its experience and a small hobby... writing my own http-based front end to the thing.)
It's drives are a little.. ancient. I know they are eventually going to die, or somethings going to happen and the system will need to be reinstalled on the same drives... either way the hardware isnt going to change unless i donate them a new system... in which case it will be a mini ITX one with a CF card for / 

in any case, my current restore method to get the system back to its current state is a bit... crude, and slow.

I'm going to be making a set of CD's to restore the system to its current state... based on a modified DamnSmall LiveCD. Im going to write scripts that  use [this]("http://www.ubuntuforums.org/showthread.php?t=35087&highlight=ghost+drive") restore method for the contents of /

But then theres that nagging MBR.... i can capture everything else for backup purposes, but i have no idea about this bit...

how would i back up the MBR of the drive? the way of outputting the backup file back INTO the MBR of a drive would have to have a non-interactive option... so it can be run from a script easily... 
say .. the dd command?

also, any comments about the rest of the ghosting procedure?

---

### Post by Sam on 2006-08-05
For backing up the MBR:
```
$ dd if=/dev/hda of=/root/hda.boot.mbr bs=512 count=1
```

---

### Post by Chris Tucker on 2006-08-05
So, for putting the MBR back, it would be ```
dd if=/path/to/backed/up/mbr of=/dev/hda bs=512 count=1
```
?

---

### Post by lamego on 2006-08-05
MBR contains generic boot code, you shouldn't care about backing it up because it can always be installed using a Live CD .

---

### Post by Chris Tucker on 2006-08-05
> MBR contains generic boot code, you shouldn't care about backing it up because it can always be installed using a Live CD .
No... thats the point. A custom livecd will be doing the restoration, and the MBR will have to be restored AUTOMATICALLY. so installing one is more complicated than copying the old out and copying it back in.

as for my previous post, not quite, but found a wikipedia article thats helping figure it out. so far all i get is the text word GRUB when i attempt to boot the test VM.

---

### Post by lamego on 2006-08-06
The point is, you dont need to restore the MBR because you can simply install it from ANY Live CD, the MBR does not containt any data or configuration.

---

### Post by Chris Tucker on 2006-08-06
> The point is, you dont need to restore the MBR because you can simply install it from ANY Live CD, the MBR does not containt any data or configuration.
Wrong.
The MBR contains rough boot information. and it DOES get corrupted sometimes. it DOES change depending on your OS. And my system needs to replace things that MAY break WITHOUT ANY INPUT FROM THE PERSON DOING THE RESTORE. so "installing" the MBR again from a livecd is NOT an option.
> A Master Boot Record (MBR), or partition sector, is the 512-byte boot sector that is the first sector of a partitioned data storage device such as a hard disk.> 
A boot sector is a sector of a hard disc, floppy disc, or similar data storage device that contains code for bootstrapping programs (usually, but not necessarily, operating systems) stored in other parts of the disc.

---

