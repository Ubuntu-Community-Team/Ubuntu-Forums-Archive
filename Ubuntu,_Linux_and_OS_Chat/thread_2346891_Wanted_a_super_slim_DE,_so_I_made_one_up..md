---
title: "Wanted a super slim DE, so I made one up."
date: 2016-12-19
forum: Ubuntu, Linux and OS Chat
---

### Post by dorian7 on 2016-12-19
Not from scratch mind you, but I'm pretty happy with the result considering how well it works, and it uses under 200 MB of RAM when booted.

I spent some time this afternoon making a how-to video if anyone else wants to try to make their own: [https://www.youtube.com/watch?v=fxWRZuKqmk4](https://www.youtube.com/watch?v=fxWRZuKqmk4)

With openbox it's easy to pick your parts, for instance, if you don't want to use tint2 as a panel/taskbar, you can use fbpanel, or lxpanel, etc.

The base Ubuntu I installed is the Ubuntu MinimalCD.  You can find the ISO here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


To install all the packages I'm using "sudo apt install" and the packages I install, in the order I install them, are:


lightdm
openbox-gnome-session
openbox
gnome-terminal
obmenu
gedit
tint2
docky
nitrogen
ubuntu-wallpapers
pcmanfm
lxappearance
xcompmgr
firefox
pavucontrol
volti
gconf-editor


The file you want to create/edit for openbox autostart commands is located at ~/.config/openbox/autostart.sh


The file you want to create/edit to automatically login is located at /etc/lightdm/lightdm.conf (Must be root to edit/create this file).

---

### Post by DuckHook on 2016-12-19
Not technical help request, so *thread moved to **Ubuntu, Linux and OS Chat** as the more appropriate forum.*

---

### Post by dorian7 on 2016-12-19
I just started posting here, but I made a how-to video of a core install I built-up starting with nothing but the minimal install with just a console and working my way into a basic functional GUI with a few apps.  I'm planning a "Part 2" for alternative GUI options and further expanding functionality.

Thread is here : [https://ubuntuforums.org/showthread.php?t=2346891](https://ubuntuforums.org/showthread.php?t=2346891)

Straight to the video here : [https://www.youtube.com/watch?v=fxWRZuKqmk4](https://www.youtube.com/watch?v=fxWRZuKqmk4)

---

### Post by wildmanne39 on 2016-12-19
Threads merged. Please do not post duplicates, it dilutes community effort.

---

### Post by mörgæs on 2016-12-20
Thanks for the video. 

I think it would be easier for people to try if they also had a list of commands to run. Could you post that, please?

---

### Post by tuyenhuynhvan on 2016-12-20
thanks for the video tutorial

---

### Post by dorian7 on 2016-12-20
> **mörgæs said:**
> Thanks for the video. 

I think it would be easier for people to try if they also had a list of commands to run. Could you post that, please?

Thanks for the tip!  Added it to my original post :)

---

### Post by bluemagoo on 2016-12-21
looks good - !  I noticed that he is using a VM;  you should consider FreeBSD as well or OpenBSD - both lean installs, work very well in a VM especially OpenBSD, and the beauty of OpenBSD is it comes with the X libraries with fvwm pre-installed.  If you want something better, you can either install fvwm2 or xfce, very easily.    FreeBSD is equally easy but does require a bit more effort, since you need to install everything after the base OS is up & running.

> **dorian7 said:**
> Not from scratch mind you, but I'm pretty happy with the result considering how well it works, and it uses under 200 MB of RAM when booted.

I spent some time this afternoon making a how-to video if anyone else wants to try to make their own: [https://www.youtube.com/watch?v=fxWRZuKqmk4](https://www.youtube.com/watch?v=fxWRZuKqmk4)

With openbox it's easy to pick your parts, for instance, if you don't want to use tint2 as a panel/taskbar, you can use fbpanel, or lxpanel, etc.

The base Ubuntu I installed is the Ubuntu MinimalCD.  You can find the ISO here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


To install all the packages I'm using "sudo apt install" and the packages I install, in the order I install them, are:


lightdm
openbox-gnome-session
openbox
gnome-terminal
obmenu
gedit
tint2
docky
nitrogen
ubuntu-wallpapers
pcmanfm
lxappearance
xcompmgr
firefox
pavucontrol
volti
gconf-editor


The file you want to create/edit for openbox autostart commands is located at ~/.config/openbox/autostart.sh


The file you want to create/edit to automatically login is located at /etc/lightdm/lightdm.conf (Must be root to edit/create this file).

---

### Post by mikodo on 2016-12-21
'Tis going to be fun to follow this vid and the next one you have planned. 

Your voice and etiquette is pleasing to follow.

---

### Post by vasa1 on 2016-12-21
> **dorian7 said:**
> ...
To install all the packages I'm using "sudo apt install" and the packages I install, in the order I install them, are:
...
obmenu
...
xcompmgr
...
gconf-editor


The file you want to create/edit for openbox autostart commands is located at ~/.config/openbox/autostart.sh
...
[LIST]
[*]I don't use *obmenu*. I prefer to edit **rc.xml* by hand.
[*]You may consider adding *obconf*.
[*]Instead of *xcompmgr*, I use *compton*.
[*]I don't have *gconf-editor*. I have *dconf-editor*.
[/LIST]

And I think it's now just *autostart* although *autostart.sh* may still work. I use *autostart*.

---

### Post by mikodo on 2016-12-22
A little off topic here, but I thought I would look again at what my stock .iso Xubuntu DE 16.04.1 install was using in memory. I do shut off some things I don't use, but not much; although it is a bigger install than this. It was 200mb of memory exactly, with the terminal open and using < free -m > command. It surprised me how little if is still. Although, I remember how not too many years ago, a fresh install was about 109 GB of memory. I credit the big increase lately to, SystemD init system as of late.

I have never built a system like this, and it is illuminating for me to watch how it is done. Like mentioned above me, I think Ubuntu (?Debian) went to dconfig-editor quite a few years ago, and maybe other things that vasa1 mentioned that I am not sure of.

Thanks again.

(Please excuse any grammatical mistakes, I just had bi-lateral eye-surgery and I am not able to see too well yet)

---

### Post by dorian7 on 2016-12-22
> **mikodo said:**
> 'Tis going to be fun to follow this vid and the next one you have planned. 

Your voice and etiquette is pleasing to follow.

Thanks!  I've made 3 more and uploaded them to my youtube channel, just showing a couple extra things, and a way to get your desktop up without using a display manager.

> **vasa1 said:**
> 
[LIST]
[*]I don't use *obmenu*. I prefer to edit **rc.xml* by hand.
[*]You may consider adding *obconf*.
[*]Instead of *xcompmgr*, I use *compton*.
[*]I don't have *gconf-editor*. I have *dconf-editor*.
[/LIST]

And I think it's now just *autostart* although *autostart.sh* may still work. I use *autostart*.

Yes there's several ways to skin a cat when it comes to doing things in Linux :)  I didn't try using just autostart without the .sh but I supposed they may have changed it.  I just wrote the filename according to some documentation I read, which may have been outdated.  Either way, it works.  I haven't' tried compton but I might see how it compares to xcompmgr with resource usage.

> **mikodo said:**
> A little off topic here, but I thought I would look again at what my stock .iso Xubuntu DE 16.04.1 install was using in memory. I do shut off some things I don't use, but not much; although it is a bigger install than this. It was 200mb of memory exactly, with the terminal open and using < free -m > command. It surprised me how little if is still. Although, I remember how not too many years ago, a fresh install was about 109 GB of memory. I credit the big increase lately to, SystemD init system as of late.

I have never built a system like this, and it is illuminating for me to watch how it is done. Like mentioned above me, I think Ubuntu (?Debian) went to dconfig-editor quite a few years ago, and maybe other things that vasa1 mentioned that I am not sure of.

Thanks again.

(Please excuse any grammatical mistakes, I just had bi-lateral eye-surgery and I am not able to see too well yet)

dconf is newer yes, I used 12.04 for the longest time.  The only reason I used gconf-edit was to change the Docky item setting.  In my other videos, I've actually switched from docky to plank because it uses even less resources so there's no need for dconf-editor OR gconf-editor at all in this case, because plank doesn't have that anchor icon.

I also uploaded a CPU/Memory usage video showing that when booted into the DE I made up, it only uses 160MB of RAM.  I think that's pretty nice and light :)

---

### Post by dorian7 on 2016-12-22
Even more barebones installation (without a display manager) : [https://www.youtube.com/watch?v=OP9l-m02Yng](https://www.youtube.com/watch?v=OP9l-m02Yng)

---

### Post by dorian7 on 2016-12-22
> **vasa1 said:**
> 
[LIST]
[*]I don't use *obmenu*. I prefer to edit **rc.xml* by hand.
[*]You may consider adding *obconf*.
[*]Instead of *xcompmgr*, I use *compton*.
[*]I don't have *gconf-editor*. I have *dconf-editor*.
[/LIST]

And I think it's now just *autostart* although *autostart.sh* may still work. I use *autostart*.

So I gave compton a shot, and found that even at idle with nothing but the terminal window open, compton used a constant 1.5-3% CPU, and 91 MB of memory.

xcompmgr on the other hand uses 0% until you start moving windows, and then it goes back to 0% CPU.  And it only uses 1.5 MB of memory.  You should try xcompmgr, it's quite light!

As for adding obconf, I'm not sure I understand that comment.  obconf comes with openbox, and I used it in the video to change the window themes and font sizes in the video.  I do like to create a submenu afterwards and move all the openbox stuff into a submenu just to organize the clutter :D

---

### Post by vasa1 on 2016-12-22
Re. *obconf*, you're probably right. I use the Openbox session of Lubuntu and have no experience with minimal systems. But what my suggestion was based on was the output of *apt show openbox* which has *obconf* as a recommend rather than as a dependency. So someone who goes the *--no-install-recommends* route may not have it:```
$ apt show openbox
Package: openbox
Version: 3.6.1-1ubuntu2
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Mateusz &#321;ukasik <mati75@linuxmint.pl>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,210 kB
Provides: x-session-manager, x-window-manager
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.35.9), libice6 (>= 1:1.0.0), libobrender32 (>= 3.6.0), libobt2 (>= 3.6.0), libsm6, libstartup-notification0 (>= 0.7), libx11-6, libxau6, libxext6, libxi6 (>= 2:1.2.99.4), libxinerama1, libxrandr2
Recommends: obconf, python-xdg | obsession, scrot
Suggests: menu, fonts-dejavu, python, libxml2-dev, tint2, openbox-menu, openbox-gnome-session (= 3.6.1-1ubuntu2), openbox-kde-session (= 3.6.1-1ubuntu2)
Breaks: menu (<< 2.1.12)
Homepage: http://www.openbox.org
Task: lubuntu-core
Supported: 3y
Download-Size: 266 kB
APT-Manual-Installed: yes
APT-Sources: http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Description: standards-compliant, fast, light-weight and extensible window manager

$ 

```Re. xcompmgr v/s compton, I'm guessing that the way one sets up the compositor will contribute to RAM and CPU usage. The image I posted is with the Vivaldi browser, lxterminal, and gnome-system monitor open. I'll stick with compton, partly because I lost quite a bit of sleep figuring out the syntax of compton.conf ;)

---

### Post by dorian7 on 2016-12-23
> **vasa1 said:**
> Re. *obconf*, you're probably right. I use the Openbox session of Lubuntu and have no experience with minimal systems. But what my suggestion was based on was the output of *apt show openbox* which has *obconf* as a recommend rather than as a dependency. So someone who goes the *--no-install-recommends* route may not have it:```
$ apt show openbox
Package: openbox
Version: 3.6.1-1ubuntu2
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Mateusz &#321;ukasik <mati75@linuxmint.pl>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,210 kB
Provides: x-session-manager, x-window-manager
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.35.9), libice6 (>= 1:1.0.0), libobrender32 (>= 3.6.0), libobt2 (>= 3.6.0), libsm6, libstartup-notification0 (>= 0.7), libx11-6, libxau6, libxext6, libxi6 (>= 2:1.2.99.4), libxinerama1, libxrandr2
Recommends: obconf, python-xdg | obsession, scrot
Suggests: menu, fonts-dejavu, python, libxml2-dev, tint2, openbox-menu, openbox-gnome-session (= 3.6.1-1ubuntu2), openbox-kde-session (= 3.6.1-1ubuntu2)
Breaks: menu (<< 2.1.12)
Homepage: http://www.openbox.org
Task: lubuntu-core
Supported: 3y
Download-Size: 266 kB
APT-Manual-Installed: yes
APT-Sources: http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Description: standards-compliant, fast, light-weight and extensible window manager

$ 

```Re. xcompmgr v/s compton, I'm guessing that the way one sets up the compositor will contribute to RAM and CPU usage. The image I posted is with the Vivaldi browser, lxterminal, and gnome-system monitor open. I'll stick with compton, partly because I lost quite a bit of sleep figuring out the syntax of compton.conf ;)

You're right about obconf.  The version I run also recommends obconf, but it does get installed somehow.  When I first installed openbox I always change the font size and theme.

I found compton did have much more options to play with.  But that is another reason I like xcompmgr; It's simple, and doesn't require a config file.  Running --help shows you the basic options for shadows and fades, then you just make sure it starts with the right switches.

For example, in my openbox autostart, I start the compositor with

```
xcompmgr -cfF -t-9 -l-11 -r9 -o.95 -D6 -I0.06 -O0.06 &
```

Looks confusing at first, but after reading the help, it's quite straightforward.

```
dorian@ubuntu:~$ xcompmgr -help
xcompmgr: invalid option -- 'h'
xcompmgr v1.1.7
usage: xcompmgr [options]
Options:
   -d display
      Specifies which display should be managed.
   -r radius
      Specifies the blur radius for client-side shadows. (default 12)
   -o opacity
      Specifies the translucency for client-side shadows. (default .75)
   -l left-offset
      Specifies the left offset for client-side shadows. (default -15)
   -t top-offset
      Specifies the top offset for clinet-side shadows. (default -15)
   -I fade-in-step
      Specifies the opacity change between steps while fading in. (default 0.028)
   -O fade-out-step
      Specifies the opacity change between steps while fading out. (default 0.03)
   -D fade-delta-time
      Specifies the time between steps in a fade in milliseconds. (default 10)
   -a
      Use automatic server-side compositing. Faster, but no special effects.
   -c
      Draw client-side shadows with fuzzy edges.
   -C
      Avoid drawing shadows on dock/panel windows.
   -f
      Fade windows in/out when opening/closing.
   -F
      Fade windows during opacity changes.
   -n
      Normal client-side compositing with transparency support
   -s
      Draw server-side shadows with sharp edges.
   -S
      Enable synchronous operation (for debugging).

```

It's just window shadow offset, and fade times really. :)

---

