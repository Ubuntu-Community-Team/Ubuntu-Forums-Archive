---
title: "Pangoline Performace &amp; Ubuntu 9.04 Beta"
date: 2009-03-28
forum: System76 Support
---

### Post by Lee_Machine on 2009-03-28
So I have been running the Jaunty Beta for about a day now and I'm happy to report that I have no issues so far.

What I have tested is:

Install an run Nvidia 180 driver with no issues.

Resume, and Hibernate work flawlessly.

All hot keys work.

Wireless, and wired networking.
 
Sound.

Correct Screen Resolution.

Plus run, and install all apps.

The only thing that didnt work was having root be ext4. Something to do with GRUB. But with the new work on getting Ubuntu to boot faster with ext3 the boot times are the same as it would have been with ext4.

I will test more, such as sound over HDMI out of the box.

But so far it all works great...and this is without the S76 driver :P

---

### Post by Lee_Machine on 2009-03-28
So far fprint does not work. "Dependency cycle issue" I'm assuming that means it's not in the repos yet?

and I have gotten a couple package updates where dependencies got broken. Nothing sudo dpkg --configure -a wont fix.

So I cannot test the fingerprinter reader.

---

### Post by Talon2 on 2009-03-28
Thanks.  Keep those reports comin'.

---

### Post by Lee_Machine on 2009-03-29
So I have tested both Cheese and Skype, and again they both worked "out of the box" for skype I obviously had to turn the mic on via ALSA mixer. 

I still dont see why we dont have the mic turned on automatically like with Skype on Mac? Anyone know?

So the only thing so far that does not work is the fingerprint reader. Not a big deal since it has no use on Ubuntu

Anyways so far Jaunty is a great release!

This is all still without the S76 dirver on a Pangoline Performace panp4n.

Looks like the driver will be needed to get fprint to work.

---

### Post by Lee_Machine on 2009-03-29
So far the things that do not work is fprint, and sound via HDMI. Since the release of ALSA 1.0.18 last November this is supposed to work on nvidia cards, and I did get it working on 8.10. 

But no dice with 9.04 beta.

---

