---
title: "Make wine have less lag or none at all?"
date: 2011-04-29
forum: Wine
---

### Post by linuxmaniack on 2011-04-29
I have got Command And Conquer: The First Decade (i use it for C&C renegade) On wine and it is so and it has a lot of lag. I have reduced the settings to as low performance at is can go and it is still has lag. Is it possible to do it? Will it work better on playonlinux? 

Thanks

---

### Post by _outlawed_ on 2011-04-29
Running games under Wine is limited to the current version of Wine you are using, and the settings used ingame. But mostly, it's limited to your hardware. If you have low-spec hardware, expect poor results.

And PlayOnLinux is only a support application designed to assist in installations, nothing more.

---

### Post by linuxmaniack on 2011-05-01
i have a vary high spec pc...

---

### Post by Dlambert on 2011-05-01
Acording to your signiture. No you dont

---

### Post by Tweak42 on 2011-05-02
> **linuxmaniack said:**
> i have a vary high spec pc...

For an old game like C&C Renegade your cpu should be plenty fast, however your Radeon video could be limiting you because of poor 3D drivers.  Try both the open and the catalyst drivers, or switch to a nvidia card.  Also try different wine versions (older and beta).  

There aren't enough reports to see what hardware works, but there is a ATI fix mentioned here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=910](http://appdb.winehq.org/objectManager.php?sClass=version&iId=910)

---

### Post by bobwyajnr on 2011-05-02
> **Dlambert said:**
> Acording to your signiture. No you dont
[COLOR="Navy"]
I think it's more a case of the "hardware is willing but the drivers aren't"... :) I really feel for people who bought 3xxx hardware (especially high-end cards) though - who could know what ATI had up it's sleeve with the 4xxx series![/COLOR]


@**linuxmaniack**

I would refer to section (9) Performance on this WINE HQ page:
[WineHQ Performance FAQ]("http://wiki.winehq.org/FAQ#head-2dddc6846f36407f3eb660910033e0ec2f5a3a66")
**WINEDEBUG=-all** can be added before the shortcut for your game to stop it trying to write pointless debugging messages to the (global TTY) console.

Get the latest, most bleeding-edge, unstable ATI 11.x Catalyst drivers you can! I know on my laptop's HD 4650M card things have slowly improved. Generally things are working as well - 3D gaming+full desktop effects - as my older Nvidia cards (8800 GTX's). I didn't find the latest AMD/ATI drivers too hard to install straight from their website (which is a big change!)

[The Open Source ATI drivers are no where near as mature for 3D performance so don't bother with these (yet!) Only really needed if you have an older <2xxx card...]("http://www.phoronix.com/scan.php?page=article&item=amd_radeon_histq111&num=1")

Team green graphics cards to match the ATI HD3870 performance are reasonably affordable. Although the Nvidia 460 cards don't have the powersaving features of the 5xx series they have good price/performance.


Make sure you switch to MetaCity (i.e. don't have Compiz running) before running your game, etc. All the usual rules performance tweaks apply!


Also I have recently striped out pulseaudio from my systems. Basically I wanted to get AC3/DTS surround-sound, optical (SPDIF) pass-through working (which was relatively easy without PulseAudio getting in the way).
I mention this because the WINE developers are always moaning about PulseAudio adding latency, etc. As a result they refuse to have PulseAudio support in the mainline WINE code (support can be patched in).
I just [COLOR="Red"]Bing[/COLOR]'d :P on this and found a very short+easy guide!! :P

Bob

---

