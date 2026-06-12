---
title: "The disk drive for /home is not ready yet or not present"
date: 2013-06-09
forum: Server Platforms
---

### Post by kevmev12 on 2013-06-09
Hi guys,

Let me preface this by saying I'm a Linux and server newbie and I am trying to learn. About 3 years ago I built a home server using Ubuntu Server 10.04 LTS. I had the OS installed on an 80GB disk, and then I partitioned 4 x 1TB disks to RAID5 in software RAID. It has worked trouble-free and wonderfully well for the last 3 years and it was a great experience in learning how to install and configure Ubuntu Server.

About 2 weeks ago during boot-up, I was alerted to the fact that one of the 1TB disks has a bad SMART status; looks like it's time to replace one of the 1TB disks. The server still worked fine, just that every the server boots up I get reminded that I need to replace the disk. This morning as I tried to turn on the server in order to back-up all my stuff to prepare for disk replacement, this error comes up:

[B]/dev/sda2: clean, 570369/4644864 files, 2029517/18561024 blocks
The disk drive for /home is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery

[/B]From what I can understand, I think it means the OS is unable to mount the RAID because the /home directory is missing. If I press S to skip mounting and log into the server, it appears I can only see the OS drive and not any of the RAID drives. If I press M and then fdisk -l, I can see all the drives present - including the 1TB disks which is listed as 'Linux RAID Autodetect'.

I suspect this has nothing to do with the RAID or the 1TB disk with the bad SMART status - I think it might be something wrong with the OS or the 80GB disk that the OS is installed on. Am I correct in that assumption? What are the checks I should be running to confirm my suspicion? What is my next step in trying to resolve this issue?

I would appreciate any help you can give me. Thank you for your time.

-Kevin-

---

### Post by carl4926 on 2013-06-09
I've seen this very briefly but only in Linux Mint.
What I mean is, I see it, then it's gone and everything behaves normally.
Not RAID though
But /home is separate

Seen it before, but again, only in Mint

---

### Post by SeijiSensei on 2013-06-10
Probably you need to run mdadm to analyze the RAID and take the faulty disk out of service.  It's likely you'll need to do this after booting into recovery mode.

You might start by reading this: [https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery)

---

