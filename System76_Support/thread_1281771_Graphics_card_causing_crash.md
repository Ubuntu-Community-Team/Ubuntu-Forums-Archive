---
title: "Graphics card causing crash"
date: 2009-10-03
forum: System76 Support
---

### Post by japhyr on 2009-10-03
Hello,

I have been quite happy to be a System76 customer.  I love my computer, and the customer service has been excellent.  That said, the computer has been crashing, and I think I have figured out why.  I spoke with Tom Aaron yesterday, but I wanted to post some results here in case anyone can suggest further steps before Monday.

The computer has been hard crashing, not just freezing.  I tested the graphics card by starting instances of glxgears, and watching the gpu core temp in nvidia-settings.  After being off for about 4 hours, the gpu core temp is listed at 60.  My house is 60 degrees F, so this does not seem accurate, assuming the reading is supposed to be in C.  At idle, the core quickly settles on about 80.

I started 3 instances of glxgears, and the temperature rose steadily to 110 and then the computer shut itself off instantly, all in less than 5 minutes.  I let it rest 5 minutes, then ran the test again with 5 instances of glxgears.  It ran ~10 minutes, then crashed with a last reading of 110.  This morning I ran 5 instances for about ten minutes, which ran steady at 105-108, just shy of crashing.  I started two more instances of glxgears, and it crossed 110 and crashed in less than a minute.

Graphics card and driver:
lspci | grep VGA:  nVidia Corporation Device 06ec (rev a1)
from nvidia x server settings:  driver version 180.44
Also, I have the WSXGA screen if that matters.

Does anyone have any idea if there is something I can do to address this, or if it's a straight hardware issue?  The laptop gets warm, but nowhere as hot as other laptops I have used.  I am wondering if the sensor is not calibrated correctly, or if a shutoff setting is set too low.  Is there any simple solution to try like reinstalling a driver?  I know I will hear from S76 support shortly into the week, but if anyone has any ideas to play with over the weekend I'd love to hear them.

---

### Post by jdb on 2009-10-03
> **japhyr said:**
> Hello,

I have been quite happy to be a System76 customer.  I love my computer, and the customer service has been excellent.  That said, the computer has been crashing, and I think I have figured out why.  I spoke with Tom Aaron yesterday, but I wanted to post some results here in case anyone can suggest further steps before Monday.

The computer has been hard crashing, not just freezing.  I tested the graphics card by starting instances of glxgears, and watching the gpu core temp in nvidia-settings.  After being off for about 4 hours, the gpu core temp is listed at 60.  My house is 60 degrees F, so this does not seem accurate, assuming the reading is supposed to be in C.  At idle, the core quickly settles on about 80.

I started 3 instances of glxgears, and the temperature rose steadily to 110 and then the computer shut itself off instantly, all in less than 5 minutes.  I let it rest 5 minutes, then ran the test again with 5 instances of glxgears.  It ran ~10 minutes, then crashed with a last reading of 110.  This morning I ran 5 instances for about ten minutes, which ran steady at 105-108, just shy of crashing.  I started two more instances of glxgears, and it crossed 110 and crashed in less than a minute.

Graphics card and driver:
lspci | grep VGA:  nVidia Corporation Device 06ec (rev a1)
from nvidia x server settings:  driver version 180.44
Also, I have the WSXGA screen if that matters.

Does anyone have any idea if there is something I can do to address this, or if it's a straight hardware issue?  The laptop gets warm, but nowhere as hot as other laptops I have used.  I am wondering if the sensor is not calibrated correctly, or if a shutoff setting is set too low.  Is there any simple solution to try like reinstalling a driver?  I know I will hear from S76 support shortly into the week, but if anyone has any ideas to play with over the weekend I'd love to hear them.

100 C is where they usually shut down so it's doing what it's supposed to.

It's either really getting that hot or the sensor is reading wrong.

If the fan isn't running or is plugged up with a dust bunny it could be getting that hot.
If no air is circulating it could be really hot inside the case but not feel hot on the outside.

jdb

---

### Post by japhyr on 2009-10-03
The fan is running, and it's new enough there really should not be a dust issue.  I opened it last night to reseat the RAM and look at the HD, and there's no dust in there.

Is there a way to calibrate the nvidia-settings temperature sensor?  The fact that it reads 60C immediately upon startup has me suspicious of the calibration.

---

### Post by jdb on 2009-10-03
> **japhyr said:**
> The fan is running, and it's new enough there really should not be a dust issue.  I opened it last night to reseat the RAM and look at the HD, and there's no dust in there.

Is there a way to calibrate the nvidia-settings temperature sensor?  The fact that it reads 60C immediately upon startup has me suspicious of the calibration.

Yeah, 60 C when it's first turned on sounds fishy.
I don't know of any way to calibrate it.

jdb

---

### Post by jdmelton on 2009-10-04
Make sure your heat sinks have good contact. Air flow is not enough if the heat sinks are not in good contact.

Based on my experience with industrial systems, there is probably a combination of firmware and hardware that senses temperature. Several systems that I know of use RTD type detectors. Since resistance varies with temperature, if the resistance value of the RTD is not within specification, the interpreted temperature will not be correct. Or, if the firmware table of resistance values versus temperature is wrong, then a wrong value is reported.

From your posts, it seems that you know what reported value shuts your system down. Since your system does not seem to crash below that point and crashes seem to be repeatable, the problem does seem to be temperature related.

I would not assume that the temperature is reported in C. Many systems have BIOS settings that allow selection between C or F.

All of the systems that I have put a probe on have had surface mounted chips for temperature control. Some have fixed firmware. So, it can be very hard to calibrate a system.

If your heat sinks are in good contact, your airways are not clogged, your BIOS is not set to F (so temperature reporting is bad), and assuming your crashes are temperature related, I recommend that you return the system or at least the card. I can be wrong, yet I think it will be very difficult to repair a temperature related problem.

---

### Post by japhyr on 2009-10-04
Thank you for your very informative response, jdmelton.  I look forward to hearing from S76 support, and I'll post the resolution to all of this.

---

### Post by marshmallow1304 on 2009-10-04
Mine reports 56 C on startup, and I've had no problems with crashes, even when running Savage 2 for a couple hours.

---

### Post by japhyr on 2009-10-05
How hot does yours get?

I just set my computer in front of a fan for a couple hours, off, to see what it would read on startup at room temperature.  It started at 50C, in an 18C home.

---

### Post by marshmallow1304 on 2009-10-05
I don't really know, as I haven't had reason to check.  It does feel pretty hot on the left of the bottom though.  I'll check the next time I do something graphics intensive.

EDIT:
I ran some tests with glxgears.  I started 5 instances and waited 5 minutes, then started another 5.  I couldn't get the temp to go above 72 C.  It even dropped back into the 60s a couple times.

---

### Post by japhyr on 2009-10-05
That's interesting, because my temperature shoots up to 110 pretty quickly with that kind of load.  The only difference I see between my panp5 specs and yours is that my cpu is about 2.1 GHz, and I have a wsxga screen.  It's going to be sad to have to send this computer back, but I'm guessing that's where this is all headed.

---

### Post by thomasaaron on 2009-10-05
japhyr,

That's pretty much what I was expecting to see when I suggested running glxgears.

Your graphics card is overheating. It's not really a matter of calibrating anything. I've seen this once or twice before. For warranty purposes, it's better if you don't do anything to it. I'll explain via email.

Please contact me via email (if you haven't already done so) and we'll get it fixed.

---

### Post by japhyr on 2009-10-21
I finally got my PanP5 back today, and I am very happy to see the overheating issue resolved.  Thank you to everyone who helped, and to S76 staff who were so easy to work with the whole way.

---

