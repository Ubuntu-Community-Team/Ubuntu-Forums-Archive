---
title: "Ubuntu and a Complete Hardware Upgrade"
date: 2009-09-04
forum: Testimonials &amp; Experiences
---

### Post by Zoot7 on 2009-09-04
Due to a hard drive failure I had to replace the Hard Drive housing Ubuntu on my home built desktop, and due to lazyness I wasn't too chuffed about having to reinstall and recompile all the stuff I all over again, so I thought why not just clone my fully functional installation of Hardy off my laptop and just pop the drive into the case, and see what the outcome would be.

Well it worked perfectly! :) I had a small bit of work to configure the video again, uninstall the nVidia driver and envy, then install the ATi driver manually (but that's to be expected). Then I had to upgrade ALSA to 1.0.21 in order to get my X-Fi working, and everything is as was once again.
Ubuntu has amazed me at it's versatility yet again, i wouldn't even dare to attempt the same thing under Windows, which normally gets extremely upset after a motherboard change. :)

Anyway the specs of both are:

#1 Dell XPS M1530 | Intel T7500 @ 2.2GHz | 2GB DDR2-667 | 8600M GT
#2 Gigabyte MA-790FXT-UD5P | AMD Phenom II X4 955 | 4GB DDR3-1333 | Sapphire HD4870 1GB | X-Fi XtremeGamer

(In hindsight I wouldn't have bought the X-Fi if I knew 3 years ago of it's non-existent ALSA support.... until now :) )

All I can say is keep up the great work Canonical! :)

---

### Post by Garrovick on 2009-09-04
I've "cloned" both of my computers to external hard drives. Acronis True Image works with Linux and Windows. I've tested both.

And with Windows, we are allowed to make ten hardware changes before we have to make a simple phone call to reactivate for ten more changes to hardware.

---

### Post by fh_scott on 2009-09-05
My Inspiron 6400 (jaunty 32-bit) was getting a little old and I found this Vostro 1500 sitting in the server room, so I popped the hard drive out of the Inspiron and put it into the Vostro and booted up. The only thing that needed configuring was activating the Broadcom card and rebooting and I was good to go.

Now I had a second hard drive for that Inspiron that had an XP installation on it. Guess what happened when I put that one in the Vostro?

If you guess BSOD on boot, you would be correct.

Ubuntu FTW.

---

### Post by stalkingwolf on 2009-09-06
> The only thing that needed configuring was activating the Broadcom card and rebooting and I was good to go.

I have an HP nc8000.  With 8.10 and 9.04 all 3 of my wireless adapters
show deactivated.  How did you activate yours?

internal   intel something
DLink DWL G650
Netgear wv 111 V2

all work fine on an older release of 8.04.

---

### Post by fh_scott on 2009-09-07
System | Administration | Hardware Drivers

I had two to choose from, Broadcom B43 and Broadcom STA.

I didn't know much about either, and honestly picked the STA because it said proprietary and I was hoping for better functionality.

It downloaded, activated, told me to reboot, and I was good to go. It even used my existing Wifi configuration even though the broadcom registered as eth2 instead of wlan0 like my Intel card. I guess NetworkManager took care of that.

-scott

edit: the intel 3945 card on my inspiron 6400 worked without any kind of fiddling or intervention. It just worked.

---

### Post by stalkingwolf on 2009-09-07
it was weird all 3 showed up in the wifi manager but i couldnt activate any of them.  I ended up digging out a copy of 8.04 from just after the release
and installing it.  All of them worked fine and continue to work after the updates and all , weird.

---

