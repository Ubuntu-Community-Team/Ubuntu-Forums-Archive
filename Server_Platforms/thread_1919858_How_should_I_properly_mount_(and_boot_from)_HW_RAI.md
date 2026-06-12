---
title: "How should I properly mount (and boot from) HW RAID 5 array?"
date: 2012-02-03
forum: Server Platforms
---

### Post by oakleym82 on 2012-02-03
Let me start by saying that I'm an Ubuntu n00b, but I'm not totally lost.

Here's my hardware:

[LIST]
[*]2U PC (64 bit Intel)
[*]Adaptec 3405 SAS RAID controller
[*]4x 750GB? HDDs
[/LIST]
(Note: No separate boot drive, only the array in this machine, I want to boot from the array unless it's a really bad idea)

Here's what I've done:

[LIST]
[*]Powered on PC, entered the Adaptec 3405's UI with Ctrl-A.
[*]Configured my RAID 5 array
[*]Booted from Ubuntu CD and installed 10.04.3 LTS on the resulting 2.2TB array
[/LIST]

works great.

Problem:  I want to be able to monitor the health of my array without having to look at the LEDs on the card.

I downloaded the Adaptec Storage Manager (ASM) RPM, covered it to a DEB, installed it, and it detected my card and the array, and then a few hours later started beeping and telling me the array was degraded and drive 0 had been dropped.  I rebooted and the card rebuilt the array (took 1.5 hours), and Ubuntu came back up.  This happened again, and happens like 1-2 times a day.  

I uninstalled ASM and waited a few days, rebooted and went into the card's UI and the array is health and optimized.  Maybe I had accidentally installed the ASM utility for the 2405 card?  I don't think I did, but I'm afraid to try again.  I have a backup of all of the stuff on this array, but it's in production and I don't want to break it unless I really have to reinstall, and I'd like to do that on the weekend.

I think I messed up because my array is mounted at /dev/sda1, and appears under "Peripheral Devices" in Disk Utility.  I'm thinking it should be mounted under /dev/mapper?  or maybe /dev/aacd[x] and appear under "Host Adapter AAC-RAID" in Disk Utility?

Help??

-Matt

---

### Post by oakleym82 on 2012-02-06
bump.

anything I can contribute to get some help in this matter?

I'm thinking I need to reinstall Ubuntu with the proper driver.  Thoughts?

---

### Post by rubylaser on 2012-02-06
It sounds like you have a bad hard drive, and it's just rebuilding the array, only to have it fail again.  Have you verified if it's the same disk falling out of the array repeatedly?  If so, I'd replace that disk.

If the ASM can see your disks, it sounds like you have the correct version.

---

