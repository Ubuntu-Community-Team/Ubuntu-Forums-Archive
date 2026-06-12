---
title: "nvidia driver for Jaunty 64-bit"
date: 2009-05-05
forum: System76 Support
---

### Post by nsprangers on 2009-05-05
I performed a clean install of Jaunty on my Serp4 recently, both 32 bit and 64 bit versions on separate partitions.  Under the 32 bit version I was able to very easily enable the nvidia driver for the 8600M GT card I have by going to System > Administration > Hardware Drivers. However, under the 64 bit system nothing is listed under available drivers. Did something go wrong with the install? What exactly does the Hardware Drivers app do? If it just installs a couple of packages I could do that, but I don't know which ones are needed.

---

### Post by thomasaaron on 2009-05-05
It should be the same under 64-bit.

Do you have desktop effects?

If not, run this command...

sudo apt-get install nvidia-glx-180

...and see if it appears in hardware drivers.

---

### Post by farruinn on 2009-05-05
Thank you for the quick reply, Thomas. nvidia-glx-180 was already installed, so I removed that as well as nvidia-180-kernel-source and nvidia-180-libvdpau and tried to re-install nvidia-glx-180.  It complained about not being able to apply a patch at some point, so I uninstalled those, installed patch, and then reinstalled them again. No errors this time, but the driver still doesn't show up in the Hardware Drivers dialog.  I tried to enable desktop effects: it put up a little window saying "searching for drivers" for a bit but then said it couldn't enable desktop effects.

It's been a while since I've edited an xorg.conf, but I'll see if I can specify the binary driver and test that.

---

### Post by thomasaaron on 2009-05-05
If you want to post the xorg.conf here, I'll help you with it.

---

### Post by farruinn on 2009-05-06
I ran nvidia-xconfig which produced a usable xorg.conf, so I'm all set now. Still a little troubling that the option didn't show up in the first place, but it's working now at least.

---

