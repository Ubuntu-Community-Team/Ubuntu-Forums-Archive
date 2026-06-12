---
title: "ATi Catalyst 9.7 released"
date: 2009-07-24
forum: The Cafe
---

### Post by Pasdar on 2009-07-24
Anyone try it out already?

**    New Features**

    This release of ATI Catalyst Linux introduces support for the following new operating systems:

        * RedFlag DT 7.0 production support

**    Resolved Issues**

        * X segmentation fault no longer occurs after applying reflections or rotations on some systems that support Xrandr 1.2 or higher
        * Catalyst Control Center hot plugging a secondary display no longer causes screen corruption in clone mode
        * Monitor are now disabled after removing the secondary display when system is in standby
        * Some systems now report CrossFire adapters available during driver re-install
        * On some multi-monitor configurations disabling one display no longer causes both displays to become disabled
        * X Server does not intermittently fail to start on some multi adapter configurations
        * Executing xrandr --prop no longer causes Ubuntu 9.04 X Server to stop responding
        * [Ubuntu 9.04] Segmentation fault no longer occurs with X server Xinerama is enabled
[B]
    Known Issues[/B]

        * Toggling between terminals may cause the system to become unresponsive
        * Catalyst Control Center Display Manager may fail to display HDTV PAL modes
        * The mouse cursor may fail to switch between primary and secondary display in some dual-head configurations
        * &#8220;aticonfig -xinerama=o&#8221;n may result in different dimension and dpi settings between Ubuntu 8.10 and 9.04
        * RandR 1.2 specifying Rotate in xorg.conf may cause X startup to fail
        * The mouse cursor may show incorrect rotation and position on some systems with large desktop enabled
        * Removing secondary display may cause the login screen to appear on the ghost monitor
        * Moving the mouse cursor between two displays may show a the cursor on both displays simultaneously
        * System may stop responding when running Return to Castle Wolfenstein

Download: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-7-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-7-x86.x86_64.run)

---

### Post by days_of_ruin on 2009-07-24
I didn't know it was out. *runs to install it*

---

### Post by days_of_ruin on 2009-07-24
Wow compiz is a lot smoother!
Moving windows still have a little bit of tearing, but it significantly
smoother:D

---

### Post by MaxIBoy on 2009-07-24
Sweet genius, I'm all OVAH that baby!

That was my stupid phrasing for the week. Sometimes you have to get it out of your system.

---

### Post by Pasdar on 2009-07-24
> **days_of_ruin said:**
> Wow compiz is a lot smoother!
Moving windows still have a little bit of tearing, but it significantly
smoother:D

How about things like maximize/minimize window, etc? did they solve the delay problem? Also how about video playback?

---

### Post by rocknrolf77 on 2009-07-24
I'm still pretty skeptical that everything goes to hell when upgrading. Maybe it's better in ubuntu with an older kernel than in arch. Testing in ubuntu first and see what people say about 9.7 in arch after a couple of days.

---

### Post by days_of_ruin on 2009-07-24
> **Pasdar said:**
> How about things like maximize/minimize window, etc? did they solve the delay problem? Also how about video playback?

Minimize is fast, unminimizing is slow as is maximize.
As for video, totem start up slow but then plays video fine :), just don't minimize the window:(

---

### Post by DougieFresh4U on 2009-07-24
Will it work with the .31.4 kernel?
Also, sorry for the stupid question, but once I download it, how do I run it? Not good with these kind of files  yet.

---

### Post by snargfish on 2009-07-24
Awwwww poor ATI users with your third-world drivers :P

---

### Post by days_of_ruin on 2009-07-24
> **snargfish said:**
> Awwwww poor ATI users with your third-world drivers :P

Don't rub it in wise@$$.

---

### Post by snargfish on 2009-07-24
> **days_of_ruin said:**
> Don't rub it in wise@$$.

Rofl :P:P:P:P:P

---

### Post by ELD on 2009-07-24
> **snargfish said:**
> Awwwww poor ATI users with your third-world drivers :P

Bring on Christmas monies to go back to nvidia for me!

---

### Post by lethalfang on 2009-07-24
> **snargfish said:**
> Awwwww poor ATI users with your third-world drivers :P

*smack* [IMG]http://www.clipartof.com/images/emoticons/xsmall2/743_gangster_shooting_a_machine_gun.gif[/IMG]

---

### Post by snargfish on 2009-07-24
> **lethalfang said:**
> *smack* [IMG]http://www.clipartof.com/images/emoticons/xsmall2/743_gangster_shooting_a_machine_gun.gif[/IMG]

Where's the love?

---

### Post by Pasdar on 2009-07-25
> **DougieFresh4U said:**
> Will it work with the .31.4 kernel?
Also, sorry for the stupid question, but once I download it, how do I run it? Not good with these kind of files  yet.

It's only compatible with Ubuntu 9.04 kernel. Once you've downloaded it, type the following in terminal:

chmod +x filename.run
then
./filename.run

and it will start the installation.

---

### Post by Pasdar on 2009-07-25
ATI is getting there.

You guys seem to forget that NVIDIA drivers were just as horrible before 180 release not long ago.

---

### Post by lethalfang on 2009-07-25
> **Pasdar said:**
> ATI is getting there.

You guys seem to forget that NVIDIA drivers were just as horrible before 180 release not long ago.

A man can always dream....... :D

---

### Post by snargfish on 2009-07-25
> **Pasdar said:**
> ATI is getting there.

You guys seem to forget that NVIDIA drivers were just as horrible before 180 release not long ago.

No they weren't.

---

### Post by lethalfang on 2009-07-25
> **DougieFresh4U said:**
> Will it work with the .31.4 kernel?
Also, sorry for the stupid question, but once I download it, how do I run it? Not good with these kind of files  yet.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf)

---

### Post by stwschool on 2009-07-25
> **lethalfang said:**
> [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf) surely?

---

### Post by stwschool on 2009-07-25
> **stwschool said:**
> [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf) surely?
Wow that was pain-free. Normally when I try to upgrade my gfx driver other than through Jockey I end up killing my computer! And first impressions are very good. It's much friendlier with compiz now by the looks of things (I successfully fired up a video and used scale, no flickering, crapness or weirdness).

---

### Post by days_of_ruin on 2009-07-25
Woah weird bug/glitch with 9.7 and firefox 3.5/Shiretoko:
[http://www.ubuntu-pics.de/bild/19950/screenshot_011_A3S376.png]("http://www.ubuntu-pics.de/bild/19950/screenshot_011_A3S376.png")


Notice how firefox 3.0 renders it correctly.

---

