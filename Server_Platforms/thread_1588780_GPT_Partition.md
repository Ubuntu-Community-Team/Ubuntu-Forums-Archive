---
title: "GPT Partition"
date: 2010-10-05
forum: Server Platforms
---

### Post by djanie78 on 2010-10-05
Fellas am in the process of removing a GPT partions so i can go ahead with my server installation. 2.7TB drive. Its been almost two day. I can see activity on the hard drive.  I started it on a work bench right next to my desk thinking it was gonna take a few hours. Being a server, the noise is driving me insane. 

Any one done this before? How long does it take?

---

### Post by CharlesA on 2010-10-05
How are you removing the partition? gparted?

Is this on a RAID array or something?

---

### Post by srs5694 on 2010-10-05
First, if you've got a "2.7TB drive," you may need GPT. MBR tops out at 2TiB on disks with 512-byte sectors. You can fudge this by starting a sub-2TiB partition before the 2TiB mark, but this is a hack that only works, to the best of my knowledge, on OSes that have good GPT support anyhow. I therefore don't recommend doing it. If the disk uses sectors that are larger than 512 bytes, the MBR limit also goes up. Nonetheless, lacking any further information, I'd recommend using GPT on any disk over 2TiB in size.

Second, removing the GPT data structures takes a fraction of a second -- they total 17.5KiB in size, assuming the default number of partitions. Thus, either something is very wrong with your disk or you've opted to do something other than simply wiping the GPT data structures. Perhaps you're wiping the whole drive? ("dd if=/dev/zero of=/dev/sdb" or something similar.) Two days seems a bit extreme for this, although if you're using a utility that does a "secure erase" operation, it might come to that value. ("Secure erase" is usually done by erasing a sector multiple times, thus multiplying the time it takes to do its work.) Also, if the disk is connected via USB, that will be much slower than a faster PATA or SATA connection.

If all that's needed is wiping GPT data structures, my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) package will do the job. Go to the experts' menu and select the "z" option; or you can use the -z option (or -Z if you also want to wipe the MBR) to sgdisk. The actual wipe operation will take a fraction of a second; you'll spend more time typing to activate the correct options than the program will take to do the job.

If you need more advice, I suggest you post more details, including the type of disk you've got (make and model), whether you're using a RAID configuration, and why you don't want to use GPT.

---

