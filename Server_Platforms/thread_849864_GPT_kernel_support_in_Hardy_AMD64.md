---
title: "GPT kernel support in Hardy AMD64?"
date: 2008-07-04
forum: Server Platforms
---

### Post by cgreen on 2008-07-04
My server is running RAID6 and has around 4TB of disk space in a single partition (and a chunk for the OS which is separate). I had to use parted 1.8.8 to configure this using a GPT disk label (an MSDOS disk label doesn't allow for partitions over 2TB, and there is a serious bug in parted 1.7.x which causes GPT partitions to be very unstable). The kernel version is the latest release (2.6.24-19-server AMD64).

I've come across an online article that said that in order for GPT to be 100% reliable there needs to be some support in the kernel, and this support is achieved by setting CONFIG_EFI_PARTITION to 'y' at kernel compile time.

(See: [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html))

My question is - how can I tell whether the kernel I'm running has this option enabled already? I'm not seeing any problems so far - but I'm concerned that this might blow up in my face one day.

I've googled myself silly on this and I'm clearly not using the right search terms (Google knows EVERYTHING, right?), so any help or nudges in the right direction from you guys would be much appreciated.

**Update:** I've discovered that Ubuntu saves the config used to build the kernel in /boot - the file is called config-2.6.24-19-server in my case. Happily I find that CONFIG_EFI_PARTITIONS=y so my 4TB partition should be fine. Watch out for that parted bug though. This thread was really helpful: [http://ubuntuforums.org/showthread.php?t=716793](http://ubuntuforums.org/showthread.php?t=716793)

---

### Post by windependence on 2008-07-05
Why RAID 6? I would have to look up what kind of striping that even was. RAID 0, 1, 5 , and 10 are pretty popular but 6? What IS that.

-Tim


EDIT: OK so it's double parity. You are really paranoid and have lots of money for disks.

---

### Post by cgreen on 2008-07-05
Hi Tim,

I sell space to third parties as a secure storage solution. The cost of RAID5 plus one extra disk is much cheaper than RAID10 for my configuration, and I've recently seen two RAID5 machines lose more than one hard drive simultaneously. So not paranoid really, just practical in these circumstances. And beneficial from a marketing point of view too.

C

---

