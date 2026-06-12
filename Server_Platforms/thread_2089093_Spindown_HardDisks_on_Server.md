---
title: "Spindown HardDisks on Server"
date: 2012-11-28
forum: Server Platforms
---

### Post by lseg on 2012-11-28
Hi Everybody,

I have a home server with Ubuntu 12.04 (desktop version, I sometimes do like GUIs), with Software Raid 5 configuration (3 disks).

On these 3 disks I also have my OS.

Question now is: How can I make my Harddisks go to idle ?

First question is: How can I check if they spun down or not (preferably on a timeline) ?

I believe the main reason why my disks never spin down are all these logs that are being stored, by the kernel and by other applications.
Is this correct ?

Is it possible to route all these log files to a USB flash drive, or somehow limit the logging to every 6 hours instead of every 15 seconds ?

How can I detect who is writing what to my HardDisk on a time line, so I can detect how frequent things are being written to my harddisks, and which processes I should deal with?

Kind regards,

Luc

---

### Post by rubylaser on 2012-11-28
With your OS being on the same disks, spinning these down is going to be very tricky, if not impossible because the OS is never truly idle.  I would separate your RAID5 array from your OS drive.  I'd run the OS from a small SSD(s) or Flash drive (if you'd like to RAID1 the OS).

If you go this way, your SSD or flash drive will draw almost no power and your disks can easily be [spun down]("http://zackreed.me/articles/60-spin-down-idle-hard-disks").

---

### Post by lseg on 2012-11-28
Ok,

It seems a bit exagerated to me to buy an extra small SSD, only to reduce the power by approximately 3x6W = 18Watt (and probably adding some Watts for the SSD).

Economically it doesn't seem the right thing to do.

Kind regards,

Luc

---

### Post by dannyboy79 on 2012-11-28
his whole point was that you shouldn't have installed the OS within the RAID array. It should be on it's own HDD, whether that's an SSD, an HDD, or a Flash Drive. IF you want your raid disks to spin down, you'll need to seperate the OS from the raid array.

---

### Post by rubylaser on 2012-11-28
> **lseg said:**
> Ok,
It seems a bit exagerated to me to buy an extra small SSD, only to reduce the power by approximately 3x6W = 18Watt (and probably adding some Watts for the SSD).
Economically it doesn't seem the right thing to do.
Kind regards,
Luc

Nope, I would agree, but I just wanted to present the option to you :)  As it's currently setup, you are stuck with having all your disks spun up full time.

---

### Post by lseg on 2012-11-28
I was just wondering if it was possible, since this is basically what those NAS makers are already doing. 
I could not imagine that they are only using the very small flashmemory they have on their motherboard, to do all loggings etc.

But as you are stating it now, they probably are doing exactly that.

Kind regards,

Luc

---

### Post by darkod on 2012-11-28
If I may add, you have one option that might be cheaper than buying a small SSD.
You can buy a Compact Flash to SATA adapter, and depending of the space the server install uses right now, a 4GB/8GB/16GB CF card. They are compatible replacement of hard disks, bootable, etc, you can easily run OS from them.

Especially if you are in the USA those adapters and CF cards would be dirty cheap. Check Ebay or similar websites.

The HDDs might consume only 18W but make the 24/7 calculation and see the electricity math over a longer period of time.

---

### Post by lseg on 2012-11-28
Would an USB3 stick be an option ? Or would that still be too slow ? Maybe 2 Sticks in Raid1 (Or maybe keep a copy on the HDDs).

I am a bit worried about the performance, although I understood that kernel for example is loaded in memory, so that should not be a problem.

Compact Flash seems a bit ancient technology.

I think my Ubuntu Installation takes about 10Gb, so that would not be a problem.

Kind regards,

Luc

---

### Post by darkod on 2012-11-28
I wouldn't worry too much about the speed. Especially if accessing many smaller files, a flash memory (CF, SD, usb stick) would usually be faster than HDD. Flash memory has very low access time, which is why SSDs are much faster than HDDs in random access.

I think you should be fine with USB2 stick, no need to spend extra money for USB3 (unless the price is similar). I wouldn't complicate it further with usb sticks in raid or similar.

I haven't investigated the detailed information and specification, but if I remember correctly I think CF cards are designed for larger number of read/write cycles compared to SD cards or usb sticks. That's also something to consider, you don't want it failing too soon. They might sound like old tech but I think CF cards are precisely the ones used for embedded and small devices. That's why there are CF to SATA and CF to IDE adapters on the market.

---

