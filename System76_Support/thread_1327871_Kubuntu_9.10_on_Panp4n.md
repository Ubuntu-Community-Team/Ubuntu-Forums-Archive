---
title: "Kubuntu 9.10 on Panp4n"
date: 2009-11-15
forum: System76 Support
---

### Post by 3Miro on 2009-11-15
Hi Everyone,

I decided to share my experience. I got my Pangolin almost a year ago and it came with Ubuntu 8.10. I feel Gnome is getting outdated, so I decided to switch to KDE (after having used it on my desktop). I know that system76 doesn't officially support KDE, but I decided to post this anyway:

Sound, Video, 3D Video, Keyboard + Shortcuts, Touchpad + USB Mouse all work.

Camera and Mic also work for Skype.

WiFi and Wired network both work. KDE Network Manager can use some work, but does the job fine enough.

Kwin 3D cube is a bit more jittery (when switching desktops), then Gnome + Compiz, but this might be because of the different wallpapers on each desktop. It just doesn't cash them all in memory. I will see if I can fix that.

Virtual Box + USB support works (I had to add myself to the ld group for printing, but this was minor VB issue). Tested it with Windows guest only.

Suspend and Hibernate work, however, more testing is needed to see if stability will suffer if we use too many suspend-resume cycles.

I installed the System76 driver, however, everything seemed to be working without it anyway. I am not sure if it actually provides any drivers for my specific laptop or is it just a log creating tool.

I observed the AC power bug. The laptop doesn't recognize when the AC cord is plugged and doesn't switch to performance mod. Luckily KDE has a nice widget so that I can manually control this with couple of clicks. Battery level is measured, but battery time is not. I posted on one of the other treads. I will try to recompile the kernel to see if it will have an effect.

Another odd bug is that upon boot, sometimes the log in menu will not appear. Or it will appear for a split second and then the splash screen will show up. I have never observed this on my non Sys76 desktop. Ctr+alt+F1, then killall Xorg, then startx fixes the issue. I will see if the splash screen settings would prevent it from happening. The bug random, so testing is not very easy.

I have not tested the fingerprint reader, I just don't use it.

---

### Post by abulluck on 2009-11-16
Cool.  Keep us updated as I may try out Kubuntu 9.10 soon on my panp4.

---

### Post by 3Miro on 2009-11-16
I found something like a work around on the AC Adapter bug here:

[http://ubuntuforums.org/showthread.php?t=1328735](http://ubuntuforums.org/showthread.php?t=1328735)

Please read carefully.

The Log In screen problems seems to have been improved by changing the splash screen theme. 3 reboots showed no problem, however, more testing is needed.

---

### Post by thomasaaron on 2009-11-17
> I feel Gnome is getting outdated

So do the devs. Here are some screenshots of what may be the future of gnome. I've been using it for a couple of weeks and am addicted...

[http://live.gnome.org/GnomeShell/Screenshots](http://live.gnome.org/GnomeShell/Screenshots)

---

### Post by 3Miro on 2009-11-17
> **thomasaaron said:**
> So do the devs. Here are some screenshots of what may be the future of gnome. I've been using it for a couple of weeks and am addicted...

[http://live.gnome.org/GnomeShell/Screenshots](http://live.gnome.org/GnomeShell/Screenshots)

Interesting, I thought they gave up on the idea of introducing too many new features. Good to know they are not waisting time.

It also looks like they integrated some effects in metacity.

---

### Post by Lee_Machine on 2009-11-17
Yeah, I'm wondering how many of these new features of GNOME 3.0 will be in 2.30.0, and what ones are being held off until GNOME 3.0.

For those that didn't know the release of GNOME 3.0 was pushed until September 2010.

I see this as a good thing, to try and, not repeat KDE 4.0 

 
[http://www.osnews.com/story/22477/GNOME_3_0_Pushed_Back_Six_Months](http://www.osnews.com/story/22477/GNOME_3_0_Pushed_Back_Six_Months)

---

### Post by thomasaaron on 2009-11-18
I think the next version of Ubuntu will be a LTS version. It'll be interesting to see if they think it is a good idea to make such a radical change on an LTS version.

Frankly, I've been using for a while, and now I can't live without it. It's really good for productivity.

---

### Post by 3Miro on 2009-11-19
Today I removed kubuntu and reinstalled ubuntu 9.10. My reasons were:

1. The 3D effects under KDE were not what they should have been. The thing was too jittery, when I added a few of them. Compiz never had this issue, nor does my KDE desktop. In any care, it was bothering me.

2. My wife got very used to Gnome and this is now technically her laptop.

Interestingly, the AC power bug doesn't appear. I cannot see time estimates on the battery life, however, I can clearly see AC in - AC out.

---

### Post by lnxguit on 2010-02-22
I tried to set up "kde-full" on my Pangolin P5 yesterday. Everything worked great except for the kde power manager - it would not recognize that my ac adapter was plugged in.

---

