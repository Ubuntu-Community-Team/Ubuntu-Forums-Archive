---
title: "Video tearing and/or choppy playback - only on HDMI TV"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by DavidSommen on 2012-04-25
I am running Precise Pangolin up-to-date on my system. My system specs are:

MSI 790GX G-65 motherboard
AMD Phenom II X3 720 Processor
4GB of DDR3 RAM
ATI RS780D [Radeon HD 3300] onboard video.

I have a 17" computer monitor via VGA and a television (Philips 32") attached via a HDMI cable.

If I watch fullscreen video (VLC) on my 'main' monitor, the video playback is smooth and clean, as it should be. However, if I watch the video on the TV, the video tears lightly to moderately. If I use unity-2D, the video tearing is even worse (heavy tearing).

I have switched the output (Default, X11, XVideo, OpenGL GLX) on VLC to no avail.
I have come close to a workaround by enabling 'Force full screen redraws (buffer swap) on repaint' in CCSM -> Workarounds. This gets rid of the video tearing, but makes the video playback choppy (some frames are dropped and the overall playback is not smooth anymore), however my CPU doesn't seem to be overstressed. 

Combined with this bug ([https://bugs.launchpad.net/unity/+bug/954446](https://bugs.launchpad.net/unity/+bug/954446)) this makes watching video on my TV a rather unpleasant experience... I have watched 'System monitor' and cpu use is around 10-20% while playing back the video. Seems acceptable to me.

The odd thing is, on my main monitor, the problem of tearing/choppiness does not occur at all, as far as I can tell.

So... Is this a driver issue? A refresh rate issue? Obviously the resolution on my TV is different from the one on my monitor (1366*768 on tv vs 1280*1024 on the monitor), but with my system, I think that shouldn't be a problem...

any ideas?

---

### Post by 23dornot23d on 2012-04-25
Have you thought about a dedicated graphics card rather than using the onboard - as that should quickly solve the problems ..... if you can find one that suits your motherboard and price range.


[https://www.google.com/search?client=ubuntu&channel=fs&q=HD+3300+choppy+&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=HD+3300+choppy+&ie=utf-8&oe=utf-8)

---

### Post by DavidSommen on 2012-04-25
No, I haven't thought about that, I think for normal video playback a onboard graphics card should be enough, shouldn't it? :confused:

And as the video playback is perfect on monitor #1, I think this has more to do with the software part of the system than a graphics card that's too slow... might be wrong.

---

### Post by Grenage on 2012-04-25
I used onboard ATI over HDMI on my media centre, and it was a bit dicey to say the least. In the end, I got it working ok with XBMC and refresh synchronising, but it was never fantastic.  After a year I added an Nvidia card, and no tweaking was required (with the proprietary driver).


While the hardware is technically more than capable of handling the output, the awful drivers and questionable software driving it will hamper your efforts.

---

### Post by 23dornot23d on 2012-04-25
Try this in a terminal window ....

[COLOR=Blue]**date && lsb_release -sd || cat  /etc/*release &&  uname     -s -r && unity --version  &&     /usr/lib/nux/unity_support_test -p && dpkg -s  mesa-utils**[/COLOR]

This is what mine returns back as an example .... 
( will give some more information to work with - see how it is set up at the moment - I use a 32 inch TV and no problems
but use a Nvidia 9300 M GS card as below ... )

> 
[EMAIL="keith@keith-Aspire-7730ZG:%7E/.config"]keith@keith-Aspire-7730ZG:~/.config[/EMAIL]$ [COLOR=Blue]**date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s ****mesa-utils**[/COLOR]
Wed Apr 25 11:53:29 CEST 2012
Ubuntu 12.04 LTS
Linux 3.2.0-23-generic-pae
unity 5.10.0
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV98
OpenGL version string:  2.1 Mesa 8.0.2

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
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: [http://mesa3d.sourceforge.net/](http://mesa3d.sourceforge.net/)

[COLOR=Blue][B]lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'

[/B][/COLOR]> 
[EMAIL="keith@keith-Aspire-7730ZG:%7E/.config"]keith@keith-Aspire-7730ZG:~/.config[/EMAIL]$ lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1) (prog-if 00 [VGA controller])
        Kernel driver in use: nouveau
        Kernel modules: nouveau, nvidiafb



[https://www.google.com/search?client=ubuntu&channel=fs&q=XBMC+and+refresh+synchronising&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=XBMC+and+refresh+synchronising&ie=utf-8&oe=utf-8)

---

### Post by DavidSommen on 2012-04-25
Thanks for your replies. Here is the output:

```

sommen@sommen:~$ date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Wed Apr 25 12:15:28 CEST 2012
Ubuntu 12.04 LTS
Linux 3.2.0-23-generic
unity 5.10.0
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS780
OpenGL version string:  2.1 Mesa 8.0.2

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
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 148
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

```

```

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780D [Radeon HD 3300] (prog-if 00 [VGA controller])
	Kernel driver in use: radeon
	Kernel modules: radeon

```

---

### Post by 23dornot23d on 2012-04-25
Well everything looks to be set up alright ..... and if the card is capable of running 
1280 x 1024 ok then its got to be the drivers - but I do not know what alternatives exist for
your card ...... on 12.04     ok just seen this too [http://ubuntuforums.org/showthread.php?t=1964321](http://ubuntuforums.org/showthread.php?t=1964321)

[https://www.google.com/search?client=ubuntu&channel=fs&q=drivers&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=p70&channel=fs&sclient=psy-ab&q=drivers+Radeon+HD+3300+linux&oq=drivers+Radeon+HD+3300+linux&aq=f&aqi=&aql=&gs_nf=1&gs_l=serp.3...1871.11988.0.12269.14.12.2.0.0.0.154.1491.1j11.17.0.gQDS_9WisF0&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=fb02d6c488e49837&biw=1158&bih=610](https://www.google.com/search?client=ubuntu&channel=fs&q=drivers&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=p70&channel=fs&sclient=psy-ab&q=drivers+Radeon+HD+3300+linux&oq=drivers+Radeon+HD+3300+linux&aq=f&aqi=&aql=&gs_nf=1&gs_l=serp.3...1871.11988.0.12269.14.12.2.0.0.0.154.1491.1j11.17.0.gQDS_9WisF0&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=fb02d6c488e49837&biw=1158&bih=610)

[https://www.google.com/search?client=ubuntu&channel=fs&q=drivers&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=moL&channel=fs&sclient=psy-ab&q=drivers+Radeon+HD+3300+linux+2012&oq=drivers+Radeon+HD+3300+linux+2012&aq=f&aqi=&aql=&gs_nf=1&gs_l=serp.3...60503.81157.0.81579.17.11.5.0.0.0.184.1352.1j10.22.0.LHWSi9DdZpE&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=fb02d6c488e49837&biw=1158&bih=610](https://www.google.com/search?client=ubuntu&channel=fs&q=drivers&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=moL&channel=fs&sclient=psy-ab&q=drivers+Radeon+HD+3300+linux+2012&oq=drivers+Radeon+HD+3300+linux+2012&aq=f&aqi=&aql=&gs_nf=1&gs_l=serp.3...60503.81157.0.81579.17.11.5.0.0.0.184.1352.1j10.22.0.LHWSi9DdZpE&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=fb02d6c488e49837&biw=1158&bih=610)

Keeps coming back to the same thing .... choppy playback ..... 

[https://www.google.com/search?client=ubuntu&channel=fs&q=drivers&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=drivers+Radeon+HD+3300+linux+x-swat&oq=drivers+Radeon+HD+3300+linux+x-swat&aq=f&aqi=&aql=&gs_nf=1&gs_l=serp.3...13516.13516.2.14432.1.1.0.0.0.0.114.114.0j1.1.0.1dbsvpvTO8Q&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=fb02d6c488e49837&biw=1158&bih=610](https://www.google.com/search?client=ubuntu&channel=fs&q=drivers&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=drivers+Radeon+HD+3300+linux+x-swat&oq=drivers+Radeon+HD+3300+linux+x-swat&aq=f&aqi=&aql=&gs_nf=1&gs_l=serp.3...13516.13516.2.14432.1.1.0.0.0.0.114.114.0j1.1.0.1dbsvpvTO8Q&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=fb02d6c488e49837&biw=1158&bih=610)

if it was me - would be looking for a new graphics card to
slot into the motherboard .... PCI x 16 ......

---

### Post by DavidSommen on 2012-04-25
Installing fglrx doesn't seem to work for me, it messes up my system. The opensource driver has always done everything I wanted from my computer, apart from this (I recently attached the tv, so I don't know if this is a regression since previous ubuntu versions). 

Buying a new card is not really on my list now, I don't want to spend a lot of money just to watch a movie, I'm not a gamer or anything. And in my humble opinion, this is a software-based bug...

---

### Post by Grenage on 2012-04-25
I would heartily recommend the proprietary AMD driver; while some will say otherwise, I've experienced nothing but an uphill battle with the open driver.

If you elaborate on the issues you faced, we can perhaps work on those.

---

### Post by 23dornot23d on 2012-04-25
Just a thought - have you tried different players to watch the movies ....

I use Miro ..... Dragon .... Mplayer .... see if there is any difference ... in the way they buffer the video .... worth a try ..... although they are all going to use the same graphics driver ..... as well as vlc.

---

### Post by DavidSommen on 2012-04-25
OK, you are probably right :)

I just installed the fglrx driver via system settings -> Additional drivers. After reboot, the screen is messed up as if there two screens over each other, the top one around 300 pixels lower than the bottom one. I was however able to fix this (I never tried before, I always deleted the driver after seeing this) by going to 'Displays'. There I found that my TV (via hdmi) was no longer detected anymore. Instead it shows, apart from my BenQ 17" monitor, another screen named 'Laptop', although I do not have a laptop screen of any kind connected to this computer. After disabling the 'laptop' screen, the display on my normal monitor works fine.

However: it does not detect my TV anymore! So this is my main problem with the proprietary driver now... :)

---

### Post by DavidSommen on 2012-04-25
> **23dornot23d said:**
> Just a thought - have you tried different players to watch the movies ....

I use Miro ..... Dragon .... Mplayer .... see if there is any difference ... in the way they buffer the video .... worth a try ..... although they are all going to use the same graphics driver ..... as well as vlc.

I have tried smplayer briefly, and it seemed to have the same problems, but I will try some more I think.

---

### Post by DavidSommen on 2012-04-25
Miro, Dragon and Mplayer gave the same results... video tearing.

---

### Post by Lollerke on 2012-04-25
Same here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/961124]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/961124") [https://bugs.launchpad.net/unity-2d/+bug/792315]("https://bugs.launchpad.net/unity-2d/+bug/792315")
One solution is to create a xorg.conf file with the "sudo X -configure" command. Modify the file at the EXAVSync line to:
Option "EXAVSync" "true", copy the xorg.conf to the /etc/X11/ directory and do a restart. You will have tear free video under Unity 2D.

---

### Post by DavidSommen on 2012-04-26
> **Lollerke said:**
> Same here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/961124]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/961124") [https://bugs.launchpad.net/unity-2d/+bug/792315]("https://bugs.launchpad.net/unity-2d/+bug/792315")
One solution is to create a xorg.conf file with the "sudo X -configure" command. Modify the file at the EXAVSync line to:
Option "EXAVSync" "true", copy the xorg.conf to the /etc/X11/ directory and do a restart. You will have tear free video under Unity 2D.

I don't seem to have a xorg.conf, only xorg.conf-backup-120324133430 and xorg.conf.failsafe in /etc/X11.

---

### Post by Lollerke on 2012-04-26
Yes, by default you don't have one. You have to create it manually which will only work when the xserver is not running:
1. Press CRTL+ALT+F1 in the Unity2D session.
2. Log in with your user.
3. Type "sudo stop lightdm".
4. Type "sudo X -configure". This will create a xorg.conf.new file in your home directory.
5. Type "sudo start lightdm". This gives back the xserver and the GUI.
6. Edit the xorg.conf.new file as I mentioned and rename it to xorg.conf and copy it to /etc/X11.
7. Restart the computer.

---

