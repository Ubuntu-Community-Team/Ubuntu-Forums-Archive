---
title: "LightDM and Use wallpaper if available not working"
date: 2016-04-02
forum: Ubuntu Development Version
---

### Post by makitso on 2016-04-02
OK, so I have 4 systems that are running xubuntu 16.04 and all configured about the same, and all use the Variety wallpaper changer.
So, I want the LightDM login screen to use the wallpaper that the user sees when logged in, not a specific graphic or color.  

All systems have the LightDM GTK Greeter setting the same.  However,  on1 of the 4 systems this work correctly.  However, on the other three systems the wallpaper shows up for an instant and then the Image selected.

I have looked high and low for what might be causing this problem.  

So my question is,  how does one configure the lightdm-gtk-greeter.conf file to make this happen

So when I log into any of the three systems that do not work they all behave the same.  First you get the blue background for a second or two and then you seen the correct wallpaper for about 5 seconds and then it reverts back to the blue background again.

---

### Post by justen_m on 2016-04-03
I'm running straight Ubuntu 16.04LTS Beta and use unity-greeter, but also use Variety(0.6.0), on 5 systems. 1 wouldn't show my wallpaper on the login screen. It would quickly flash it, then it would disappear to the default image. Its problem? Under accessibility options, I had high-contrast selected (not sure how that happened). Simple as that for me, but don't know if it can happen with your setup.

---

### Post by makitso on 2016-04-03
So, I did a clean install on a Thinkpad T60 of the daily build xubuntu 16.04.  The problem I see with the LightDM Gtk+ Greeter is that on this install when you log out you get the blue screen even if a wallpaper is selected.  On a boot it is OK in that the blue screen shows for a second and then the wallpaper.  Tried the same thing on Virtualbox and that works correctly on either a boot or logout/login.  So, its a minor point and am not going to waste any more time on it.

---

