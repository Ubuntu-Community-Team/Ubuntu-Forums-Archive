---
title: "ubuntu on sdcard"
date: 2015-03-14
forum: Ubuntu, Linux and OS Chat
---

### Post by kerry_s on 2015-03-14
i was wondering if there was anything that needed to be done for sdcard, should i treat it like a ssd ?

i'm asking cause i know there’s a few raspberry pi users here who run linux everyday from sdcard & figured you would know how to get the best out of such a setup.

i'm running on my normal desktop through a sdcard reader, i pretty much did a straight forward install from usb, the boot loader is on the sdcard, it's a stand alone install, i remove when not using, boot from the card for ubuntu.

specs:
ubuntu 14lts
atom 330 1.6ghz x4
2gb ram, swap is done with a auto swap file 2gb's. (dphys-swapfile)
running on 64gb micro sdcard

let me get your thoughts, i'm just messing around so no problems blowing it away & starting over if need be. now that i know it works & runs pretty good, not as slow as i thought it would be, it's pretty much as fast as a normal hd install.

---

### Post by kerry_s on 2015-03-15
so a friend gave me a busted up laptop it's a toshiba satellite t-135, he dropped it about a year ago & it was put away, he just bought a replacement & moved on. the top right of the screen is all broken pieces missing, but the screen is fine just shell damage. the hard drive is also toasted & i can't get it out, cause i don't have the tool to fit the special screws. so i used the sd card as a hard drive and it seems to be working, i've disabled the hd in bios so i don't have to hit f1 at every boot, the sdcard boots first works just fine.

specs:
elementary os
dual core intel 1.3ghz
2gb ram
using 64gb micro sd card in adapter

so no body has tips for sd card install ?

---

### Post by kerry_s on 2015-03-15
so far:

> sdcard treat like a hd
don't try to use the /tmp tweak or the ramlock, ramvar. it will cause mount issues with the sd card. pretty much just install & use
if you have intel or amd install microcode. sudo apt-get install intel-microcode or  sudo apt-get install amd64-microcode , if you have old firmware this will fix, cut my boot time after installing.
don't touch fstab, it won't mount if you modify, so no adding nodata,nodirtatime
if you have enough ram, i have 2gb, don't use swap, it runs better.

will edit with what ever comes up still trying things i find

---

### Post by kerry_s on 2015-03-17
i managed to get the broken hard drive out, still messing with the sd card as hard drive.
currently have elementary os luna 32bit, runs fine, a little laggy at times, sd card access is slower than regular drive.

up next is xubuntu 64bit 14.0.4.2 lts, i made the installer, just waiting till i'm in the mood. lol

---

### Post by tgalati4 on 2015-03-18
The SD card is probably on a USB2 connection which typically 35 MBytes/sec.  A typical SATA notebook hard disk throughput is 45 to 75 MBytes/sec depending on the disk.

My guess is that your SD card will work for a few months or a few years until it wears out.  The constant poking of flash memory locations will wear them out.  Some suggest running strickly in RAM disk and then dumping the image to SD as you sleep--sort of hibernate-to-disk.  SD cards tend to be optimized for large file writes in a serial manner--like using in a digital camera.  Lots of small random writes (as in an OS) will cause slow downs as the card fills up.

I have read that when you reach TB levels of writes to an SD that it is shot, so that is something you can monitor.

> tgalati4@Mint17 ~ $ sudo dumpe2fs /dev/sda1 | grep Lifetime
dumpe2fs 1.42.9 (4-Feb-2014)
Lifetime writes:          135 GB

---

### Post by kerry_s on 2015-03-18
i am planning to put a drive in, now that i got the old 1 out. just not in the budget right now, so i'm using what i have.

i got xubuntu installed it is pretty fast, most of it is kept in ram already, i'll see the light on when it's writing to sd. i dumped swap, not using swap at all makes a huge difference. suspend works, it is so fast waking. it says i don't have that program installed. have to wait till later cause it's updating.

my bag typo, lol
it only gives me the dumpe2fs version number, i don't get that lifetime writes line. it's a 64gb class 10 made for video cameras.

what shocks me most is the laptop battery still lasts 8 hours after sitting in a drawer for so many years. lol

---

### Post by tgalati4 on 2015-03-18
Try paging through the output:

```
sudo dumpe2fs /dev/sda1 | more
```

There is a certain satisfaction in resurrecting old computers and putting them to work.

---

### Post by kerry_s on 2015-03-18
it says 7711mb

i'm setting it up simple, no menu on the panel, just 4 icons on the desktop-> firefox, home, trash, logout
i'll probably put for the kids to use. not sure, it took a bit of glue to hold it back together, not very kid proof if they move it around. i could give them the desktop & use the laptop, not ready for that yet. lol

---

### Post by gordintoronto on 2015-03-19
You might find that Xubuntu provides a better experience with that configuration. I'm currently testing Xubuntu 15.04, running from a USB 3.0 flash drive plugged into a USB 2.0 port, and I'm delighted with the performance.

> **kerry_s said:**
> i was wondering if there was anything that needed to be done for sdcard, should i treat it like a ssd ?

i'm asking cause i know there’s a few raspberry pi users here who run linux everyday from sdcard & figured you would know how to get the best out of such a setup.

i'm running on my normal desktop through a sdcard reader, i pretty much did a straight forward install from usb, the boot loader is on the sdcard, it's a stand alone install, i remove when not using, boot from the card for ubuntu.

specs:
ubuntu 14lts
atom 330 1.6ghz x4
2gb ram, swap is done with a auto swap file 2gb's. (dphys-swapfile)
running on 64gb micro sdcard

let me get your thoughts, i'm just messing around so no problems blowing it away & starting over if need be. now that i know it works & runs pretty good, not as slow as i thought it would be, it's pretty much as fast as a normal hd install.

---

### Post by kerry_s on 2015-03-19
> **gordintoronto said:**
> You might find that Xubuntu provides a better experience with that configuration. I'm currently testing Xubuntu 15.04, running from a USB 3.0 flash drive plugged into a USB 2.0 port, and I'm delighted with the performance.

i currently do have xubuntu on it, but i was planning on trying some lubuntu next. 
my friend says he has 1 of those sdcard to sata adapters i can have, he just got to find it on his day off cause he's pretty sure he put it in storage. can't wait to try that out.
performance is pretty good here to, once you open the app you want, it's just fast.

i'm currently messing around with lubuntu on my desktop, since i had the installer already made, fricken ubuntu unity bugged out on me for the 3rd time, nothing but a cursor & backgroud, so i figured just wipe it instead of reset it again, it was annoying me anyways with all the fading to gray while it thinks about something. lol

---

