---
title: "Ubuntu as the basis for a NAS box"
date: 2010-04-03
forum: Server Platforms
---

### Post by XEyedBear on 2010-04-03
I am considering building my own NAS box for use on my home network, as a much cheaper alternative to buying one. The primary function is to be able to share a growing library of photographs  (currently about 150GB in size, growing at 1 GB per week) among the (mostly XP or Wn 7) computers, with a secondary objective of acting as a reliable storage for other data I have and thirdly as a print server.

I assume Ubuntu is a suitable Linux distro for this task? 

I would prefer it over, say OpenSUSE, as I have found it much easier to get SAMBA shares working under Ubuntu. A concern I have is that the performance may not be as good as a dedicated motherboard built only for a NAS function  (I plan to use a spare ASUS A8V motherboard with a 2.2GHz socket 939 AMD processor with 2GB RAM). What steps should I take to esusre that the Ubuntu installation is as small and quick as possible?

I plan to use 2 250GB drives in RAID 1 to start. Does Ubuntu server have functions which can spin the drives down when they haven't been accessed for some time? Can the whole system be configured to put itself to sleep, say overnight, without my intervention at either the start of the day or the end of the day?

Advice greatly appreciated.

---

### Post by CharlesA on 2010-04-03
It can be done with Ubuntu. You shouldn't really notice any major performance issues compared to a "regular" NAS box.

I know you can use mdadm to so software raid, but I don't know the syntax off the top of my head.

I seem to recall that there was a thread talking about using WoL to wake up a system that had been put to sleep after a period of inactivty, but I cannot recall what the thread's name was.

---

### Post by XEyedBear on 2010-04-03
I didn't think I would have to use any software RAID emulation tools, because there is RAID capability on the motherboard. I assumed that Ubuntu would just 'see' a single drive. Is this correct?

I have previously used this motherboard, with RAID 1, in a Win/XP installation where the read performance was most satisfactory - and that's mostly what I would want to do anyway. That is, I don't think the slower write performance of a RAID 1, using SATA I (150 MB/sec) drives, is going to be a big issue.

---

### Post by CharlesA on 2010-04-03
Oh, if you are using RAID on the mobo, it should just see 1 drive.

It should be fine, the only iffy part is how you would configure an array configured in the BIOS. I know that there was a utility for setting up RAID in Windows, but none for Linux, and that was on a Gigabyte mobo that had RAID 0,1, JBOD functionality (I ended up not bothering with RAID on the mobo and just got a cheap HW RAID card that worked with Linux.

---

### Post by Adina on 2010-04-03
You can set spindown time in /etc/hdparm.conf if you uncomment the line with #spindown_time = 24

If only linux machines need to connect to your "NAS-box" you should use NFS-server. It is super fast, just like a disk on your local system, simpler to set up than samba too.

---

