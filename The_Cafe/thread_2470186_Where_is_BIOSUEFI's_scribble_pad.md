---
title: "Where is BIOS/UEFI's scribble pad?"
date: 2021-12-21
forum: The Cafe
---

### Post by nginmu on 2021-12-21
There are broadly 3 areas of read/writable semiconductor memory on a x86/AMD64 PC, outside of disks, video cards etc, I can think of..

Processor cache;
CMOS memory chip;
RAM sticks.

When the BIOS or UEFI first runs the POST, starting at the reset vector address high up in the memory map, and shortly after whilst it's still setting up the hardware, what memory outside the ROM does it use before it hands over to the bootloader?

My programming experience is limited to a handful of high level beginner & scripting languages so I'm not hugely familiar with the fine details of hardware & memory geography.

I sort of imagine the BIOS starts off using only bits of processor cache, then as the boot progresses it starts to read and write stuff in the CMOS memory chip as well, before later on in the process, maybe it begins to start adding in some use of the main RAM too?

If anyone knows any good pages that cover this sort of thing that would be a good help to my understanding.

---

### Post by GhX6GZMB on 2021-12-21
Why do you think that main RAM doesn't work from start?
It does.
That the OS might reallocate later on is a different issue.

---

### Post by nginmu on 2021-12-21
I thought the POST would have to find the main RAM first before it could R/W it, and it would use maybe, CMOS or CPU cache as 'temporary notepad' before it did. So, the RAM is accessible to the POST process right from the first instruction at the reset vector, purely by virtue of the motherboard's electrical design, yes?

---

### Post by GhX6GZMB on 2021-12-22
CPU = HW
Memory controller = HW
RAM = HW
Of course it works. Otherwise nothing would. It can very well be that the machine starts at lowest speed (to ensure component compatibility) before the system has been fully explored by the firmware, but that's irrelevant.
Cache is also HW and will only work if main RAM works.
CMOS memory is quite small and not useful.

And I've no idea what "POST" means (except sending a letter or playing on FB).

---

### Post by nginmu on 2021-12-22
power on self test.. just after one releases power button

---

### Post by GhX6GZMB on 2021-12-23
Well, at least it's an FLA (aka ETLA) and not just a TLA.

---

### Post by nginmu on 2021-12-28
Some interesting stuff here on the subject, seems to say the RAM is unavailable in the very earliest stages & something called cache-as-RAM is used instead

[https://binarydebt.wordpress.com/2018/10/06/how-does-an-x86-processor-boot/](https://binarydebt.wordpress.com/2018/10/06/how-does-an-x86-processor-boot/)

---

