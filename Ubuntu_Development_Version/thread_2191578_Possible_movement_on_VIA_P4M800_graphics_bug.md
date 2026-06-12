---
title: "Possible movement on VIA P4M800 graphics bug"
date: 2013-12-03
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-12-03
I love it when I get any dev response to a bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643)

Hopefully I'll be able to provide all of the info needed to move that off of incomplete status :D

---

### Post by ventrical on 2013-12-03
> **kansasnoob said:**
> I love it when I get any dev response to a bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643)

Hopefully I'll be able to provide all of the info needed to move that off of incomplete status :D

Those MoBos with Via chipset are very common in North America. (Got two here myself ). 

Nice work noob :)

fingers crossed :)

---

### Post by kansasnoob on 2013-12-03
> **ventrical said:**
> Those MoBos with Via chipset are very common in North America. (Got two here myself ). 

Nice work noob :)

fingers crossed :)

Perhaps sadly I bought a pallet of those WalMart Everex boxes that shipped with [gOS]("http://en.wikipedia.org/wiki/GOS_%28operating_system%29") , but I'd been confronted by many of my fellow seniors at the local senior center about dead Win 98 and Win ME boxes so I jumped on the deal - I think it came out to less than $20.00 US per box so it seemed like a good fix at that moment in time :)

In retrospect I feel like a boob :redface:

I'm now quite broke due to the Great Recession so I'm not financially capable of upgrading the 23 boxes I still have running that chip, but they're good until April 2017 using this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

But I'd love to get another two years if we can get it to work in Trusty :guitar:

---

### Post by ventrical on 2013-12-03
That is a very detailed thread on gnome instructional development  with 12.04. It is also very noble of you to help your fellows as you are. Ya know .. no child left behind .. no senior left behind either. I am currently working with a senior and instructing him in gnome-fallback and it seems a lot easier for him than Unity.

My point. I'll try to keep contributing as I can on the side.

Regards..

---

### Post by ventrical on 2013-12-03
I got the USB iso to boot.. it is now installing from Ubiquity to HD. It is an S3 32MB OnBoard video with the Via Chipset. More info to come. I know Unity will not work so I will have to install fvwm-crystal and lubuntu-desktop and gdm to see what happens after the install (if I can).

  I chose nomodset before I Installed. Also I pulled my nVidia quatro agp from the slot.
  Side note... ubiquity is actually smooth scrolling from side to side. What fresh E'll is this :)

---

### Post by ventrical on 2013-12-03
Install went great but it will not open gdm or lightdm at boot (have it set for gdm).  I can get to terminal from Grub (Recovery mode) and then , root, and from there I can run top and Midnight Commander but  when I use 'startx' it goes back to this green stripped screen with illegible characters. Plymouth worked Ok .. etc... so I wonder what is causing it to gum up like this.

What would be your next idea after you got this far?

edit:

btw  I have the [S3 ProSavage8] VIA. Does not one driver fit all for this chipset?

---

### Post by QDR06VV9 on 2013-12-03
> kansasnoob

I'm now quite broke due to the Great Recession so I'm not financially capable of upgrading the 23 boxes I still have running that chip,
 but they're good until April 2017 using this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)


> ventrical
I am currently working with a senior and instructing him in gnome-fallback and it seems a lot easier for him than Unity.

You Two are Real Gems  +1 +2 Your Awesome=D>
I lifts my heart, off topic I know but worth posting.

---

### Post by ventrical on 2013-12-03
Thanks runrikus! :) But honestly , I'm still trying to figure out who's on first! :):)lol

---

### Post by ventrical on 2013-12-03
@kansasnoob

  I did it .....    I removed:

xserver-xorg-video-savage  (which takes care of the S3 Savage series) and then installed:

xserver-xorg-video-vesa   and now I have GDM up and clear as a bell.  I did all of this through Grub (Recovery Mode) in #root.   I can't believe it.   Ya know .. the thing is that I didn't even know there was an 'xserver-xorg-video-vesa'. I just experimented and put it in there and , voila'. So , now off to see if I can log in and sends a message from there.

Edit:

I tried all the different sessions after downloading lubuntu-desktop .. etc... and GDM works but it will not pass me to the operating system. It just hangs at GDM no matter which session I try .. so I will try , in the morning , to remove GDM and reinstall lighdm and then try a workaround with the xserver-xorg-video-***  and see what happens from there.  I know that this is not the exact bug you are referring to but it is pretty close. mabey I'll find something.  Who knows eh  :)

---

### Post by QDR06VV9 on 2013-12-03
> **ventrical said:**
>  I'm still trying to figure out who's on first! :):)lol

Still one of the best comedy acts to ever take place.
Good job on the video driver. Have you tried them on xmir yet?

---

### Post by cariboo on 2013-12-03
I have the same chipset here, but I added a used Nvidia 6200 graphics card a few years back. I installed Trusty Lubuntu on the system a couple of weeks back, and it now runs way better than it ever did running XP.

---

### Post by ventrical on 2013-12-03
> **cariboo907 said:**
> I have the same chipset here, but I added a used Nvidia 6200 graphics card a few years back. I installed Trusty Lubuntu on the system a couple of weeks back, and it now runs way better than it ever did running XP.

Thanks cariboo907.

@kansasnoob

Ok!! It worked. I removed gdm and now lightdm is passing me to lubuntu-desktop on this VIA chipset graphics onboard chip.

```

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: S3 Graphics Ltd. VT8375 [ProSavage8 KM266/KL266]
ventrical@ventrical-P4M266A-8237:~$ 


```

---

### Post by Irihapeti on 2013-12-03
I have a similar chipset that was misbehaving earlier. It seems to be different enough to be working with the latest update.

```
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
```

Previously I was using the vesa workaround. Removed everything vesa (I thought) and found that the monitor wasn't working AT ALL after login. The culprit was displays.xml in ~/.config/xfce4/xfconf/xfce-perchannel-xml, which had a refresh rate of 0, for some reason. Once that file was gone, all was OK.

---

### Post by kansasnoob on 2013-12-04
> **Irihapeti said:**
> I have a similar chipset that was misbehaving earlier. It seems to be different enough to be working with the latest update.

```
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
```

Previously I was using the vesa workaround. Removed everything vesa (I thought) and found that the monitor wasn't working AT ALL after login. The culprit was displays.xml in ~/.config/xfce4/xfconf/xfce-perchannel-xml, which had a refresh rate of 0, for some reason. Once that file was gone, all was OK.

Had you joined that bug report as "effects me too"?

I guess it doesn't matter at this point but I'd personally appreciate a comment at that bug report stating that the latest openchrome driver is known to work with P4M900 :D

That should narrow things down for the dev involved.

---

### Post by Irihapeti on 2013-12-04
@kansasnoob:

Done. (I meant to do it yesterday but somehow got sidetracked.)

I was already subscribed to the report as "affects me too".

---

### Post by kansasnoob on 2013-12-04
> **Irihapeti said:**
> @kansasnoob:

Done. (I meant to do it yesterday but somehow got sidetracked.)

I was already subscribed to the report as "affects me too".

Many, many thanks :D

I'm going to retest with the latest Lubuntu either tonight or tomorrow because I noticed the addition of some odd "gnome" packages recently, so while I have a new image it's always worth spending a few extra minutes to check things out.

---

### Post by kansasnoob on 2013-12-21
Seems to be fixed based on testing both Xubuntu and Edubuntu Alpha 1 :guitar:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643)

---

