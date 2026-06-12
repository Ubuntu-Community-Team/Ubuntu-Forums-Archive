---
title: "Software RAID5 Ubuntu install"
date: 2010-11-26
forum: Server Platforms
---

### Post by mealies on 2010-11-26
I have a hp ml110 server with 4 500GB disks.  It only has fakeRAID so i want to install ubuntu server via Software RAID. 

i have read the install guide [here]("https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html").  As the Guide is for RAID1 i just need help tweaking the process

I understand that you can't boot of of a RAID5 partition so i assume you need to do the following.

create a /boot partition on the 1st 2 drives
create the /swap & / & /home partitions on all four drives.

On the /boot partition, select the bootable flag

Would the above steps give me a working installation?  Would i need to do anything else to boot into Ubuntu after install?

Thanks

Andrew

---

### Post by any.linux12 on 2010-11-26
> **mealies said:**
> I have a hp ml110 server with 4 500GB disks.  It only has fakeRAID so i want to install ubuntu server via Software RAID. 

i have read the install guide [here]("https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html").  As the Guide is for RAID1 i just need help tweaking the process

I understand that you can't boot of of a RAID5 partition so i assume you need to do the following.

create a /boot partition on the 1st 2 drives
create the /swap & / & /home partitions on all four drives.

On the /boot partition, select the bootable flag

Would the above steps give me a working installation?  Would i need to do anything else to boot into Ubuntu after install?

Thanks

Andrew

Did you try to install with hardware RAID? I have a pc with a fake RAID1 and it works well.

You can try to boot your pc with a software called "super grub loader" and if it work with that it's easier to understand why it doesn't work without cd.

---

### Post by chideock on 2010-11-26
RAID3 works fine following the instructions. If you are using the latest versions of Ubuntu you do not have to set the flag - skip that step.

I used "/" (root), a swap partition and a "/home"  -- that worked OK

---

### Post by annoyingrob on 2010-11-26
> **mealies said:**
> I understand that you can't boot of of a RAID5 partition so i assume you need to do the following.

create a /boot partition on the 1st 2 drives
create the /swap & / & /home partitions on all four drives.

On the /boot partition, select the bootable flag

Would the above steps give me a working installation?  Would i need to do anything else to boot into Ubuntu after install?

Thanks

Andrew
I'm not sure if booting off of RAID5 is still a problem or not. With that being said, RAID1 for /boot is pretty common.

You seem to have the right idea, create raid partitions on two drives (or all 4 if you really want), mark them as bootable (both of them. You would hate to have one drive die, and not be able to use the other because it's not bootable), and set them up as RAID1 for /boot. 

Create 3 more raid partitions on each of the drives. Set one partition on each as RAID5 for /, one partition on each as RAID5 for /home, and one partition on each as RAID0 for swap. 

Note: Personally, I raid0 swap space across all drives, but I'm not sure how it would handle a drive being missing. It may be better running 4 separate swap partitions instead.

I used to have a server with 6x drives software RAID5 for OS, and another 12xdrives RAID5 for data. All 18 drives were SCSI, and boy did it take a long time to spin up during power on. Currently, I run 4xRaptors in RAID0 on my desktop.

---

### Post by mealies on 2010-11-27
Thanks for all the advice.

As soon as i have finished backing up the current drives i will try the install process.

I hadn't even heard of RAID3 before so i will look into that.  For now i will go ahead with the RAID5 install as i understand that better.

I will update once i have done the install.

Andrew

---

### Post by mealies on 2010-11-27
UPDATE:

I tried installing ubuntu server as per instructions and it didn't work.  it just sat with a blinking cursor for 5 minutes and then failed.

For each of the 4 drives i created 3 partitions.   /boot (500mb)  /(445GB)  /swap (5GB)
for the boot device i created a RAID1 drive from sda1 sdb1.  for / & /swap i created a RAID5 drive from sdba, sdb, sdc & sdd.

No errors were reported on install and everything seemed to go ok.  on Reboot nothing was found.

the installer reported GRUB being installed to sda & sdb

Any ideas on what i did wrong?

Andrew

---

