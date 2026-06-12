---
title: "usb port not working new gazelle professional"
date: 2011-07-22
forum: System76 Support
---

### Post by nerdy_kid on 2011-07-22
Hi, I just bought a brand new gazelle professional which is working great, but for some reason the first USB 3 port isn't behaving.  I tried both usb3 and usb2 harddrives, which both failed to connect.  Sometimes
"hub 3-0:1.0: unable to enumerate USB device on port 4" is shown in the syslog, but most times nothing shows.  I tried a bluetooth adapter, and it seemed to work fine though.  I tried rebooting the system to no avail.  Someone tell me this is software, cause if I have to send this back in I will kill something.

---

### Post by nerdy_kid on 2011-07-22
ok now a usb2 drive is working, but my usb3 drive (which also is a usb2, not sure if that is typical or not) still throws the "unable to enumerate" error.  Do I need to update the BIOS?

---

### Post by isantop on 2011-07-25
Does the USB 2 drive work in one of the Non-USB3 ports?

---

### Post by nerdy_kid on 2011-07-25
> **isantop said:**
> Does the USB 2 drive work in one of the Non-USB3 ports?

Yes, and both the USB 2 ports work fine -- in fact, all of the USB ports work as expected (including the second USB 3 port) except for this port (USB 3 port closest to the back of the laptop).

So, in review (sorry if I am sounding confusing):

Both USB2 ports work as expected.

The USB3 port furthest to the back of the laptop does not work as USB3, however USB2 devices currently seem to work just fine.  However, The USB3 drive that I have does not work at all with this port, even though the drive is backwards compatible with USB2.  
I was having a little trouble connecting any USB storage device at all to this port (USB wireless cards and bluetooth both worked fine, strangely enough), but now USB2 drives seem to work fine.



The second USB3 port works as expected, I get 80 megabytes a second copying from my external hard drive (not a SSD).

---

### Post by nerdy_kid on 2011-07-29
Also, I just noticed that plugging my USB3 drive into the working USB3 port causes all other USB ports on that side of the laptop (left side) to stop working at all.

---

### Post by nerdy_kid on 2011-08-01
bump....

---

### Post by isantop on 2011-08-01
So if you get the USB3 port working and plug something into it, even the USB2 port stops working? You might try running the drive off of a different cable, since that sounds like a possible short.

---

### Post by nerdy_kid on 2011-08-01
> **isantop said:**
> So if you get the USB3 port working and plug something into it, even the USB2 port stops working? You might try running the drive off of a different cable, since that sounds like a possible short.

Unfortunately I only have one cable for this drive, and I don't have any other USB3 devices.  However, if it was a short in the cable, wouldn't USB2 be affected as well?  
Do you have any idea where this problem could be coming from -- software/hardware?  If it is software I can live until the next Linux kernel, but if it is hardware I am going to need an under warranty repair...

---

### Post by isantop on 2011-08-02
USB3 uses four extra connectors to boost transfer speeds. The short could occur between two of the SuperSpeed connectors and not affect USB2 use.

---

### Post by nerdy_kid on 2011-08-02
ok, I don't think it is a short in the cable, simply because if it was a short in the cable, I would not be able to consistently reproduce the exact same behavior every time.  Perhaps it is a short/loose connection in the USB ports themselves though, in which case I'll be asking for a replacement...

Does it void my warranty if I take the laptop completely apart myself and inspect (and possibly repair) the soldering?

---

### Post by isantop on 2011-08-04
Repairing the laptop yourself does void the warranty. 

Can you try the drive on the computer while running from a LiveCD? The USB 3 ports work out of the box in Ubuntu, and this should allow you to rule out a hardware or software issue.

---

### Post by nerdy_kid on 2011-08-05
> **isantop said:**
> Repairing the laptop yourself does void the warranty. 

Can you try the drive on the computer while running from a LiveCD? The USB 3 ports work out of the box in Ubuntu, and this should allow you to rule out a hardware or software issue.

The same symptoms occur under the LiveCD.

---

