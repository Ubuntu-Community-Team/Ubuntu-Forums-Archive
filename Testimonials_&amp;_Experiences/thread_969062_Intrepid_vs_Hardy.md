---
title: "Intrepid vs Hardy"
date: 2008-11-03
forum: Testimonials &amp; Experiences
---

### Post by scourge on 2008-11-03
I've been using Ubuntu since 2005, and upgrading every six months. Every time things seem to work a little bit better than previously, and so far that has also been the case with 8.10 64-bit.


Improvements I've noticed:

- Hardy 64-bit had a serious bug in the VGA (Vesa) driver which caused the graphical boot screen to not work. That's fixed now.
- So far nspluginwrapper hasn't dropped connection to the Flash plugin. With Hardy this happened constantly, forcing me to restart the browser.
- With Hardy I had to change the nVidia driver's and Compiz Fusion's settings to get rid of the tearing in videos and even general desktop use. No more.
- The GTK theme looks more mature.
- The key ring is used more, for example in Evolution. This eases the hassle with passwords.

The minor disappointments:
- The Flash plugin didn't install correctly when Firefox tried to do it. I had to go to the command line, purge the nspluginwrapper and flashplugin-free packages, and reinstall them.
- No Open Office 3.0. I guess it was too late to include it.


Overall I'm happy. All my hardware works like it's supposed to, but then again I've chosen every component of my PC with Linux in mind, so that was expected. There are a lot of people installing Ubuntu on some crappy ancient laptop with a shiny "Designed for Windows 98" sticker next to the touch pad, and then they come here to complain that Ubuntu sucks because their Winmodem doesn't work. If you're truly interested in experiencing the real Ubuntu, you should try it on supported hardware.

---

### Post by ukripper on 2008-11-03
> **scourge said:**
> 

- So far nspluginwrapper hasn't dropped connection to the Flash plugin. With Hardy this happened constantly, forcing me to restart the browser.


Flash 10 works just fine with Hardy 64-bit too using nspluginwrapper. I had no problem using it with firefox 3.0.3, so far no crashes using Intel X3100 graphics card. Flash 10 and 9 always been stable for me on FF 3 but not on FF2

---

### Post by tuxxy on 2008-11-03
> **scourge said:**
> I've been using Ubuntu since 2005, and upgrading every six months. Every time things seem to work a little bit better than previously, and so far that has also been the case with 8.10 64-bit.


Improvements I've noticed:

- Hardy 64-bit had a serious bug in the VGA (Vesa) driver which caused the graphical boot screen to not work. That's fixed now.
- So far nspluginwrapper hasn't dropped connection to the Flash plugin. With Hardy this happened constantly, forcing me to restart the browser.
- With Hardy I had to change the nVidia driver's and Compiz Fusion's settings to get rid of the tearing in videos and even general desktop use. No more.
- The GTK theme looks more mature.
- The key ring is used more, for example in Evolution. This eases the hassle with passwords.

The minor disappointments:
- The Flash plugin didn't install correctly when Firefox tried to do it. I had to go to the command line, purge the nspluginwrapper and flashplugin-free packages, and reinstall them.
- No Open Office 3.0. I guess it was too late to include it.


Overall I'm happy. All my hardware works like it's supposed to, but then again I've chosen every component of my PC with Linux in mind, so that was expected. There are a lot of people installing Ubuntu on some crappy ancient laptop with a shiny "Designed for Windows 98" sticker next to the touch pad, and then they come here to complain that Ubuntu sucks because their Winmodem doesn't work. If you're truly interested in experiencing the real Ubuntu, you should try it on supported hardware.

I agree its a worth update to Hardy, to comment on Flash on Hardy 64-bit it ran fine for me too but is yet to even crash once on Ibex, if you do experience a crash simply close nsplugin process listed in system monitor and you should not need to restart browser then :)

---

### Post by scourge on 2008-11-03
> **tuxxy said:**
> I agree its a worth update to Hardy, to comment on Flash on Hardy 64-bit it ran fine for me too but is yet to even crash once on Ibex, if you do experience a crash simply close nsplugin process listed in system monitor and you should not need to restart browser then :)

Good to know. Flash 9 on Hardy treated me like a dog. Sometimes refreshing the page would show the video, but too often I had to restart the whole browser. Flash 10 is definitely better. But still, Adobe, I want my 64-bit Flash plugin!

---

### Post by tuxxy on 2008-11-03
> **scourge said:**
> Good to know. Flash 9 on Hardy treated me like a dog. Sometimes refreshing the page would show the video, but too often I had to restart the whole browser. Flash 10 is definitely better. But still, Adobe, I want my 64-bit Flash plugin!

hehe dont we all! not long to go now though bring it on!

---

### Post by scourge on 2008-11-03
> **tuxxy said:**
> hehe dont we all! not long to go now though bring it on!

[quote=Adobe]We expect to provide native support for 64-bit platforms in an upcoming release of Flash Player following Flash Player 10.[/quote]

Interesting choice of words. My English is a bit lacking, so I'm not sure what to make of it. Do you interpret "in an upcoming release" as the next release, or just some future release after Flash 10?

---

### Post by Sef on 2008-11-03
>  No Open Office 3.0. I guess it was too late to include it.

Yes, that is correct.  It should be available through the backports in after 3.01 gets released from what I read or you can open the Terminal and then paste or type this command:

```
gksudo gedit /etc/apt/sources.list
```

then add these two lines:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

---

### Post by maks_zbogar on 2008-12-16
If "tracker" is important to you and you use Evolution, there is a problem as new version of Evolution in Intrepid use mysql and Tracker can't index your emails anymore... Also "Mail notification" doesn't work in Intrepid Ibex for me.

---

