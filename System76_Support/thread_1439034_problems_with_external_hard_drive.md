---
title: "problems with external hard drive"
date: 2010-03-25
forum: System76 Support
---

### Post by porlaizquierda on 2010-03-25
i just recently bought a seagate 500 GB external hard drive. just a few minutes ago i was transferring some files when another window popped up. i simple closed the window when another window showed up. now when i try to mount my hard drive i get this:

UNABLE TO MOUNT EXPANSION DRIVE

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details

does anyone know what that means? i'm going to go to the seagate website for help too, but i wanted to try here first. can anyone help?

---

### Post by porlaizquierda on 2010-03-25
well never mind. i reformatted. it's not that big of a deal since i already have everything on my actual computer. but can anyone maybe explain this just in case it happens to someone else?

---

### Post by bill516 on 2010-03-26
My immediate reaction is that these external drive devices are optimized for use on Windows XP/Vista/7 and they fuss about being used on Linux when they cannot find their Windows hooks.  You appear to have solved your problem when you reformatted your Seagate.  I had a very similar problem with a WD 500 Gig "My Passport" external drive.  In that case the best response is to go to the WD site where a person can find instructions for disabling the "hidden" partition that the WD drive contains.

Apparently in your case simply reformatting the Seagate drive worked.  With a WD this will not work because the formatting software (e.g., GParted) cannot see that WD hidden partition at all.

So with the WD borrow a Windows computer so you can turn off the Windows-specific backup software preloaded on the drive (because they assume you want to use for Windows backup).  To do so follow instructions on the WD site.  Then reformat the drive as you would prefer for your purposes.  I used GParted and that worked just fine.

The problem with that Seagate could be very different than I assume, but I doubt it.  It surely would be nice to be able to purchase an external drive without the built-in clutter!  And it does cost a certain loss in capacity with the WD.  That is irritating.  But there are 450+ Gigs or so after all is done.  Not too long ago we would have thought that was amazing.  And in such a small form factor it really is remarkable.

---

### Post by thomasaaron on 2010-03-26
Based on the error messages, it looks like the drive was formatted with NTFS (Windows' filesystem). Typically, Ubuntu does a good job of navigating NTFS. But my guess is that either there was a failure of that filesystem, or you happened across a bug in Ubuntu's ability to work with NTFS.

Either way, reformatting it was probably the best thing to do. Good job.

---

### Post by jdb on 2010-03-26
> **bill516 said:**
> 
Apparently in your case simply reformatting the Seagate drive worked.  With a WD this will not work because the formatting software (e.g., GParted) cannot see that WD hidden partition at all.



In Gparted if you select the "Device" menu and "Create Partition Table"
I think it will get rid of any hidden partitions & give you a clean slate to partition.

jdb

---

