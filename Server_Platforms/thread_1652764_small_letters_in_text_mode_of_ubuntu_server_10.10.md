---
title: "small letters in text mode of ubuntu server 10.10"
date: 2010-12-25
forum: Server Platforms
---

### Post by sgoran on 2010-12-25
I am new user of ubuntu server. I installed it on very old machine P3 1200Mhz and it works ok but I have problem with text mode because I have 75x132 aprocs. text on screen and I don't see what I type or system replay. Is there simple way to change to 25x80 or something with greater letters. I don't have GDI.

Someone sad to me to do:
sudo dpkg-reconfigure console-setup

and it's does the job but when I restart system it's gone.

---

### Post by sgoran on 2010-12-28
I find answer to my question on this forum but it has error.

Brandon Williams in

Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Development & Programming > Ubuntu Forum Archives > Lucid Lynx Testing and Discussion (CLOSED)

from March 24th, 2010

> 
Now my /etc/default/grub has these settings:
```

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep

```

And I have a new file called /etc/modprobe.d/radeon.conf:
```

options radeon modeset=0

```


I try this and it help me but resolution was 640x480 and not 1024x768. He made mistake in name of file. Name of the file need to be
/etc/modprobe.d/radeon-kms.conf
and then it work for me.

---

### Post by sgoran on 2010-12-29
I test this solution with different resolutions and it not work. Only right thing is that
/etc/modprobe.d/radeon-kms.conf
with
```

options radeon modeset=0

```
will stop using maximal resolution for console text mode. It will exclude use of radeon framebuffer-s and use default.

---

### Post by Eric106 on 2011-01-10
I'll add on here because my situation is very similar to the original  poster's and this thread ranks high on a Google search for "ubuntu  server 10.10 console resolution."  I hope this information will be useful to someone else.

I have a Dell PowerEdge 2800 server with a DRAC4 on which I recently installed  Ubuntu 10.10 Server.  I was having a similar problem with the  console resolution.  In my case the DRAC4 card would not recognize/pass the  high resolution video mode to which the console defaulted.  This left me  blind.  The GRUB2 menu was visible but when the radeon module would  load during the boot process it would switch to the highest resolution  and I would loose all video via the DRAC.

For those not familiar, a DRAC is a Dell Remote Access Card.  It can be  thought of as either a hardware based VNC server that lets you connect before the OS  has even loaded and interact with the BIOS during boot or, you could think  of it as a KVM switch that works over the network.  One of the other  features is the ability to remotely mount an ISO image as a virtual  CD-ROM and then, with the boot order configured appropriately in BIOS,  the system will boot from this image.  With this you can completely  reinstall the OS on a system remotely.  

This all works great during the install and during the GRUB menu but  then when the kernel loads the radeon module it switches to the highest  resolution and I loose video.  Keyboard input is still sent but the  DRAC cannot sync video at the new resolution.  I had to connect a monitor to the system to see what I was doing.  This may not always be an option though if the server is geographically remote.

People have suggested using ssh to connect once the OS is installed.   This may be a good choice in many cases but is not always a viable  option.  The DRAC has its own network interface and may be on a  different physical network, VLAN, VPN, etc. from the system itself.  There may be other  security reasons why an ssh login is not possible or is not possible at  this early stage of the install.  

Most all of the suggested solutions I have come across refer to making changes in  /etc/default/grub or other files which would first require you to be able to see the  console to log in and make the changes.  In my case it is not just an  inconvenience to have to read the tiny font, I cannot see anything.  I  needed a solution that could be applied as a command line option to the  Linux kernel since this is all I have to work with in GRUB before Linux  boots.

My initial attempts to pass a vga= option or a video= option to the  kernel would only last until the radeon module was loaded and then it  would set the display to max resolution.  Blacklisting the radeon module  solved the problem but you have to be logged in to do this so it is not  a solution for me.  I was looking for a way to keep a module from  loading as a kernel command line option.  I never found the correct way  to do this but I did find that if you pass the radeon module a parameter  that it does not understand it will fail to load.  Thus if you add  radeon.anythingyouwat=something or just radeon.x=1 to the kernel command  line the radeon module will not load and your vga= parameter will be  honored.  

There are several kernel module related to the radeon module that are  also not needed and can be removed after boot.  These are the drm, ttm,  drm_kms_helper, and i2c_algo_bit.  If you add drm.x=1 the the kernel  command line it will keep the drm module from loading and also the ttm  and drm_kms_helper modules since they depend on the drm module.  The  only other one not needed then is the i2c_algo_bit module.

Personally, I think it is bad form for a server OS, which will usually  be headless anyway, to install all these modules.  I guess they are so  common now that nobody thought they should be pulled out of the server  version.  I think they should have been left out; make the default  install as simple, fast, & low memory as possible.  If you want to  run X on your server you can install the advanced video drivers with the  rest of the X system.  But this is all just my opinion.

Another solution is pass the radeon.modeset=0 option to the kernel.   This parameter to the radeon module will keep it from changing modes.   You can then pas a vga= option to set the resolution you desire.  You  can use sudo hwinfo --framebuffer to find the available modes for your  video hardware.

I now know that if I need to I can do a complete reinstall remotely.   After installing the OS at the first GRUB boot menu I can hit 'e' to  edit the kernel command line and add the required options.  For me these  are radeon.modeset=0 vga=791 (highest VESA mode mine will support).   Then once I have logged in I can edit /etc/default/grub to add the  options to the GRUB_CMDLINE_LINUX_DEFAULT line.  Then run sudo  update-grub to make the changes persistent.  

I suppose you could also just delete the relevant module from the system which would also obviously keep them from loading.

I hope this helps someone else.

-Eric

---

