---
title: "Chromium 7 hardware acceleration"
date: 2010-10-04
forum: The Cafe
---

### Post by Iksf on 2010-10-04
Hey all, just want to check with other linux Chromium 7 users, if you load it with the --enable-accelerated-2d-canvas flag and stick it at [http://demos.hacks.mozilla.org/openweb/HWACCEL]("http://demos.hacks.mozilla.org/openweb/HWACCEL/")/

Do you get stupidly insane performance. All iv been hearing recently is Firefox and IE9 arguing about whos faster, and on Windows 7 one of them does seem to be faster, but on Linux Chromium seems faster than any Windows, Linux, or Mac browser by a stupid amount. 

Simply put i have Chromium pulling over 300fps on that test on a laptop.

---

### Post by Dustin2128 on 2010-10-04
> **Iksf said:**
> 
Simply put i have Chromium pulling over 300fps on that test on a laptop.
At some point it just ceases to matter.. your screen can only refresh so fast. Still, its awesome.

---

### Post by Dragonbite on 2010-10-04
Holy crap!

---

### Post by sdowney717 on 2010-10-04
for me, 19 versus 4 fps
I get 36 on firefox
[http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/61416/](http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/61416/)

got it from here

---

### Post by ubuntu27 on 2010-10-04
I get 22 FPS with [Rekonq browser]("http://rekonq.sourceforge.net/") version 0.6.0 (Using KDE Development Platform 4.5.1)

35 FPS with Mozilla Firefox 3.6.10 (Mozilla/5.0 (X11; U; Linux x86_64; en-US;)

---

### Post by NightwishFan on 2010-10-04
28 FPS on Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10

Intel GPU.

---

### Post by Frogs Hair on 2010-10-04
Namoroka-38 Minefield FF4 beta 4-48 IE9 beta-60 (Opera doesn't work with the test)

---

### Post by kerry_s on 2010-10-04
:lolflag: i didn't want to stop my torrent, so i got a sad 2.

---

### Post by Noz3001 on 2010-10-04
> **kerry_s said:**
> :lolflag: i didn't want to stop my torrent, so i got a sad 2.

How would your torrent affect anything?

---

### Post by JBAlaska on 2010-10-04
On the daily Chromium build, I get 19FPS without hardware Accel, 32FPS with, and 42FPS on Firefox 3.6.10

---

### Post by kerry_s on 2010-10-04
> **Noz3001 said:**
> How would your torrent affect anything?

it's using most of the connection for download. i would have to throttle it more for vids or streaming stuff like that test.

---

### Post by Dragonbite on 2010-10-04
> **kerry_s said:**
> :lolflag: i didn't want to stop my torrent, so i got a sad 2.

I got that without a torrent even installed!

---

### Post by CharlesA on 2010-10-04
Gogo 18 fps with firefox.

---

### Post by oobuntoo on 2010-10-05
73 FPS with firefox 3.6.10, 6 FPS with Chromium 6.0.472.63

---

### Post by Khakilang on 2010-10-05
I got 12fps on Firefox 3.6.10. Compare with others this is miserable. Don't know whether it is time to upgrade my Graphics card?

---

### Post by NightwishFan on 2010-10-05
Actually it is probably normal. Unless you do things that need intense real-time 3d, I think you will be fine. Midori (Gtk Webkit) on my card gets 10fps, and Firefox did less than 30fps on subsequent results. I can play Urban Terror easily on this machine.

---

### Post by lovinglinux on 2010-10-05
> **Khakilang said:**
> I got 12fps on Firefox 3.6.10. Compare with others this is miserable. Don't know whether it is time to upgrade my Graphics card?

I get 8. Anyone knows which cards are supported?

@Iksf

Looks to me most users are reporting better speeds in Firefox.

---

### Post by del_diablo on 2010-10-05
12 FPS running Opera in laptop with shitty CPU.
Got 6 FPS on a old Intel Atom revision O.o

---

### Post by Linye on 2010-10-05
Minefield 4.0b7pre   26fps

Chromium 7.0.541.0 (61160)   15fps first and 25fps after enabling hardware acceleration

---

### Post by Iksf on 2010-10-06
Im using Nvidia 330M GT, which is somewhere in the Nvidia 230 GT series equiv. You need to be using chromium 7, there was only minimal development for HW accel in the 6 series. Im using daily snapshots from chromium buildbot, nvidias current stable blobs

Know many people have said (for windows version) to enable

--enable-accelerated-compositing

this actually massivly slowed it for me

im using just

--enable-accelerated-2d-canvas

---

### Post by renkinjutsu on 2010-10-06
Holy crap! I got 18 fps will no accel, and i got 97 fps will accel!

using Nvidia 8600GT with Nouveau+Gallium

---

### Post by Iksf on 2010-10-06
> **renkinjutsu said:**
> Holy crap! I got 18 fps will no accel, and i got 97 fps will accel!

using Nvidia 8600GT with Nouveau+Gallium

With Nouveau?!?!?!

Damn thats promising

---

### Post by MJWitter on 2010-10-06
Hmmm,

90 in firefox 4 (Minefield)
71 in firefox 3 (Namoroka)
189 in Chromium 7 (with or without acceleration flags)

---

### Post by renkinjutsu on 2010-10-07
> **Iksf said:**
> With Nouveau?!?!?!

Damn thats promising

Yup! Right now i'm using the nouveau xf86 driver version 0.0.16 (the one i have installed is dated 2010-8-19) and mesa version 7.8.2

I didn't think the HW acceleration would work, but wow, that's amazing

---

### Post by Jesus_Valdez on 2010-10-07
20 fps with Firefox 3.6 and 8 using Midori.

I think I'm Ok with this.

---

### Post by Lucradia on 2010-10-08
I got 15 FPS on Firefox 3.6.10 under Windows 7 64-bit. :( nvidia GTX 470.

---

### Post by Iksf on 2010-10-08
Everyone saying unaccelerated browsers dont :D

Firefox 4
Chrome 7
IE9
Probably some dev release of Opera (/dont care)

Not Firefox 3, Midori (legend browser imo), rekonq etc

---

