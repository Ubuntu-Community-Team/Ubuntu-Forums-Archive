---
title: "what version of ubuntu studio is best for use with the freebob driver?"
date: 2010-02-17
forum: Ubuntu Studio
---

### Post by _nate on 2010-02-17
I have tried to use my Presounus Firebox with ubuntu studio 9.10 but I start to receive a ton of xruns after a few seconds.  Would an earlier version of ubuntu studio work better?

---

### Post by AutoStatic on 2010-02-18
Hello _nate, is there a specific reason why you would like to use the freebob driver? The Presonus Firebox should work well with the successor of freebob, the 'firewire' (FFADO) driver.
So no, I don't think an earlier version would work better.

---

### Post by prouddad1 on 2010-02-27
Firebox + pcmcia firewire card (Syba SD-PCB-2F) on T40p thinkpad - latest release of studio

I'm comfortable with ardour now but the frikken internal audio on the thinkpad blows for recording.  

got the firewire cardbus adapter today.....should have the firebox tomorrow - Will all this plug-n-play together or do I need to tweak?    

Any shortcuts or a link would be greatly appreciated.  I read a couple of threads that say a recompile is necessary - I'm kinda new at this, so I'm trying to prepare before I dive in.

Thanks!

---

### Post by trulan on 2010-02-27
You will need to tweak a few things.  You shouldn't need to compile anything though.  Here's a guide for setting up firewire audio:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
Good luck!

---

### Post by mango42 on 2010-02-27
> got the firewire cardbus adapter today.....should have the firebox tomorrow - Will all this plug-n-play together or do I need to tweak?

I'm interested to know which firewire expresscard you are trying, as I'm also attempting firewire on a T43. I hope your system log doesn't report a complaint of being 'dazed and confused'...

As for tweaks, **trulan** has the true word ;-)

---

### Post by prouddad1 on 2010-02-27
> **trulan said:**
> You will need to tweak a few things.  You shouldn't need to compile anything though.  Here's a guide for setting up firewire audio:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
Good luck!


Trulan, thanks for the link.  Everything is looking good so far.  Got to the last step and now I'm not sure what to put in the irq priority list for the pcmcia firewire adpater card.  The instructions say it needs to be listed   Here it is verbatim:  Note: If your firewire card is handled by a controller (for instance, if you are using a PC-Card), you will need to add it to the RTIRQ_NAME_LIST in front of ochi1394 (giving it a higher priority).

I'm not sure what device name gets listed here (I understand, just don't know what its called).  Does the system monitor identify the device name?  I'll go poke around.

UPDATE: I was able to capture with many Xruns, albeit still not in RT mode.  Change the buffer settings and havent been able get the source audio back.  Looks like the hw is working.  Now its user ignorance and config settings.  Not sure which is the greater factor.

---

### Post by trulan on 2010-02-28
Well, if you are using a PC card with a controller, it needs to be prioritized with rtirq, this can make a big difference.  Here's where I got my info on prioritizing irq's:
[http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)
In the example given there, the controller is named 'yenta' and is found by running:
```
cat /proc/interrupts
```So in the example the rtirq_name_list looks like this:
```
RTIRQ_NAME_LIST="rtc yenta ohci1394 ehci_hcd:usb"
```If you are still not sure about this, you could post the output of cat /proc/interrupts.

User ignorance and improper settings often go together, at least when it's me running the computer they do. :P

---

