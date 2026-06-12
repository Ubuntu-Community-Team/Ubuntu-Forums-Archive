---
title: "questions on ramdisk"
date: 2011-08-05
forum: Server Platforms
---

### Post by scott1256ca on 2011-08-05
Background:
I decided to create my own NAS, starting with ubuntu server. I want to install onto a usb flash drive, and got to thinking about the log writes, which I'd rather not have written to flash frequently. 
So I thought of using a ramdisk, and maybe writing something to dump them to hard drive every now and then (I have no schedule in mind yet, I'm just getting started). Did a search and found that /dev/shm is already set up to act as a ramdisk.

Questions:

What does linux usually do with this ramdisk? The only things on my desktop ramdrive are some pulse-shm-[0-9]* files.

I read that by default 1/2 of ram is set aside for the ramdisk. Is that correct, or is that out of date?

Is there any reason I shouldn't redirect log files there (provided I limit the space they use)?

Is there any advantage to increasing/decreasing the size of the ramdisk? Some help answering this may be in the info below.

System:
atom based
4G ram
2G usb stick (not very fast).
Drives I'll be connecting will be green 2T drives. NOT RAID. Maybe RAID in the future, but not planned for now.
Will be used as NAS/dlna. Not really planning anything else yet.

Thanks in advance

---

