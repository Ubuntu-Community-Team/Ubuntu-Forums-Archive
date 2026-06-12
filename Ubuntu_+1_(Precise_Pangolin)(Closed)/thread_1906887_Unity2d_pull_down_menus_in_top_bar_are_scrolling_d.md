---
title: "Unity2d pull down menus in top bar are scrolling despite large monitor"
date: 2012-01-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-01-10
Hello All

**Unity 2d in 12.04** on my test box has taken to scrolling the pull down menus in applications that integrate with Unity global menu (e.g. gedit, firefox but not libreoffice). See attached small screen grab for an example.

The visible length of the menu seems to be decided by some kind of algorithm as its different for different lengths of menu. This scrolling also occurs on the indicator menus.

**The effect does not occur on Unity 3d or on gnome shell, nor is it present in an up to date 11.10 install.**

Is this a planned mandatory feature of Unity 2d, or a bug of some kind? Is there a way of switching off this feature?

This testing box has Gnome Shell and gnome-fallback-session installed.

Does anyone else see this behaviour in Unity 2d or have I been messing around with this test box too much :twisted:

---

### Post by lucazade on 2012-01-10
in /usr/share/themes/Ambiance/gtk-3.0/settings.ini  (or Radiance for the light theme)
disable the automnemonics setting:

gtk-auto-mnemonics = 0

then logout/login

---

### Post by keithpeter on 2012-01-10
> **lucazade said:**
> in /usr/share/themes/Ambiance/gtk-3.0/settings.ini  (or Radiance for the light theme)
disable the automnemonics setting:

gtk-auto-mnemonics = 0

then logout/login

Hello lucazade

Thanks for that suggestion, but changing the setting has no effect on the pull down menus in the top bar: they still scroll.

In the 11.10 installation, gtk-auto-mnemonics = 1 is the setting, and the menus *don't *scroll. 

I'd also emphasise that this affects Unity 2d only, Unity session still has proper full length menus, so its the Unity 2d specific settings I'm looking at I suppose.

I'll start googling in earnest. I do hope this *is* just a change in a default setting somewhere and not a 'feature'.

---

### Post by lucazade on 2012-01-10
> **keithpeter said:**
> Hello lucazade

Thanks for that suggestion, but changing the setting has no effect on the pull down menus in the top bar: they still scroll.

In the 11.10 installation, gtk-auto-mnemonics = 1 is the setting, and the menus *don't *scroll. 

I'd also emphasise that this affects Unity 2d only, Unity session still has proper full length menus, so its the Unity 2d specific settings I'm looking at I suppose.

I'll start googling in earnest. I do hope this *is* just a change in a default setting somewhere and not a 'feature'.

ah.. too bad.
that automnemonics settings usually removed scroll arrows in menu in classic gnome (i.e. recent items).
it looks like the indicator-appmenu, in this case, doesn't follow this setting.

---

### Post by ventrical on 2012-01-10
yep!!!... I got it here on my Viewsonic monitor widescreen.

They will scroll down but will not scroll back up.

---

### Post by keithpeter on 2012-01-10
> **ventrical said:**
> yep!!!... I got it here on my Viewsonic monitor widescreen.

They will scroll down but will not scroll back up.

Hello ventrical

Thanks for confirming that this is a real 'feature' and not me messing about with different desktop environments causing a setting collision.

I'm downloading the Jan 10th 'daily' to run a fresh live session and if the scrolling menus are still in the Unity 2d session and not the Unity 3d session, I'll file a bug

Thanks all.

You can see this in a live session, so filed [bug #914255]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/914255")

---

### Post by ventrical on 2012-01-10
I thinks it is a 3.2.0-8 kernel prob because It works fine on 3.2.0-7.

But this is on a Nvidia GE218. The other (with the bug)is the Intel graphics card which is why I installed xubuntu and lubuntu desktops.on that install.

---

### Post by lucazade on 2012-01-10
ventrical, ventrical... 
how a gtk issue can be related to the kernel??!?!

by empathy, radiation or by sympathy?

:D

---

### Post by ventrical on 2012-01-10
> **keithpeter said:**
> Hello ventrical

Thanks for confirming that this is a real 'feature' and not me messing about with different desktop environments causing a setting collision.

I'm downloading the Jan 10th 'daily' to run a fresh live session and if the scrolling menus are still in the Unity 2d session and not the Unity 3d session, I'll file a bug

Thanks all.

You can see this in a live session, so filed [bug #914255]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/914255")


  If this is relevant to your bug you have my permission to insert it into your report.

[http://www.youtube.com/watch?v=IWNMBX87UhI](http://www.youtube.com/watch?v=IWNMBX87UhI)

---

### Post by ventrical on 2012-01-10
> **lucazade said:**
> ventrical, ventrical... 
how a gtk issue can be related to the kernel??!?!

by empathy, radiation or by sympathy?

:D

no, no .... sorry .. I forgot to edit it out ..  your right .. not a kernel prob.. I was just experimenting on the fly :)

---

### Post by ventrical on 2012-01-10
Ok.. I added the link to your report.

---

### Post by keithpeter on 2012-01-10
Hello All

Thanks everyone for spending time on behalf of us 2d folk.

[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/913237](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/913237)

I marked the bug as a duplicate of the one above, which has been assigned.

---

