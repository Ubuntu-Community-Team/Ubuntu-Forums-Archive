---
title: "using a Tascam US-144mkII with linux/ardour"
date: 2009-12-21
forum: Ubuntu Studio
---

### Post by mnkytrk on 2009-12-21
hi all

have asked this question on the ardour forum, and doesn't sound too hopeful, but maybe someone knows something here.

can i use the tascam us-144mk2 with linux/ardour. i've been given links for using a 122, but also seen warnings that mk2 stuff doesn't work

any help most appreciated

cheers for now

P

---

### Post by wbm on 2009-12-21
> **mnkytrk said:**
> hi all

have asked this question on the ardour forum, and doesn't sound too hopeful, but maybe someone knows something here.

can i use the tascam us-144mk2 with linux/ardour. i've been given links for using a 122, but also seen warnings that mk2 stuff doesn't work

any help most appreciated

cheers for now

P

I have the Tascam US-122 and could not get it to work for both in and out in Ubuntu.  I could only record in (showed up as an input device).
In Ubuntu STudio it does work for both in and out.
In both cases I installed from Synaptic usx2yloader (2 different packages)
[http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/)
Try in synaptic a search for Tascam and see if yours shows up.
I'd just install those two usx2yloader, plug in, reboot and see what happens.

---

### Post by mnkytrk on 2009-12-23
thanks for this, will have a go over christmas

cheers

---

### Post by AutoStatic on 2009-12-23
I dare to say with about 95% accuracy that it won't work. It's an USB2 device, so not class compliant. Also, its predecessor didn't work properly either until very recently. If you want a working USB soundcard in Ubuntu you'd best swap the US-144mk2 for another card.

---

### Post by Fezzler on 2010-01-04
AutoStatic -

Buying my first audio interface box for Ubuntu 9.10 Studio Audio Package.

Very confused.  Which ones are known to work?  MBox?  M-Audio?  TASCAM?  All I need is Midi in/out, two powered mic ports and two instrument ports.  Mainly recording guitar, so any controls to get best results appreciated.

---

### Post by AutoStatic on 2010-01-04
Hello Fezzler, then get yourself an Edirol UA-25EX. This is a USB1 class compliant device that works out of the box, has nice pre-amps (also for guitar) and good performance.

---

### Post by matt_fedora on 2010-04-15
It looks like kernel 2.6.30 added support for the advanced mode switch on the back of the Edirol UA-25EX.  Does that make 24bit 96kHz work?  [http://alsa.opensrc.org/index.php/Edirol_UA-25EX#Getting_Advanced_mode_to_work](http://alsa.opensrc.org/index.php/Edirol_UA-25EX#Getting_Advanced_mode_to_work)

---

