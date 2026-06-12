---
title: "USB Boot for Lucid Install on ment1"
date: 2010-12-29
forum: System76 Support
---

### Post by jerickson314 on 2010-12-29
My parents have a Meerkat NetTop (ment1) which I have set up as a server for sharing the printer, NAT for the network in place of a router, etc.  It's currently on 9.10 (which it shipped with), so I'll need to upgrade it so that it continues to receive security updates.

I'm trying to install Lucid (10.04.1) since it's the LTS release, so that I can avoid having to do another upgrade for a while.  I want to do a fresh install to avoid problems.  However, I can't get the USB booting to work.  I've enabled USB boot in the BIOS and selected my flash drive as the first hard drive.  When I do this, I just get a message "Boot Error" at the top of the screen (with nothing else on the screen) when I try to boot.

I've tried with the Server 32-bit and 64-bit images, as well as the Desktop 64-bit image.  All have successfully booted on other machines I have around, but all resulted in a "Boot Error" message on the ment1.  I'm going to try the Alternate 64-bit image next, but I'm doubtful it will work.

Are there any tricks I need to do to get the USB booting working?  I could also do the update within the OS instead, but not being able to reinstall if I have a problem makes me nervous.

---

### Post by jerickson314 on 2010-12-29
For the record, it also doesn't work with 10.04.1 Alternate or 9.10 Desktop (both 64-bit).

---

### Post by isantop on 2010-12-30
Is it a standard Meerkat, or a Meerkat Ion? They do have very different underlying architectures, and while USB boot on the Meerkat has worked fine, there are some tricks to get it working on a Meerkat Ion.

---

### Post by jerickson314 on 2010-12-30
It's just a standard Meerkat.

---

### Post by jerickson314 on 2011-01-13
This issue is still outstanding, although I'm not at my parents' place until March.  I'd still like to figure out how to get the USB boot working so we can get the OS upgraded safely.

---

### Post by isantop on 2011-01-13
Would it be possible to try it on a different USB drive? Also, try making the disk from a different computer. It may be that there's an issue with your installation of the startup disk creator.

---

