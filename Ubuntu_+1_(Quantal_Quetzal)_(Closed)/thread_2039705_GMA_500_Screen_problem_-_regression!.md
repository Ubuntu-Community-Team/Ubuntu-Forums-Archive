---
title: "GMA 500: Screen problem - regression!"
date: 2012-08-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by simplygades on 2012-08-09
Hi! 
I was trying to report a bug, but for some reason I can't figure out how to do it via my browser anymore, and apport crashes, too!

I use Kubuntu, but the same issue exists using the daily Ubuntu build. My hardware is a GMA500 Acer-AO751h, supported by the kernel by gma_500 module I think. 12.04 works fine, however with 12.10 the screen appears to be shifted ~ 5 pixels upwards, thus cropping the top 5 pixels and leaving a row of black ones on the bottom. Moreover, the screen turns black randomly for 1 sec, and then back to normal, that being accompanied by a proccesing hiccup, i.e. skipping/scrambling the audio if I'm listening to something at that moment.

Please, add some info if you're on the same boat, and help me with filing a bug report the safe way. Thanks!

---

### Post by lucazade on 2012-08-09
yep, same here using gma500_gfx and fbdev as xorg driver.
The screen is identified as 1360x768 instead of 1366x768.. you can check it in /var/log/Xorg.0.log
This is a regression. haven't seen the screen blanking btw.

Have you look at this thread?
[http://ubuntuforums.org/showthread.php?t=2012088&page=4](http://ubuntuforums.org/showthread.php?t=2012088&page=4)

We can now use "modesetting" driver..
It is a better solution and the screen resolution is correctly identified.

---

### Post by simplygades on 2012-08-09
Thank you Luca! Hadn't noticed the thread. I'll try to configure Xorg the way you suggested. However Ksyslog says:


	Information	[    22.078] (--) FBDEV(1): Virtual size is 1366x768 (pitch 1366)
:confused: Is that before the module takes over or sth? Sorry if I don't get it, but thats the only line with resolution reference. Cheers!

---

### Post by lucazade on 2012-08-10
> **simplygades said:**
> Thank you Luca! Hadn't noticed the thread. I'll try to configure Xorg the way you suggested. However Ksyslog says:


	Information	[    22.078] (--) FBDEV(1): Virtual size is 1366x768 (pitch 1366)
:confused: Is that before the module takes over or sth? Sorry if I don't get it, but thats the only line with resolution reference. Cheers!

I don't have the netbook here to check the log.. I remember to have seen a wrong 1360x768 in the logs.

Btw you just need to install xserver-xorg-video-modesetting and reboot (no manual tweak to /etc/X11/xorg.conf, it is done automatically). Let me know ;)

---

### Post by fjgaude on 2012-08-10
The last update containing kernel 3.5.0-9 made much come together for my Poulsbo box, dell mini-10 netbook. Am using the **modesetting** driver.

```
sudo apt-get install xserver-xorg-video-modesetting

```
Thanks to Luca for keeping us informed on what to do.

```
 sudo mv /usr/lib/pm-utils/sleep.d/99video /usr/lib/pm-utils/99video
```

Works now for Suspend/Resume! Brightness always worked.

```
frank@sweetie:~$ echo && echo -n "Date/Time: " && date && echo -n "Release: " && lsb_release -sd && echo -n "Kernel: " || cat /etc/*release && uname -s -r && echo -n "Unity: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo &&  dpkg -s mesa-utils && echo || echo && echo "Xserver xorg core:" && apt-cache policy xserver-xorg-core | grep Installed && echo

Date/Time: Fri Aug 10 17:18:45 PDT 2012
Release: Ubuntu quantal (development branch)
Kernel: Linux 3.5.0-9-generic
Unity: unity 6.0.0

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

dpkg-query: package 'mesa-utils' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Xserver xorg core:
  Installed: 2:1.12.1.902-1ubuntu1
```

**GtkPerf** 0.40 - Starting testing: Fri Aug 10 17:20:01 2012

GtkEntry - time:  0.25
GtkComboBox - time:  4.92
GtkComboBoxEntry - time:  3.01
GtkSpinButton - time:  0.56
GtkProgressBar - time:  0.60
GtkToggleButton - time:  1.86
GtkCheckButton - time:  0.54
GtkRadioButton - time:  0.88
GtkTextView - Add text - time:  4.07
GtkTextView - Scroll - time:  1.19
GtkDrawingArea - Lines - time:  5.49
GtkDrawingArea - Circles - time:  8.24
GtkDrawingArea - Text - time:  4.63
GtkDrawingArea - Pixbufs - time:  0.57
 --- 
Total time: 36.81

---

### Post by blugeco on 2012-08-13
Hi,

I can confirm this solution also works on Fedora 17 with the latest kernel 3.5.

Same issue was found and installing 'modesetting' driver 

> yum install xorg-x11-drv-modesetting

fixed it.

Thanks guys,

blugeco

---

### Post by simplygades on 2012-08-27
> **lucazade said:**
> I don't have the netbook here to check the log.. I remember to have seen a wrong 1360x768 in the logs.

Btw you just need to install xserver-xorg-video-modesetting and reboot (no manual tweak to /etc/X11/xorg.conf, it is done automatically). Let me know ;)

Ok, finally I'll let you know, although with some delay. I installed the modesetting package, can't tell for sure what the improvement in speed is, I'm just used to it and it's  OK, probably a bit snappier in some occasions. The pixel-shifting is now fixed, plymouth   works better and I can use "Redshift" again! :smile: It's really great if you spend a lot of night time on the computer, and it didn't work since the transition to the kernel module. Right now, Kubuntu Quantal, works better than Precise for me...

Should I mark the thread as "SOLVED"?

---

### Post by fjgaude on 2012-08-27
I'm leaving 12.10 as it is until after Beta1 comes out. Simply don't have the time to mess with it. 12.04 works great and I'm sure 12.10 will also after the devs gets all the changes made.

---

### Post by lucazade on 2012-08-28
> **simplygades said:**
> Ok, finally I'll let you know, although with some delay. I installed the modesetting package, can't tell for sure what the improvement in speed is, I'm just used to it and it's  OK, probably a bit snappier in some occasions. The pixel-shifting is now fixed, plymouth   works better and I can use "Redshift" again! :smile: It's really great if you spend a lot of night time on the computer, and it didn't work since the transition to the kernel module. Right now, Kubuntu Quantal, works better than Precise for me...

Should I mark the thread as "SOLVED"?

ah great.. happy this works also for you :)

---

### Post by KEYofR on 2012-09-09
> **lucazade said:**
> yep, same here using gma500_gfx and fbdev as xorg driver.
The screen is identified as 1360x768 instead of 1366x768.. you can check it in /var/log/Xorg.0.log
This is a regression. haven't seen the screen blanking btw.

Have you look at this thread?
[http://ubuntuforums.org/showthread.php?t=2012088&page=4](http://ubuntuforums.org/showthread.php?t=2012088&page=4)

We can now use "modesetting" driver..
It is a better solution and the screen resolution is correctly identified.

*sigh* it's not better when I had a working X yesterday but now I have no X at all :(
I really HATE that all the distros are using plymouth now and that you can't remove it because so many of the basics actually depend on it. mountlall? really? depends on plymouth? crap.

Anyways, Vaio P. I had a working X on prcise, kernel 3.2.0, gma500_gfx, xorg apparently old held back from natty. Then I upgraded everything to quantal except xorg stayed the same still. kernel 3.5.0-14, gma500_gfx, same old xorg held back, plymouth hard-disabled by moving some of it's files. 
On 3.5.0 X still worked but became buggy. At randome times from a few times a minute to a few times an hour the screen would scramble. I could fix it just by flipping over to a text console like tty1 and back to tty7.

So, hoping to fix that annoyance I found this thread and did as directed above, or tried to since it leaves an unknown number of details unspecified.

What I did was install the xserver-video-modesetting, which automatically removed all the old xorg packages I had and installed a few other new ones.
I reinstalled plymouth and the lubuntu theme because this thread and the linked one _seem_ to be saying that plymouth is now a necessary step in the process for the new xorg modesetting driver to work.
I put "splash" back in the grub command line defaults.
update-initramfs to make sure in includes plymouth.
update-grub to make sure grub.cfg gets the new command line.
Verifiied grub.cfg says splash and $vt_handoff now

On reboot, grub2 sets the correct native 1600x768 mode for gfxterm
No splash loads when I boot linux, but the kernel messages display on a text console that is also native 1600x768.
Then lightdm switches to tty7, but no gui, just a plymouth error message:

plymouthd: ply-terminal.c:611: ply_terminal_open: Assertion `terminal != ((void *)0)' failed.

What secret undocumented yet crucial details might I be missing?
The only thing I can see right off is probably not even really an error. In grub2 at boot time, e to edit, the kernel command line ends with " splash $vt_handoff"
F2 for grub prompt and "set" shows several variables including linux gfxmode = keep (I'm not looking at the grub2 screen right now of course so I don't remember the variable name exactly, but there was one like grub gfxmode 1600x768x16 and another like linux gfxmode or linux gfx payload = keep, two different variables and only the "linux" one said keep.) and there was no variable named vt_handoff at all. I'm guessing that might be normal, maybe the variable doesn't exist until later when you actually choose that menu option and execute it?
The only other thing that looks wrong is no splash appeared even though the command line says splash and I have plymouth and a theme installed, but I don't have "quiet" on the command line so maybe that's normal too.

Just glad I have wicd-curses to get on wifi, lynx to google this thread up, and gpm to cut & paste the error message from the other tty.
Damned gma500. This $1200 Vaio P hasn't worked right for more than a week at a time since 2009 when I got it and it's completely obsolete by now and still doesn't work.

---

### Post by KEYofR on 2012-09-10
Verified/tried more things:
Verified $vt_handoff was fine, /proc/cmdline shows vt.handoff=7
Put quiet back on cmdline
I had /usr/lib/pm-utils/sleep.d/99Video moved off to the side, I put it back.
I tried 3 different values for acpi_backlight, not present on cmdline, =video, =vendor
I removed mem=1980mb from cmdline
Cmdline does have console=tty1, I don't remember if that was stock or added, maybe I should try without it?
I tried creating a /etc/X11/xorg.conf that had just the device and screen sections in the above thread to specify the modesetting driver. It had JUST those 3 minimal sections nothing else, so, normally or in the old days that would not be a valid xorg.conf but today with xorg filling in everything auto?  Anyways, I also tried with no xorg.conf at all. And no emgd thing leftover in /usr/share/X11/xorg.conf.d either. I did used to have emgd in the past. This install has in-place upgraded from karmic times but I'm pretty good about making sure the upgrades go smoothely and cleaning out the leftover stuff.
When I boot now, it's worse than my last post, now the backlight goes out right about when lightdm loads, and nothing on the keyboard or mouse wakes it up. Alt+F1, moving the mouse, any other keys, the lcd/vga toggle Fn hot key, nothing. 
BUT, if I connect the external vga dongle THAT wakes it up. I can immediately disconnect the external monitor again and the backlight stays on after that*.
(*) If I'm on battery, the backlight will blank from inactivity after a minute or two, but keypress/mouse wakes it right back up.

One thing the new driver is not, is fully automatic.

---

### Post by KEYofR on 2012-09-10
Meant to say Ctrl+Alt+F1 and the screen blanks from inactivity on AC power also not just battery.
I also just tried uninstalling every xserver except modesetting, including intel, fbdev, and vesa.
Now I guess I'll try removing modesetting and installing fbdev and/or vesa and hope I can get one of those to work the old way by disabling plymouth, no splash, no quet, etc, without having to actually reinstall the really old xorg I was using up to a day ago.

---

### Post by KEYofR on 2012-09-10
Uninstalled xserver-xorg-video-modesetting, reinstalled fbdev exclusively, no-go, removed fbdev and installed vesa, no-go, reinstalled modesetting, fbdev, vesa, and intel, which also pulled in libxcb-dri2-0, disabled plymouth my moving it's files as I had originally on the older xorg, removed splash and quiet from grub kernel cmdline, regenerated initrd and grub, still no-go. This sucks. At boot I get a native 1600x768 resolution text console for some kernel messages, then the screen goes black. Now the backlight doesn't go off, Instead it's switching to tty7, totally black with no plymouth error any more, but the backlight is on and if I move the mouse the gpm mouse cursor appears right away. The text consoles are functional with no need to wake it up by the trick of connecting the external monitor to the vga port. Alt+F1 switches to tty1, don't need Ctrl+Alt+F1 which suggests no X is running, and sure enough ps shows lightdm running but no Xorg.

How is this supposed to work on quantal? This isn't regression it's completely dead. Can someone with a working X on gma500 on quantal please document their setup better than "just enable quantal proposed and get xorg 1.13 and the modesetting xserver and kernel 3.5.0 and it all just works by itself now not like the old days"

---

### Post by KEYofR on 2012-09-10
Well of all the things....

So I'm working now. The last change I made was, I was trying to manually start X by itself to take lightdm and booting out of the picture, and startx said there was no /usr/bin/X. So I was looking around in aptitude and I noticed that although I had some xserver-xorg-video-* installed, the package "xorg" was not installed.

So I installed that, and it pulled in a couple of other packages like evdev, It did not pull in all the 50 other xservers for other video cards but did pull in a bout 4 or 5 packages total.

Sure enough, one of those provided /usr/bin/X and immediately startx works, startlxde works, and "start lightdm" works.

/var/log/Xorg.0.log shows that it loaded all three fbdev, vesa, and modesetting but kept modesetting and unloaded vesa and fbdev. 

kernel command line has nothing video related on it right now, no console=tty1, no quiet, no splash, no mem=1920mb, no acpi_backlight.

At this point I don't care about the finer points of suspend/resume, backlight keys etc, so I'm not saying any of that works or doesn't work or how well. Just that I have a working gui at all.

I don't know how I managed not to have "xorg" installed but it must be a result of the in-place upgrading from an older xorg that had different package names and different package interdependencies? Such that uninstalling the old xserver caused the old xorg to get uninstalled, yet installing the new xserver did not cause the new xorg to get installed? I would have assumed any number of installed packages like xserver-* and lightdm and lxde* would have  ended up requiring the top level xorg package but somehow that was not the case.

---

### Post by fjgaude on 2012-09-10
I'm updating my 12.10 install right now from its July date, about 600 files and a new kernel. I'll let you know what happens.

I have not issues with 12.04, a happy camper. I'll keep that partition until I can get 12.10 working reliably. After all the Beta1 doesn't seem that fixed. We'll wait until the release and the guys let us know what it takes to correctly install.

I can offer no advise to you and your issues. Sorry!

---

### Post by fjgaude on 2012-09-10
Well, after the long update, upgrade all is well with Quantal. Everything seems to be working just fine, even WiFi. So...

Happy to see your netbook is working fine also.

---

### Post by mikewhatever on 2012-09-12
> **fjgaude said:**
> Well, after the long update, upgrade all is well with Quantal. Everything seems to be working just fine, even WiFi. So...

Happy to see your netbook is working fine also.

I've tested mine, also a Dell Mini 10, and can't really say that all is well. It boots, and the resolution is correct, but is really slow. Obviously, Compiz is no match for gma500, the netbook also runs considerably hotter. I've been thinking about turning mine into a no GUI server. :)

---

### Post by fjgaude on 2012-09-12
Okay, you are right... the CPU has more work to do than with 12.04 because of the use of llvmpipe that permits the removable of the Unity 2D package. Maybe with them tuning a little things will get better, else we will simply have to continue to use 12.04.

---

### Post by lucazade on 2012-09-13
llvmpipe is too heavy for the gma500 netbooks.. so no unity.
Kde works like a charm, lxde and xfce should work well as well.. so I suggest to try other DE.

---

### Post by NormanFLinux on 2012-09-14
> **lucazade said:**
> llvmpipe is too heavy for the gma500 netbooks.. so no unity.
Kde works like a charm, lxde and xfce should work well as well.. so I suggest to try other DE.

The screen crashes at times, it runs slow and Dash home is slow to load. And the bottom Unity icons are all blanked out. I don't know if llvmpipe has anything to do with it. It may be a desktop/graphics stability issue.

I've never seen that problem with 12.04. The GMA 500 netbook can run Unity 2D and Cinnamon 2D so it shouldn't be a problem with the Gallium llvmpipe which is supposed to allow default Unity/Cinnamon desktop environments to be run on computers without accelerated graphics video cards.

My Dell Mini 1010 always defaults to 1076 X 826 which is the only allowed screen size under any distro I've installed on it.

---

### Post by lucazade on 2012-09-15
> **NormanFLinux said:**
> so it shouldn't be a problem with the Gallium llvmpipe which is supposed to allow default Unity/Cinnamon desktop environments to be run on computers without accelerated graphics video cards.


Gallium llvmpipe allows to execute Opengl stuff on the CPU instead of the GPU.
This means that the Atom is doing a giant work.. and it is simply not able to handle it.

> The Gallium llvmpipe driver is a software rasterizer that uses LLVM to do runtime code generation. Shaders, point/line/triangle rasterization and vertex processing are implemented with LLVM IR which is translated to x86 or x86-64 machine code. Also, the driver is multithreaded to take advantage of multiple CPU cores (up to 8 at this time). It's the fastest software rasterizer for Mesa.
[http://www.mesa3d.org/llvmpipe.html](http://www.mesa3d.org/llvmpipe.html)

llvmpipe needs at least a multicore 64bit cpu to work well and a lot of profiling... it is not good for ARM or Atom. take a look at phoronix benchmarks.

---

### Post by fjgaude on 2012-09-15
Thanks, Luca, for the education. I suppose that GMA500 boxes will not be of much use when 12.10 is released. We'll find that 12.04 will be good for five years. When that period is over my Dell mini-10 will be retired to the wood pile. So be it.

---

### Post by NormanFLinux on 2012-09-15
> **lucazade said:**
> Gallium llvmpipe allows to execute Opengl stuff on the CPU instead of the GPU.
This means that the Atom is doing a giant work.. and it is simply not able to handle it.


[http://www.mesa3d.org/llvmpipe.html](http://www.mesa3d.org/llvmpipe.html)

llvmpipe needs at least a multicore 64bit cpu to work well and a lot of profiling... it is not good for ARM or Atom. take a look at phoronix benchmarks.

I did a clean install of Ubuntu 12.10 and it runs acceptably except for occasional crashes.  The point is llvmpipe WAS provided to run single core computers at a standard of efficiency minus all the fancy graphics. I can live without the fancy rendering. All I care is the computer works. The lower half of the Unity launcher is mushed up.

Its a beta after all and if Canonical wants to make Unity run on ALL computers - management problems need to be resolved. I run SUSE 12.2 Cinnamon on a dog of VIA C-7 chip network and everything works fine!

My Dell Mini 10 boots up to a black screen rather than the splash screen but then the desktop loads to the correct screen size. As mentioned its a beta and far more work has to be done to make Unity run acceptably on low-end computers.

---

### Post by KEYofR on 2012-10-10
I haven't had any video problems on my gma500 Sony Vaio P since the saga above. But this is with lxde and e17 and xfce. No kde, gnome, and certainly no unity.

On 3.6.0 mainline nightly currently it's even faster than it's ever been before except for the few times I was able to use a proprietary driver.
Not fast exactly, but I can watch a YouTube video in a 2 or 3 inch window and it's almost smooth and the audio mostly stays in sync.
All the normal window/app/desktop activity is fine.

On the other hand my ath9k wifi has been complete crap on the entire range of 3.5.0 and 3.6.0. Worked fine on 3.2.0. Don't remember if I ever tried anything between 3.2.0 and 3.5.0. That's why I'm posting this from my phone!

Can't win.

---

### Post by KEYofR on 2012-10-10
...online via usb tether to my phone, which is using the very same wifi that the laptop can't use. Vaguely humiliating. :) At least I didn't have to boot to Windows or Puppy.

---

