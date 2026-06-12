---
title: "Failure of HDD drive in Raid 1 Config"
date: 2010-06-25
forum: Server Platforms
---

### Post by Hemantha on 2010-06-25
Hi Guys,
I have an issue. I had configured a Raid 1 on two 1tb drives and was working perfectly. Now one hdd drive has failed and i cannot boot with the other. 

I am being prompted to intramfs and it says that one hard disk is missing. 

Need your assistance to load the os from the other harddisk. and how i can later recreate the raid with a new drive.

Brgds,
Hemantha

---

### Post by critter.be on 2010-06-25
Can you connect the SATA connector from your failed (primary?) disk to the other disk in the mirror? Then connect the other SATA connector to a new disk or re-use the old one (after formatting it) if there's no physical damage.

Once booted, look at the recovery section of this page:
[http://kuparinen.org/martti/comp/ubuntu/en/raid.html#3]("http://kuparinen.org/martti/comp/ubuntu/en/raid.html#3")


Will.

---

### Post by Hemantha on 2010-06-25
Hi Will,
I had two identical drives, one drive had been stolen. Since these drives were out of use i do not know how to identify the primary and the secondary. i believe since gurb is not available on the drive that is available it is the secondary.

is there any way of recovering the data without setting up the mirror ??

I tired to access it through a windows pc with extfs but no luck it identifies the partition but cnt access. Tried through an old 6.06 live cd but the file system is identified as unknown.

all i have at the moment is the blank initramfs can't go anywhere from that......

---

### Post by Hemantha on 2010-06-26
Hi Guys,
I managed to solve this.

sudo mdadm -A -R /dev/md0 /dev/sdb1

where sdb1 was the raid partition on the working drive. Booted from the live CD. This mounted the raid in degraded mode, took ownership of the files and now backing it up for a fresh install.

Thanks for the help.............

Brgds,
Hemantha

:popcorn:

---

