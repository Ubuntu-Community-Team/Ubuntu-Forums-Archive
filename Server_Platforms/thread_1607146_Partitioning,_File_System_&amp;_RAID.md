---
title: "Partitioning, File System &amp; RAID"
date: 2010-10-27
forum: Server Platforms
---

### Post by molinus on 2010-10-27
Would someone please let me know if I am going the right direction with my plan as listed below?

I am a longtime Mac & PC user building a file server and website testing server (no hosting & no virtualization) with Ubuntu Server 10.04 LTS.  There will be 3 Mac & 7 PC users for the file server - very light usage.  
System: 64bit, Dual Quad Core Intels, ASUS MoBo, 24 GB DDR3, 6 - 1TB WD SATA Drives
I want to have 2 Ubuntu software RAID 1 sets - 2 drives + hot spare for Ubuntu OS & website testing, & 2 drives + hot spare for file server content.
I don't see a need for multiple partitions on any drives (my plan is 6 drives/6 partitions) - I won't be dual-booting OSs, and don't think I need a swap partition - I believe 24 GB RAM is plenty for the light usage & no virtualization.
I am planning ext3 file system for all partitions, and will be managing the server with Webmin.

I am new to Linux - does anyone see any glaring errors or a better way to do this?

Thanks very much

---

### Post by the_original_billq on 2010-10-27
When you say - "6 disks and 6 partitions", but then mention "2 disks for OS + 1 hot spare , 2 disks for data + 1 hot spare"  I assume you are doing a striped mirror using those 2 drives, then supplying a hot spare?  Sounds like a good, solid design.  The server should run fine with 24Gb RAM. You should have happy users.

-Bill

---

### Post by molinus on 2010-10-28
Thanks for the reply Bill.

The 2 RAID sets are RAID1 mirrored sets - each set is 2 drives plus 1 spare - the spares are actually hot-swap drives - I will take the 2 hot-swaps home with me each evening as off-site backup. 
With very light usage, I don't expect a big performance problem writing to 3 drives, and I like having both on-site and off-site backup coverage.

I mentioned partitions because I planned for the 6 drives to have only 1 partition each.  
Many of the Linux partitioning advice and tutorials I have read call for separate partitioning for home, swap, var, etc, usr, tmp, and so on and so on...

---

### Post by SeijiSensei on 2010-10-28
Having /home on a separate filesystem makes it possible to upgrade the operating system while keeping users' files untouched.  

Having /usr on a separate filesystem allows you to mount it read-only, which may be valuable for security purposes to protect the binaries from accidental or malicious meddling.

Having /tmp on a separate filesystem lets you mount it with the noexec flag to keep baddies from dumping executables into /tmp and running them from there.

Having /var on a separate filesystem is less compelling, though it does tend to isolate the heaviest read/write activity to that partition in cases where you're running a busy web, mail, or DB server.

Most of the time I just allocate separate partitions to /boot and /home and leave everything else in the root.

---

### Post by the_original_billq on 2010-10-28
Regarding partitioning, SeijiSensei is right on the money.

Regarding your RAID layout, however, note that a "hot-spare" is just an empty drive you can swap in for a failed RAID mirror component.  If you want it full of data, you'll want to create a 3-way mirror, then break the mirror each night when you want to take your offline copy home.  This won't be a "hot-spare" - as your RAID configuration won't have it available while it's sitting on your car seat :-)  Just a minor change in terminology, really.

Your usage sounds pretty light, but if it were to increase, perhaps I'd look at a server with hot-swap 10K RPM drives.  I think your existing setup should serve you well with a dozen users or so.

-Bill

---

### Post by molinus on 2010-10-29
Tons of thanks for the valuable input and your even more valuable time.

I think it may be better to create my RAID1 sets with 2 internal drives only, and use rsync to back up to the hot-swap (offsite) drives.

I was going to use the Ubuntu graphical installer, but maybe I need to read up on installing with command line in order to get both RAID1 OS drive bootable and the multiple file system partitions.

molinus

---

