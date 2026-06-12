---
title: "Hello need help"
date: 2008-12-05
forum: Server Platforms
---

### Post by Gregz on 2008-12-05
I downloaded Ubunto 8.10 and trying to put it on a old computer.
I looked at min req. have those, but everytime it gets to Partitions formatting it gets to 33% and freezes. 




(Creating ext3 file system for / in partition #1 of scsi1 (0,1,0) (sda)........


The above is what it says sometimes lights on keyboard sart flashing and nothing.


Thanks  

Greg

---

### Post by Gregz on 2008-12-05
OK Took the hard drive out of old computer and put it in my new computer. It went past the 33% formatted. Now says things are corrupt, won't load a kernel.

---

### Post by CrucifiedEgo on 2008-12-05
Have you run the on-disk check?  make sure there's no problems with the disk.

---

### Post by hyper_ch on 2008-12-05
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Gregz on 2008-12-05
ok first off sorry Hyper_ch. Back to business at hand. I took the hard drive out of old computer and loaded it in mine. 


That seemed to work fine all loaded and running.

1) first problem was michigan U has a corrupt feed. The downloaded iso was corrupt.

2)I think my old computer is too old it's a 1999 compaq, pentium 3, 276mb of ram 80g hard drive. i think the bios is too old.

3) is there a way I could just put the loaded hard drive back in the compaq or no ?? I tried once and got a grub failure #18.

I really want to use the old computer for this and not my good one. what are the chances and will it work???

---

### Post by falcon61102 on 2008-12-05
Seems your BIOS may need some updating before you can use the HD in it.  GRUB Error 18 pertains to the HD:
```
18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of
the BIOS translated area. This generally happens if your disk is larger than the BIOS can 
handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
```

That's a section from the GRUB Manual and basically it means that your old BIOS can't recognize the large size of your HD.  What you may want to do is check online for a BIOS update for that BIOS.  That should get you past that error.

---

### Post by Gregz on 2008-12-06
Thanks,  I think that is the problem,hunting now for bios updates. On a good note its up and running fact using it now. I love it. 


Have found one problem though. It still has the same problem as with Open Suse when it comes to nvidia drivers. They still don't like to install without a fight #-o. I've tried three times already and on reboot they won't load.....

---

