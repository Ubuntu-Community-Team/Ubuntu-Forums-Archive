---
title: "just installed Ubuntu on my flash drive"
date: 2008-09-19
forum: The Cafe
---

### Post by chris4585 on 2008-09-19
This was just to do something with it, nothing special, but yeah it worked, was pretty easy, and I could definitely tell the difference from installing on a HDD and a flash drive, there's at least a 20 - 30min difference on the same fast hardware on installing.  I understand why its so slow, but I didn't expect it to be as slow as it was.

My advise is to don't waste your time, unless you need it, because it does work, just really slow.

I"m using it atm btw

---

### Post by FuturePilot on 2008-09-19
That could probably ruin a flash drive pretty quickly because of the number of read and write cycles. It would probably be better to do something like a persistent USB install like how Fedora 9 can do [(link)]("https://fedorahosted.org/liveusb-creator"). Not to mention it would be much much faster. I think Ubuntu is planning something similar for Intrepid.

---

### Post by chris4585 on 2008-09-19
neat, I actually already knew that it would kill my flash drive faster, but its only $28 4gb flash drive, I'll more than likely whipe everything off my flash drive soon, I just though I'd mention it to some people pondering about doing what I did to save them some time

---

### Post by jcwmoore on 2008-09-19
[http://www.pendrivelinux.com]("http://www.pendrivelinux.com")

tutorials for ubuntu and other distros

---

### Post by chris4585 on 2008-09-19
lol @ our south park characters 

*shrug* I just thought that was funny, I mean when you think about it what are the coincidences of that happening in one thread

---

### Post by init1 on 2008-09-19
> **chris4585 said:**
> This was just to do something with it, nothing special, but yeah it worked, was pretty easy, and I could definitely tell the difference from installing on a HDD and a flash drive, there's at least a 20 - 30min difference on the same fast hardware on installing.  I understand why its so slow, but I didn't expect it to be as slow as it was.

My advise is to don't waste your time, unless you need it, because it does work, just really slow.

I"m using it atm btw
It's a lot better (and faster) to install it compressed like a live CD.

---

### Post by chris4585 on 2008-09-19
> **init1 said:**
> It's a lot better (and faster) to install it compressed like a live CD.

how come is this?

---

### Post by JT9161 on 2008-09-20
> **chris4585 said:**
> how come is this?
  
I believe with a live you have better read/write speeds, unless you have a really slow flash drive.

---

### Post by chris4585 on 2008-09-20
that makes sense

Well I scraped that small project, I deleted everything but /boot/ and resized the partition to about 175mbs (could be smaller) but thats plenty large enough, and then I edited my actually grub.lst on my system to display a message on grub on start up, so without my usb key in my laptop you can't boot anything without the flash drive

note, I do have grub password protected on both usb and my system

---

### Post by nowin4me on 2008-09-20
Dose Windows recognize the USB key?

It's just because Windows can't see ext2/3 without software being installed.

---

### Post by chris4585 on 2008-09-20
> **nowin4me said:**
> Dose Windows recognize the USB key?

It's just because Windows can't see ext2/3 without software being installed.

any computer with bios with the ability to boot usb devices will boot it, and windows will recognize the fat32 partition on it, but thats about it

---

