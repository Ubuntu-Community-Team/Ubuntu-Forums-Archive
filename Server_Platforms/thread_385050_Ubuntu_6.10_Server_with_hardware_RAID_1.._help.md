---
title: "Ubuntu 6.10 Server with hardware RAID 1.. help?"
date: 2007-03-15
forum: Server Platforms
---

### Post by dudinatrix on 2007-03-15
Please forgive me as this is my first time setting up a server with a RAID configuration. I have a Dell PowerEdge SC 1430.. 2 Xeon 5050's with 2 160GB SATA drives pre-configured as  hardware RAID 1.

I'm about to install Ubuntu 6.10 Server, and I'm at the partitioning section. Since the drives are already configured as RAID 1, what do I need to do to go forward? Do I have to set up the software RAID 1 as well? I assume the hardware RAID supersedes the need for that. Do I have to worry about "ext3" vs "Physical Volume for RAID" or anything?

Anyway, my options stand at:

```
Erase entire disk: SCSI1 (8,0,0) (sda) - 159.0 GB Dell VIRTUAL DISK
Use the largest continuous free space
Erase entire disk and use LVM: SCSI1 (8,0,0) (sda) - 159.0 GB Del
Manually edit partition table
```This will be a Ubuntu server (LAMP), so nothing like dual booting or anything like that. What's the best way to set up the partitions/RAID?

---

### Post by matt_b on 2007-03-15
You are right - as you have set up hardware RAID you don't need to do anything special with RAID during your installation. Ubuntu will treat your RAID1 array as a physical disk. Go ahead and partition as you would any other install.

matt_b

---

### Post by ujeezy on 2007-03-15
I just did a RAID 1 install on Dapper.  The thing you have to look out for is whether you have actual hardware RAID or what is referred to as "fake RAID", a combination of hardware/software RAID.  Fake RAID setups are not recognized by Ubuntu, but I've read that Ubuntu's software RAID is better anyway (I've been wondering why this would be -- if anyone knows, please expand!)

This tutorial was extremely helpful: [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

---

### Post by dudinatrix on 2007-03-15
I'm still hesitating to move forward... at this point, I think I'm leaning towards Erasing the disk and using LVM. That automatically sets up the following partitions:

```

LVM VG Ubuntu, LV root - 152.GB Linux device-mapper
        #1 152.6 GB    f ext3        /
SCSI1 (8,0,0) (sda) - 159.0 GB Dell VIRTUAL DISK
        #1 primary 255.0 MB B f ext3 /boot
        #2 logical      6.2 GB   f swap swap
        #3 logical   152.6GB  K lvm

```The main thing I'm confused about is does LVM have anything to do with "software RAID", and do I need it if I already have preconfigured hardware RAID 1?

Otherwise, going the non-LVM method would create:
```
partition #1 of SCSI1 (8,0,0) (sda) as ext3
partition #5 of SCSI1 (8,0,0) (sda) as swap
```Then there's the question of which to use if I want a separate partition for /home, /var, /tmp, etc. I wouldn't be confused with this if it weren't for the dang RAID :)

---

### Post by dudinatrix on 2007-03-15
Thanks for the replies! It does appear to be pure hardware RAID, and Ubuntu seems to recognize it with no problems. So I think it's really just down to... use LVM or don't? :)

---

### Post by dudinatrix on 2007-03-15
Well, I went ahead and did "Erase entire disk and use LVM" .. but I wasn't able to add my own partitions such as /var and /home.... it just went right to the clock setup afterwards. Should I restart and choose "Manually edit partition table"?

---

### Post by matt_b on 2007-03-15
If this is a simple server install then I personally wouldn't bother with LVM - I'd just use "standard" partitions. Effectively you've got one 150GB drive - if you are unlikely to add more disks in the future or don't see yourself having disk space issues, why complicate things with LVM?

You certainly don't need to worry about software RAID - it looks like Ubuntu has already detected your hardware-level array correctly so there's not going to be any issues there.

---

