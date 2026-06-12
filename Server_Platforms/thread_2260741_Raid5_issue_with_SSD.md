---
title: "Raid5 issue with SSD"
date: 2015-01-14
forum: Server Platforms
---

### Post by G-Dane on 2015-01-14
Hi guys,

My setup is 14.04.1 software raid with SSD disks.

I works flawlessly with raid10 and the fstrim function works out-of-the-box. But with the exact same disks in raid5, the trim function does not seem to be working. I have read that some makes it work and some don't.

Should I abandon the raid5/ssd/fstrim setup, or does anybody have an idea to get it working?

---

### Post by tgalati4 on 2015-01-14
Why do you need RAID-anything with SSD?  Typically RAID gives improvements in speed or availability or both with spinning disks.  There is less of a benefit with SSD's.  If you need RAID and RAID10 works, then why would you use RAID5?  

How do you know that trim is not working with RAID5?

---

### Post by kpatz on 2015-01-14
You could try running fstrim with the -v option to get more information on what it is, or isn't, doing.  Or try **mount -o remount,discard** and then check dmesg afterward (make sure to **mount -o remount** without the discard afterward).

What software RAID are you using?  From what I've found in google searching, at least as of a year or two ago TRIM wasn't supported in software RAID, but maybe it was added to RAID 1/10.  RAID 5 is a different beast since there's a parity disk involved, and discarding the parity blocks would mess up the array.

---

### Post by G-Dane on 2015-01-14
> **tgalati4 said:**
> Why do you need RAID-anything with SSD?  Typically RAID gives improvements in speed or availability or both with spinning disks.  There is less of a benefit with SSD's.  If you need RAID and RAID10 works, then why would you use RAID5?  

How do you know that trim is not working with RAID5?

My goal is not speed, but greater security against diskfailure combined with the most storage. I could settle with raid10, but raid5 offers the most storage. I have testet with fresh installs of both raid setups.

---

### Post by G-Dane on 2015-01-14
> **kpatz said:**
> You could try running fstrim with the -v option to get more information on what it is, or isn't, doing.  Or try **mount -o remount,discard** and then check dmesg afterward (make sure to **mount -o remount** without the discard afterward).

What software RAID are you using?  From what I've found in google searching, at least as of a year or two ago TRIM wasn't supported in software RAID, but maybe it was added to RAID 1/10.  RAID 5 is a different beast since there's a parity disk involved, and discarding the parity blocks would mess up the array.

I have tried fstrim with the -v flag unsuccesfully. In fstab I have also tried the discard option, also without succes.

The software raid I am using is the default from ubuntu, mdraid. I have also found out that fstrim have been implemented for some years in Raid 1/10, but regarding Raid5 there are some mixed opinions, as where some say they have got it working and others say it is a mission impossible as the way trim work are not compatible with the way raid5 returns requests.

I have hoping that maybe somebody had some experience they would share

---

