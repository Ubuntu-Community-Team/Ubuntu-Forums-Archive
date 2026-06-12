---
title: "Ubuntu 11.10 2d any updated guides / explanations?"
date: 2011-11-08
forum: The Cafe
---

### Post by keithpeter on 2011-11-08
Hello All

I was taken to task in another thread for not being logical about Unity so I have decided to dual boot on my main PC for a month or so to see what its all about. The main PC is an Asus Pundit AH1 AMD dual core with Nvidia Geoforce 6150 integrated graphics.

Installation worked really well: Ubuntu detected the Debian Squeeze installation, and I used the 'install alongside' option, allocating about 20Gb to Ubuntu. Restarted. Installed restricted drivers - Jockey detected nvidia card and suggested 173 version of the drivers. No 3d (Mod-e and Mod-w don't do the scaling thing). Ran a test and it appears that Unity 3d is not available for this hardware. 2d performance is sprightly but it always is on this box.

Anyone got any handouts/tutorials/beginner's guides to using Unity as found on 11.10 in its 2d form?

Cheers

```
keith@quiet:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6150/PCI/SSE2/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
```

PS: I'm not a '[unity hater]("http://ubuntuforums.org/showthread.php?t=1872777")' as such, and I wish Canonical every success in becoming a self-sustaining and profitable concern. 

I subscribe to the principle embodied in the quote below: from the comments to an [article in The Register]("http://www.theregister.co.uk/2011/11/08/ubuntu_on_trial/"), which is a scurrilous rag published on a Web site in the UK.

> "Then there are those for whom the shell's main task is to get the fsck out of the way so that they can do some real work."

---

### Post by cariboo on 2011-11-08
Try nvidia-current, I have Natty running on my atom powered media center pc with a pci 6250LE, I usually run XBMC on it, but when I switch to Unity, I get the 3D desktop.

---

### Post by mips on 2011-11-09
> **cariboo907 said:**
> Try nvidia-current...

This ^^

It will install version 280.13

```
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by keithpeter on 2011-11-09
Hello chaps and thanks for the suggestion, but no go

```
keith@quiet:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6150/PCI/SSE2/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
```

Anyone any idea why fairly harmless integrated graphics chipset like Geforce 6150 is blacklisted?

I've added the line 

UNITY_FORCE_START=1

to /etc/environment and am seeing a fairly slow Unity 3d. I'm supposing that was the reason for blacklisting this card in the first place. I actually think Unity 2d is a better experience on this hardware.

---

