---
title: "Boot to Ubuntu on Hard Drive via USB drive"
date: 2011-10-15
forum: The Cafe
---

### Post by fredcm3 on 2011-10-15
It's been suggested that I could get OS boot steering by plugging in a USB boot drive.

I have Ubuntu 11.10 installed on a hard drive.
GRUB2 (on the hard drive) directs the boot to another OS as default.

I have an Ubuntu 11.10 USB boot drive.
Normally it boots to Ubuntu on the USB drive as exepcted.

I will set up the USB drive to have boot priority over the hard drive.

So, I want to change the USB boot drive contents so that when it is plugged in, the default OS willl be the Ubuntu install on the hard drive.

The startupmanager doesn't seem to run when I've booted onto the USB drive......

What's the secret?

---

### Post by Luffield on 2011-10-16
I don't think you need Ubuntu on the USB drive. You only need Grub on it, and you need to configure it so that it boots an OS from your hard drive. I never tried it myself, but I don't think it's very difficult.

---

### Post by fredcm3 on 2011-10-16
It may well be that Ubuntu isn't needed on the USB drive.  But, getting it there was/is simple enough.
I'm not sure how to start just putting GRUB on it and don't know that it matters, eh?

I'm still stuck with getting what I need on that drive.

---

