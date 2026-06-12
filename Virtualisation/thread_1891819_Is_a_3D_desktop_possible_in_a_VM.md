---
title: "Is a 3D desktop possible in a VM?"
date: 2011-12-06
forum: Virtualisation
---

### Post by BradleyAtkins on 2011-12-06
Hi

I am running Ubuntu 11.10 in VirtualBox on my Win 7 Laptop. Its great but I would like to take advantage of the graphics card on the laptop to enable the 3D desktop in Unity to see what its like.

If  I run: -

```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

Yet I know the graphics card should be able to handle it. This is a brand new i7 Vaio that supports 3D movies and games etc.

When I look at the card from the VM: -

```
/home/brad >lspci | grep VGA
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
/home/brad >sudo lshw -C video
[sudo] password for brad: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=0
       resources: memory:e0000000-e0ffffff
```

According to Windows the graphics card is an NVIDIA GeForce GT 540M running a driver version 8.17.12.6830

Can anyone tell me if its possible to set this up to run the 3D desktop?

Thanks in advance

---

### Post by haqking on 2011-12-06
I run 3D unity in a VM, make sure you running latest VBox or whatever (i think VMware does 3D aswell) and enable 3D acceleration from graphics settings in VM and thats it.

Thats is me anyways

---

### Post by bluexrider on 2011-12-06
however that doesn't take into the account for the VM kernel. try Oracle it may be better

---

### Post by 3Miro on 2011-12-06
You need to get the Virtual Box manual and read the section about enabling 3D acceleration (it isn't too hard). 

By default Virtual Box doesn't give the guest access to the host's 3D graphics card. The feature is considered experimental and it is usually slow and buggy. I have heard of people being happy about Unity 3D in Virtual Box, but it doesn't work for everyone.

---

### Post by haqking on 2011-12-06
here is the manual for virtualbox 3D section

[http://www.virtualbox.org/manual/ch04.html#guestadd-3d](http://www.virtualbox.org/manual/ch04.html#guestadd-3d)

it is pretty straight forward, you tick a box and install the guest additions.

It has been stable for me across guests, but everyone is different.

Good luck

---

### Post by BradleyAtkins on 2011-12-06
Thanks for all the replies. :)

I already have guest editions installed and have enabled 3D acceleration. Maybe the output of the support test was just lying to me then.

I'll give it a go tomorrow and see what happens.

Many thanks to you all....

---

### Post by haqking on 2011-12-06
well my video from in the VM is


 ```
description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=64
       resources: memory:e0000000-e1ffffff

```

my unity support test

```
OpenGL vendor string:   Humper
OpenGL renderer string: Chromium
OpenGL version string:  2.1 Chromium 1.9

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```


I am running latest virtual box 4.1.6 with extension pack and latest additions in the VM.

My display is a Nvidia Quadro NVS 140M 512M driver version 195.36.31

not that it matters too much as in the VM it is virtualised anyways

---

### Post by BradleyAtkins on 2011-12-07
Well downloading the additional drivers seems to have helped greatly: -

```
jockey-gtk
```

Now my unity test is all green: -

```
/home/brad >/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Humper
OpenGL renderer string: Chromium
OpenGL version string:  2.1 Chromium 1.9

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

As an experiment I enabled the cube and rotating cube. It worked but I lost my launch bar. That may be because I updated: - 

```
/etc/gdm/Init/Default
``` 

with these lines to increase the screen size earlier on: -

```
xrandr --newmode "1920x1016_60.00"  161.75  1920 2040 2240 2560  1016 1019 1029 1054 -hsync +vsync
xrandr --addmode VBOX0 1920x1016_60.00
xrandr --output VBOX0 --mode 1920x1016_60.00

```

I'll play around with it some more today and will update this thread with any issues for anyone else looking to do this.

---

