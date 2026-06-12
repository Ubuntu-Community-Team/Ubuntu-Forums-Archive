---
title: "How is gnome working now with trusty?"
date: 2014-02-21
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-21
I use the gnome desktop on 12.04
I read before has some trouble?

---

### Post by cariboo on 2014-02-21
I'm not sure which gnome you are asking about, but I have Trusty gnome-shell installed on a 16GiB usb thumb drive, I don't update it as often as I should, so when I do it usually takes about half an hour. I used it all day yesterday, after one of my hard drives crashed, trying to get a working Trusty daily iso, I even used it to create a bootable usb thumb drive about 4 times, it booted every time, but the first 3 times ubiquity crashed to the point where all I had was a black screen..

Gnome-shell itself ran great without any hiccups. :)

---

### Post by 23dornot23d on 2014-02-21
I have been doing a test with upgrading from a very early version of Ultimate 2.8 and have taken it right upto 14.04

here is a video of the Gnome Classic running in it ...... my main interest is always in 3d ........ but I still have a problem
with something I use a lot ........ which is wings3d ( this seems to have been removed from the  repos from before saucy )

Here is a video ..... but its running on a optimus laptop with a nvidia gt540m graphics card ..........

[http://youtu.be/f5gFtLoLCb4](http://youtu.be/f5gFtLoLCb4)

Gnome shell runs well too ........ will post a video of that soon ......... just to show it off
also have compiz running in xfce .... but that seems a tad unstable at the moment but
no doubt it will get sorted.

The devs are doing a great job this time and there seems to be a few choices for desktops
hope that remains for the final release ....... so far having fun ........ ;)

---

### Post by sdowney717 on 2014-02-21
Great news, I expect I will upgrade this weekend then.

---

### Post by 23dornot23d on 2014-02-21
Not sure if its stable till April ....... would have to look up when the release date is .........

This is the video of Gnome-Shell ..... [http://youtu.be/5l9tQMIPJzs](http://youtu.be/5l9tQMIPJzs)

With the small problem with wings3d ...... if anyone knows how to fix the flickering that would be
a bonus ..... but as I say its only in wings3d at the moment.

They seem to have removed wings3d from the repos ....... maybe one way of solving problems
but not the way I would like them sorting.

Will post some more if you want ...... but the other things are compiz and enlightenment
just check my You tube channel ....... as I usually add things there if I get problems or success

I like this new version ....... first time my graphics have worked something like on this optimus
machine too ........ but had to do a little work to sort it out.

---

### Post by kurt18947 on 2014-02-21
It may depend on your hardware.  I have 2 installs of 14.04 running - 1 homebuilt AMD based MoBo with Nvidia 210 video and a Thinkpad T61 w/Intel video.  The desktop is running quite well.  The Thinkpad, usually a smooth ride with Ubuntu is having issues.  I've reinstalled a couple times but I'm having problems with suspend/resume and also logging out/logging in.  I get a black screen with maybe a mouse pointer but no desktop.  Cold boots are usually okay though I occasionally have to reboot.  I installed XFCE4 (Not XFCE-desktop) and it seems unaffected so it appears to me like a gnome-shell issue.

---

### Post by OGpmpdog on 2014-02-22
> **kurt18947 said:**
> It may depend on your hardware.  I have 2 installs of 14.04 running - 1 homebuilt AMD based MoBo with Nvidia 210 video and a Thinkpad T61 w/Intel video.  The desktop is running quite well.  The Thinkpad, usually a smooth ride with Ubuntu is having issues.  I've reinstalled a couple times but I'm having problems with suspend/resume and also logging out/logging in.  I get a black screen with maybe a mouse pointer but no desktop.  Cold boots are usually okay though I occasionally have to reboot.  I installed XFCE4 (Not XFCE-desktop) and it seems unaffected so it appears to me like a gnome-shell issue.

+1 here

Howdy, I've been running UG 14.04 on my T61 w/Nvidia card; despite recent & hairy updates, GS is working buttery smooth.  Suspend/Resume'Logout/in work fine.  

The only issue I had was that I had to upgrade to Nvidia 331, the Trusty kernels didnt like 319 or 325.

However, on my UG desktop, I must reconfigure my dual-monitor setup each reboot.  I dont know why the monitor config file resets each reboot.  Everything else is working beautifully.

Peace.

---

### Post by 23dornot23d on 2014-02-22
Must admit that the storing of the screen configs dual screen seems to get lost each time I restart too
gets a tad annoying - setting it up each time ............... [http://youtu.be/7PlKDCXBFsE](http://youtu.be/7PlKDCXBFsE)

Almost as if the config file is not being used after the initial change or something else keeps over riding our choices.

I got to the stage of getting the lxde xrandr script and putting it into the ~/.config/autostart/

```

[Desktop Entry]
Type=Application
Name=LXRandR autostart
Comment=Start xrandr with settings done in LXRandR
Exec=xrandr --output HDMI1 --mode 1280x720 --rate 60.0 --output LVDS1 --mode 1366x768 --rate 60.0
OnlyShowIn=LXDE

```

but its not a pretty way of doing things and it takes extra time for the computer setting it up.

---

### Post by kansasnoob on 2014-02-22
> **sdowney717 said:**
> I use the gnome desktop on 12.04
I read before has some trouble?

Much more info is needed to give an accurate answer :)

Which GNOME DE are you using in Precise?

The default GNOME DE is now gnome-shell but there are alternative GNOME DE's:

[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

What trouble have you read about :confused:

---

### Post by sdowney717 on 2014-02-22
> **kansasnoob said:**
> Much more info is needed to give an accurate answer :)

Which GNOME DE are you using in Precise?

The default GNOME DE is now gnome-shell but there are alternative GNOME DE's:

[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

What trouble have you read about :confused:

I think gnome 3.6?
I use gnome shell 

Regarding troubles recalling some posts from a couple months ago gnome shell not working in trusty.
Things change, so checked in to see what's up.
I am doing the upgrade right now.

12.04 is wearing thin, I am having some issues, like desktop crashes with serious error, vlc not playing smooth due to old libavcodec, and oddly takes a long long time to show the desktop, and programs take  a long time to come up with the hard drive working hard. fragmented files??

---

### Post by sdowney717 on 2014-02-22
just got an upgrade error

and the upgrade quits

---

### Post by Doug S on 2014-02-22
My Gnome shell log on option has not worked since about January 17th. Eventually I learned of the "xrandr" trick mentioned a few posts back, and was able to use it. However, and as of yesterdays (or was it the day before? it's becoming a blur) it doesn't work at all.

For me an interesting note is that back at the end of January I finally got the ear of someone that really seemed to know what was going on. He said "Oh ya, this [part of the upgrade] is incompatible with that [a part that was not upgraded].  Try my PPA". I built a brand new GNOME install from the trusty daily of the time, proved it still didn't work, added the PPA, did an update/upgrade cycle and everything was perfect. Been waiting ever since.

By the way, my unity desktop shell is also completely broken and has been since about Monday. [Compiz just crashes with a segfault]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1282342")

Edit: After the second upgrades of today, my gnome is back working the way it has been since January 17th. If I use the "xrandr" trick then it seems to be O.K. 

References:
[https://bugs.launchpad.net/ubuntu-gnome/+bug/1273276](https://bugs.launchpad.net/ubuntu-gnome/+bug/1273276)
[http://irclogs.ubuntu.com/2014/01/30/%23ubuntu-gnome.html#t21:22](http://irclogs.ubuntu.com/2014/01/30/%23ubuntu-gnome.html#t21:22)
[URL="http://irclogs.ubuntu.com/2014/01/31/%23ubuntu-gnome.html"]http://irclogs.ubuntu.com/2014/01/31/%23ubuntu-gnome.html

[/URL]

---

### Post by sdowney717 on 2014-02-22
I had to wipe and reinstall the os.
Now running on 14.04
Gnome shell is fine.
Got nvidia driver 331.38 from xorg-edgers.

---

### Post by 23dornot23d on 2014-02-22
grep -Fn 'NVIDIA' /var/log/Xorg.8.log ( think this only applies on mine Bumblebee install might be the Xorg.0.log )

as you are running the Nvidia 8400gs I think ..........

To check if it all loads ok ...........

Have you got better vlc playback now ?

also

grep -Fn 'GLX' /var/log/Xorg.0.log

---

### Post by kurt18947 on 2014-02-23
> **sdowney717 said:**
> I had to wipe and reinstall the os.
Now running on 14.04
Gnome shell is fine.
Got nvidia driver 331.38 from xorg-edgers.
I installed 331.38 from the additional drivers page.  That seems to have smoothed things out on the AMD/Nvidia machine.

---

### Post by sdowney717 on 2014-02-23
No EE errors.

Problem now is I cant get xorg.conf to have any effect. Everything in there ignored.

```
scott@scott-P5QC:~$ grep -Fn 'nvidia' /var/log/Xorg.0.log 
96:[    17.003] (II) LoadModule: "nvidia"
97:[    17.003] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
98:[    17.003] (II) Module nvidia: vendor="NVIDIA Corporation"
137:[    17.712] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
177:[    18.033] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
306:[    20.305] (II) NVIDIA(0): Setting mode "TV-0: nvidia-auto-select @1024x768 +0+0 {ViewPortIn=1024x768, ViewPortOut=1024x768+0+0}"
307:[    20.473] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1680x1050 +1024+0 {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0}, TV-0: nvidia-auto-select @1024x768 +0+0 {ViewPortIn=1024x768, ViewPortOut=1024x768+0+0}"
322:[    25.318] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1680x1050 +1024+0 {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0}"
323:[    25.454] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1680x1050 +1024+0 {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0}, TV-0: nvidia-auto-select @1024x768 +0+0 {ViewPortIn=1024x768, ViewPortOut=1024x768+0+0}"
372:[  9415.147] (II) NVIDIA(0): Setting mode "TV-0: nvidia-auto-select @1024x768 +0+0 {ViewPortIn=1024x768, ViewPortOut=1024x768+0+0}"
374:[  9415.505] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1680x1050 +0+0 {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0}"
380:[  9421.596] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1680x1050 +1024+0 {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0}"
381:[  9421.699] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1680x1050 +1024+0 {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0}, TV-0: nvidia-auto-select @1024x768 +0+0 {ViewPortIn=1024x768, ViewPortOut=1024x768+0+0}"
387:[  9537.188] (II) NVIDIA(0): Setting mode "DPY-2:nvidia-auto-select+0+0,DPY-3:nvidia-auto-select+1024+0"
393:[  9567.554] (II) NVIDIA(0): Setting mode "DPY-2:nvidia-auto-select+1680+0,DPY-3:nvidia-auto-select+0+0"
scott@scott-P5QC:~$ 


```

---

### Post by sdowney717 on 2014-02-23
```
9421.699] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1680x1050 +1024+0 {ViewPortIn=1680x1050, ViewPortOut=1680x1050+0+0}, TV-0: nvidia-auto-select @1024x768 +0+0 {ViewPortIn=1024x768, ViewPortOut=1024x768+0+0}"
```

I see its loading TV-0 left of DVI-I-1

And this is contrary to xorg.conf

---

