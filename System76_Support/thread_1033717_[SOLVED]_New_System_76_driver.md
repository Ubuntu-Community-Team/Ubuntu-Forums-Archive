---
title: "[SOLVED] New System 76 driver"
date: 2009-01-07
forum: System76 Support
---

### Post by ewg on 2009-01-07
Sysyem 76 Sable, 32 bit

I just noticed that System 76 driver 2.3 is available. I used to get the new drives from the update manager but that does not happen any more. I do have system 76 box checked in software sources, 3rd party software. 

I did download the latest driver. Is it just a matter of running the deb package and following any directions/

Is there a way to know when new drivers are released?

Thanks,

---

### Post by thomasaaron on 2009-01-07
I think they disabled automatic update notifications for the driver. I'm not sure why, but I'll look into it.

However, you can just install the .deb and then go to System > Admin > Sys76 Driver > Install Tab > Install Button, and you'll be good to go.

For right now, you just have to keep an eye out for new drivers.

Sorry for the inconvenience.

---

### Post by Lee_Machine on 2009-01-08
what was fixed/added in 2.3? The 2.3 driver changelog is not on the knowlege76 website yet.

---

### Post by thomasaaron on 2009-01-08
Version 2.3.0

   1. Reverse Direct Rendering w/ Suspend on fix daru3 (2.2.9) - fixed in Ubuntu
   2. Add quirks=2 to uvcvideo load on gazu3 (fixes webcam) 


...updated the wiki

---

### Post by Lee_Machine on 2009-01-08
Thanks,

I was just mostly wondering about sound with the HDMI out on the panp4. 
What's the word with the R&D guys? Just gonna wait till Jaunty?

---

### Post by crichell on 2009-01-08
> I was just mostly wondering about sound with the HDMI out on the panp4.
What's the word with the R&D guys? Just gonna wait till Jaunty?

As of now we are going to wait for Jaunty. Bringing down a new Alsa always tends to be messy. I think the majority of customers aren't using the functionality (Audio over HDMI). A script that easily installs the new Alsa may be a good interim solution.

---

### Post by asmiller-ke6seh on 2009-01-08
We're still waiting for Webcam in the System 76 driver for Serp1 and Serp2. Any news, yet?

---

### Post by thomasaaron on 2009-01-08
I'm sorry, but I've just not been able to get the webcam code for the SerP1 and SerP2 to compile on our shop computer. This makes me worry that, if we plug it into the System76 driver, it will not work on a lot of computers that are out there.

There is some new UVC code out there, though. Maybe it will compile better. I'll give it a try.

---

### Post by Lee_Machine on 2009-01-09
> **crichell said:**
> As of now we are going to wait for Jaunty. Bringing down a new Alsa always tends to be messy. I think the majority of customers aren't using the functionality (Audio over HDMI). A script that easily installs the new Alsa may be a good interim solution.

Thanks, I'll have to burn a live-CD of Jaunty Alpha 1 and see if it works out of the box.

---

### Post by tcrapper on 2009-01-11
> **crichell said:**
> As of now we are going to wait for Jaunty. Bringing down a new Alsa always tends to be messy. I think the majority of customers aren't using the functionality (Audio over HDMI). A script that easily installs the new Alsa may be a good interim solution.

I haven't gotten my laptop yet. But will [this]("http://ubuntuforums.org/showthread.php?t=962695") script work to get HDMI working?

---

### Post by thomasaaron on 2009-01-12
Judging from the posts following the script instructions, it's risky. It may work, but you're liable to break something else.

---

### Post by thomasaaron on 2009-01-12
Possibly. But judging be the posts in that thread, you're liable to hose something else in the process.

---

