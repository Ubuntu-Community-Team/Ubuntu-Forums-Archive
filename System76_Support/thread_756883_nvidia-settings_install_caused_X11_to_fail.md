---
title: "nvidia-settings install caused X11 to fail"
date: 2008-04-16
forum: System76 Support
---

### Post by toddpedlar on 2008-04-16
I was trying to get the external video (VGA) connection on my Serval Performance to display, and one of the things suggested was to use the nvidia-settings monster to set up the external monitor.

So, I calmly checked off nvidia-settings in synaptic package manager, and then installed - it uninstalled nvidia-glx, which I didn't think much of, and then after the reinstall I had lost x11.  

Tried rebooting, nothing - no x11.  

I'm now stuck with a commandline machine with no Xserver.

I have tried sudo apt-get install nvidia-glx to get nvidia-glx back, but the ethernet port isn't set up (at the point at which the machine sits leaving me on the commandline) so I'm trying to get networking working again from the commandline.

Is this what I should be wasting my time doing?  Is there another method?  

I'm stuck - this is really a pain.  Please suggest something I can do.
Rebooting from the Ubuntu CD is useless (I get internet, but installing nvidia-glx from there did nothing when I rebooted again without the CD)

Help? :(

---

### Post by toddpedlar on 2008-04-16
> **toddpedlar said:**
> I was trying to get the external video (VGA) connection on my Serval Performance to display, and one of the things suggested was to use the nvidia-settings monster to set up the external monitor.

So, I calmly checked off nvidia-settings in synaptic package manager, and then installed - it uninstalled nvidia-glx, which I didn't think much of, and then after the reinstall I had lost x11.  

Tried rebooting, nothing - no x11.  

I'm now stuck with a commandline machine with no Xserver.

I have tried sudo apt-get install nvidia-glx to get nvidia-glx back, but the ethernet port isn't set up (at the point at which the machine sits leaving me on the commandline) so I'm trying to get networking working again from the commandline.

Is this what I should be wasting my time doing?  Is there another method?  

I'm stuck - this is really a pain.  Please suggest something I can do.
Rebooting from the Ubuntu CD is useless (I get internet, but installing nvidia-glx from there did nothing when I rebooted again without the CD)

Help? :(

Bump!

Is anyone here?

---

### Post by thomasaaron on 2008-04-16
Try this:

sudo ifdown eth0
sudo ifup eth0 #Hopefully this will bring up a WIRED connection

sudo apt-get install nvidia-glx-new
sudo nvidia-glx-config enable
sudo dpkg-reconfigure xserver-xorg
 *Choose ALL defaults, except...
 *Choose nVidia for the driver (not nv)
 *Choose all available resolutions (space bar selects, arrow key moves down)
 *Choose "Advanced" and continue to select defaults
sudo reboot now

---

### Post by hoist1138 on 2008-04-16
hey there,
I'm also having a hard time booting at all with my GeForce 4 Ti-4600 nvidia card, It give me the "cant stat X server, no such file..." and tells me my display is not properly configured...

Does anyone know a good link for resolving display issues like this, I know this is the Biggest issue for Ubuntu users.....

---

### Post by thomasaaron on 2008-04-16
Did you try the above instructions (minus the first two)?
If so, what happened?

---

