---
title: "[Xubuntu] horray and some gripes"
date: 2007-04-25
forum: Testimonials &amp; Experiences
---

### Post by jojo4u on 2007-04-25
I define myself a sort of power user with an emphasis to easy of use and convinience. In oder to boot from USB including S3 standby and in the long term avoiding Vista, I came from XP to Ubuntu. I wanted a Debian based cutting edge distro with a large user base :)
Since my USB stick only has 4 GB I decided to use **Xubuntu**. After all the days of configuring and tweaking I can say that I'm content with Ubuntu. But a little bit of disappointment stays since I cannot understand why such a big distro does not emphazises more on user-experience:

1. Fonts look terrible with antialiasing disabled.
You can come by this by installing MS fonts but it needs some tweaking of fonts.conf and Xressources. Definitely not for the beginner. And after all, fonts are still not as superbly hinted as with Windows XP, which is an small annoyance with webpages. Perhaps some DPI issue (X: 72 dpi, Xft: 96 dpi).

2. (At least Xubuntu:Edgy) did not go to higher than a refresh rate of 85 Hz (i810, 1024x768)  without command-line modelintes. And the default after installation was even lower. Come on, this is 2007. Perhaps a DDC-related issue.

3. Open-Office in Edgy was pratically unusable because of ugly fonts.

3. No mouse speed adjustment possible in GUI. There's only a slider for accleration.

4. DHCP needs command-line hacking in order to announce my hostname to my router. This feature allows me to use names instead of IPs on my local LAN.

5. All the rest: no multi-core optimation for compiling activated (stability?), larger-than-necessary meta-packets (Eclipse!), some i810 issues (of course that's upstream).

All I appreciate your work. But not ready for the desktop yet ;) But Ubuntu is not the best distro for install-and-forget anyways. So let's become it! But don't forget to maintain good configurability.

---

### Post by kerry_s on 2007-04-25
Oh yeah, will build it to your needs right away. Not!

I don't have any of those problems. Sounds like your creating your own problems, why would you disable antialiasing?

Sounds your not ready for linux.

---

### Post by jojo4u on 2007-04-25
> **kerry_s said:**
> I don't have any of those problems. Sounds like your creating your own problems, why would you disable antialiasing?


Well, depends on your taste isn't it? My crappy 19" CRT and onboard VGA provide free antialising by being unsharper than your (guessed) TFT.

---

### Post by kerry_s on 2007-04-25
> **jojo4u said:**
> Well, depends on your taste isn't it? My crappy 19" CRT and onboard VGA provide free antialising by being unsharper than your (guessed) TFT.

No i only have crt's, gateway vx920 running at 1600x1200.

Have you tried running> sudo dpkg-reconfigure fontconfig-config

---

### Post by jojo4u on 2007-04-25
> **kerry_s said:**
> No i only have crt's, gateway vx920 running at 1600x1200.
Have you tried running> sudo dpkg-reconfigure fontconfig-config

Well, of course I might be too much used to Windows. I tried all 4 permutations of Msttcorefonts/Bitstream and aliased/antialiased. Results see attachments. You see how much Bitstream sucks without antialiasing (and how much Msttcorefonts suck with antialiasing ;)). This is BCI on and autohinter off (fontconfig-config).
So, comparing Bitstream aliased against Msttcorefonts antialiased I prefer the second. Antialiasing gives an impression of unclearness and lower contrast as more grey is involved. The other two pictures show Verdana and Trebuchet with ugly artifacts not found in Windows.
Your file is JPG which doesn't represent you desktop 100 %. But thanks for bringing it up, I have evidence now, that Bitstream + antialiasing is quite good.

```

pictures: aliased Bitstream / aliased MS / antialiased Bitstream / antialiased MS

```

---

### Post by kerry_s on 2007-04-25
yeah, some those font screen shoots look f'ugly.here's a png->

---

### Post by jojo4u on 2007-04-25
> **kerry_s said:**
> yeah, some those font screen shoots look f'ugly

You are using sub-pixel hinting. Is this intentional? I'm unter the impression that it's only useful on LCD screens.

```

Some part of you PNG, zoomed

```

---

### Post by kerry_s on 2007-04-26
I used> sudo dpkg-reconfigure fontconfig-config
I choose native, autohint, no. I use the stock ones in firefox and i use verdana for most of my desktop. I'm using fluxbox so i have more control over the size of my fonts in all the different parts then you would have in gnome.

---

### Post by jojo4u on 2007-04-26
> **jojo4u said:**
> And after all, fonts are still not as superbly hinted as with Windows XP, which is an small annoyance with webpages.


I got that fixed. See Bug [#110422]("https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/110422")

---

### Post by trooperchix on 2007-10-23
> **kerry_s said:**
> No i only have crt's, gateway vx920 running at 1600x1200.

Have you tried running> sudo dpkg-reconfigure fontconfig-config


Dood, tell me how you got your Gateway VX920 running right?  I just can't get that bugger configured right and I only have 800 x 600 and 600 x 400 available...  What driver are you using for it?  I have Cirrus video cards which as far as I can tell, are configured ok (identified upon install as Cirrus).  I'm running Gutsy right now...

I'll love you forever man!!

:guitar:

---

### Post by trooperchix on 2007-10-24
> **trooperchix said:**
> Dood, tell me how you got your Gateway VX920 running right?  I just can't get that bugger configured right and I only have 800 x 600 and 600 x 400 available...  What driver are you using for it?  I have Cirrus video cards which as far as I can tell, are configured ok (identified upon install as Cirrus).  I'm running Gutsy right now...

I'll love you forever man!!

:guitar:

Figured it out, had more to do with my mobo than monitor..  view thread: [http://ubuntuforums.org/showthread.php?t=588067](http://ubuntuforums.org/showthread.php?t=588067)

---

