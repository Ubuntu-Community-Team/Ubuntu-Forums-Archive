---
title: "daily-canary vs daily-live"
date: 2021-07-08
forum: Ubuntu Development Version
---

### Post by VMC on 2021-07-08
No idea what canary is, just read about it a few weeks ago in another thread. So today reading this thread:
[https://ubuntuforums.org/showthread.php?t=2464651](https://ubuntuforums.org/showthread.php?t=2464651), thought I would compare canary vs dail-live. Wow! 30.1% zsync difference to start.
Normally I zsync this: "http://cdimage.ubuntu.com/daily-live/pending/impish-desktop-amd64.iso.zsync".

So where is the canary info, and why the difference? For one, its the new install program. Is there more?

---

### Post by VMC on 2021-07-08
I've tried both now, and ventoy shows the new install, but a usb stick doesn't. Don't know why.

---

### Post by sudodus on 2021-07-08
What do you mean by

> **VMC said:**
> I've tried both now, and ventoy shows the new install, but a usb stick doesn't. Don't know why.

?

A couple of weeks ago I cloned from the canary iso file and [I saw the new installer](https://ubuntuforums.org/showthread.php?t=2463829&p=14045395#post14045395) (but it did not work all the way). Of course it might have changed, and I can test that, but I don't know yet what to look for. For example, how did you create the system in the USB stick? And how does ventoy show it?

---

### Post by VMC on 2021-07-08
The canary iso is much larger than daily-live. The canary comes up and asks for user name and location then says welcome. The installer part is exactly the same as daily-live.
One thing I did notice, is canary has a lot of errors on boot up. daily-live doesn't.

---

### Post by sudodus on 2021-07-08
If I understand correctly, the canary version is a very early testing version (maybe made for insiders / developers). We should expect that several things will not work yet.

- At first boot after installation with ubiquity I also notice that the install system comes up and asks for user name and location then says welcome. [This happens also with persistent live systems created by mkusb-dus](https://ubuntuforums.org/showthread.php?t=2463829&p=14045204#post14045204) from the canary iso file.

- But there is also another installer, that was not yet fully functional when I tested it. I describe [how to find that installer](https://ubuntuforums.org/showthread.php?t=2463829&p=14045395#post14045395) in the link from my previous post in this thread.

---

### Post by VMC on 2021-07-08
@sudodus, I think your right, its a work in progress. I'll keep zsync'ing daily-live.

---

### Post by onflash on 2021-08-22
The canary ISO's installer concept looks good - I was able to set the display to 1024x768 in VirtualBox.  The classic installer stays in 640x480 in VirtualBox.

It looks like the partitioning tool isn't functional yet, though.  I keep checking the installers of mainstream distributions to check for f2fs in one of the custom partitioning screens. :-)

---

### Post by VMC on 2021-08-23
I gave up on Canary, once I found out it depends, uses, Snap.

---

### Post by onflash on 2021-08-23
I noticed that yesterday while checking out what was running using the newly-available terminal. :-)

If an installer lets me set up an f2fs flash root filesystem and saves me 3-4 hours of manual effort, this kind of implementation detail is outside the scope of my work.  Also, I was glad to be able to set up a good screen resolution.

---

