---
title: "VirtualBox Mysteriously Broken"
date: 2009-06-18
forum: Virtualisation
---

### Post by EoRaptor013 on 2009-06-18
I've been running vBox 2.2.4 successfully on my laptop ever since upgrading to the Jackalope. During this time, I connected to the intertubes using wlan0, and vBox was set to bridge to wlan0. Last week, I connected the laptop to a cable and used eth0. I can't remember if I used vBox during the time I was connected to the cable. Later, I moved back into my office, with the wlan0 only connection, fired up vBox and got this:

[COLOR="Red"]Failed to open/create the internal network 'HostInterfaceNetworking-wlan0' (VERR_SUPDRV_COMPONENT_NOT_FOUND).
Unknown error creating VM (VERR_SUPDRV_COMPONENT_NOT_FOUND).[/COLOR]

So, now I can't start a VirtualBox WinXP VM. Laptop is a Dell E1705. 

Anyone have any ideas?

Thanks,

EoRaptor

---

### Post by EoRaptor013 on 2009-06-20
Well, learn something new every day! 

I recompiled the vbox driver module using 

sudo /etc/init.d/vboxdrv setup

restarted the Sun VirtualBox GUI, and all is well. Not sure why; I know I've run vbox since I upgraded to Jaunty. It may be one of those great mysteries of the universe.

Thanks. 

EoRaptor

---

### Post by howefield on 2009-06-20
> **EoRaptor013 said:**
> It may be one of those great mysteries of the universe.

Most likely not though., 

Could be to do with the kernel updating to 2.6.28.13 ?

---

