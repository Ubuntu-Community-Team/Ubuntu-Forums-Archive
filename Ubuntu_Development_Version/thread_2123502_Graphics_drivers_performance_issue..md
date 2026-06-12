---
title: "Graphics drivers performance issue."
date: 2013-03-08
forum: Ubuntu Development Version
---

### Post by Zestypanda on 2013-03-08
Hello I'm running raring ringtail dev build kernel 3.8.1.1 and I have an asus 6670 1gb graphics card. The open source FGLRX drivers are amazing, work out of the box, unity is fast end fluid compiz works great, yet it cannot play 3D gaming due to the fact that at this fine the open source drivers do not support hardware acceleration, so I installer the closed source AMD 13.1 beta drivers and they work fine on gaming (100+fps doom3) but now compiz is slow and unity is sluggish, when I had the open source drivers installed if said hardware acceleration was on yet whenever I strutted doom3 it would crash or any 3D game, so is there a way to either 1.) improve performance on the closed source drivers or 2.) enable 3D gaming on the open source drivers?

---

### Post by Yellow Pasque on 2013-03-08
> the open source drivers do not support hardware acceleration
false

> The open source Felix drivers are amazing
I've never heard of them. Link? (Maybe they're what is causing the issue).

---

### Post by coffeecat on 2013-03-08
*Thread moved to **Ubuntu +1 (Raring Ringtail)**.*

---

### Post by grahammechanical on 2013-03-08
Perhaps the OP is referring to this

> [COLOR=#000000][FONT=sans-serif]written by Felix A. "Dworkin" Croes[/FONT][/COLOR]

> [COLOR=#000000][FONT=sans-serif]On February 3, 2010, DGD 1.4 was released as [/FONT][/COLOR][open-source software]("http://en.wikipedia.org/wiki/Open-source_software")

[http://en.wikipedia.org/wiki/Dworkin's_Game_Driver](http://en.wikipedia.org/wiki/Dworkin's_Game_Driver)

Regards.

---

### Post by Zestypanda on 2013-03-08
No, that was a typo, I meant FGLRX. I am typing on an iPad so it autocorrects.

---

### Post by Zestypanda on 2013-03-08
Ok, so, according to you the open source FGLRX default drivers support hardware acceleration? Yes, on certain cards, not mine. So that's why when I tried to play doom3 (hardware accelerated graphics) it crashed, then when I installed the proprietary drivers it worked fine, but now compiz performance sucks.

---

### Post by deadflowr on 2013-03-08
The fglrx drivers aren't open-source.
Those would be the radeon drivers.

---

### Post by Zestypanda on 2013-03-08
The drivers that come preinstalled with Ubuntu, the default ones, which ones are those?

---

### Post by cariboo on 2013-03-08
> **deadflowr said:**
> The fglrx drivers aren't open-source.
Those would be the radeon drivers.

> **Zestypanda said:**
> The drivers that come preinstalled with Ubuntu, the default ones, which ones are those?

deadflower gave you the answer, the open source driver is called Radeon.

---

### Post by Zestypanda on 2013-03-09
Well, I that the xorg drivers were the open source ones, I'm taking about getting hardware acceleration on the xorg drivers.

---

### Post by cariboo on 2013-03-09
Xorg is the windows system that draws the different elements, you need a driver to interact with the Xorg server. The full name of the driver is xserver-xorg-video-radeon (1:7.1.0-0ubuntu1). For more info have a look [here]("http://packages.ubuntu.com/raring/xserver-xorg-video-radeon").

---

### Post by Zestypanda on 2013-03-10
Oh ok, also on a side not I installed the ati 13.2 beta7 drivers and now unity won't load, how can I purge and reinstall the default drivers from tty?

---

### Post by cariboo on 2013-03-10
> **Zestypanda said:**
> Oh ok, also on a side not I installed the ati 13.2 beta7 drivers and now unity won't load, how can I purge and reinstall the default drivers from tty?

Open a terminal and use the following command:

```
sudo apt-get purge <package-name>
```

where <package-name = the name of the driver package you installed, I refuse to use ATI/AMD graphic adapters, so you're on your own as far as the driver name is concerned.

---

### Post by Stinger on 2013-03-10
@ Zestypanda
Here you go !

 [Problem: Need to purge -fglrx]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx")

Start with this
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
Takes care of most of the unwanted elements.

I have been there a couple of times myself with my radeon HD4670 card ;)

BTW if you downloaded the driver directly from AMD the uninstall routine is a bit different.

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

---

### Post by Zestypanda on 2013-03-10
Thank you, but I already bit the bullet and re installed 13.04 (is it me or does reinstalling make ubuntu feel faster. :P ) so yeah, it's not running the x.org xserver drivers and it's butter smooth..woot. Though, I am wondering without going into the world of hurt that the proprietary drivers send me, can I hack, force, enable you call it 3d acceleration on the x.org drivers?

---

### Post by Stinger on 2013-03-11
> **Zestypanda said:**
> Thank you, but I already bit the bullet and re installed 13.04 (is it me or does reinstalling make ubuntu feel faster. :P ) so yeah, it's not running the x.org xserver drivers and it's butter smooth..woot. Though, I am wondering without going into the world of hurt that the proprietary drivers send me, can I hack, force, enable you call it 3d acceleration on the x.org drivers?

No I'm afraid not ,but at the X.Org Wiki you can see the [features available in the radeon driver]("http://www.x.org/wiki/RadeonFeature#Feature_Matrix_for_Free_Radeon_Drivers")

I know for a fact that the driver cannot display texture files i the old PCX format when i run my old Doom games with the [Doomsday engine]("http://dengine.net/"), when I covert them to PNG instead it runs just fine.

---

### Post by Zestypanda on 2013-03-11
What about this ppa? I added it and haven't installed it yet, would this work? [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

---

### Post by SkylineGTR on 2013-03-11
edited

---

### Post by Zestypanda on 2013-03-12
Sorry to bump this thread but I'm sorta confused on how to proceed with this.

---

### Post by Stinger on 2013-03-12
@ Zestypanda
You mean [xorg-edgers fresh X crack for Raring]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=raring") ?
Yes it should work, although there might be 'instability' involved as it is the fresh X crack.
Which driver are you planning to use, the standard one from Xorg or the fglrx driver from AMD ?

---

### Post by Zestypanda on 2013-03-12
Thank you for replying again, and yes I know I did one of the nonos *gasp* I bumped my thread, but yes, I am using the default xorg drivers, and yes I understand it might make my system unstable...I've run elementary OS also :P But all kidding asside, yes I understand the risk, this is not a production machine so I want to go along with this. I tried Sudo apt-get install xorg-edgers and I think it reported it could not find the package. Even after I did Sudo apt-get update after adding the ppa.

---

### Post by cariboo on 2013-03-12
The command you need to add a ppa is:

```
apt-add-repository <ppa_name>
```

so in this case it would be:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
```

then run:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Zestypanda on 2013-03-13
Ok, so I did that so what now? How can I check to see if it properly installed the package?

---

### Post by cariboo on 2013-03-13
The closed source driver will only update from the ppa, if you already have it installed. If you don't have it installed, you'll have to to that.

---

### Post by Zestypanda on 2013-03-13
I installed the xorg cracked package that should give me accelerated graphics

---

### Post by Zestypanda on 2013-03-14
Ok, I installed them and used doom3 to test them, it crashed my system and screwed up my ubuntu install, because after shutting down my computer after doom3 screwed up my screen res I restarted and let it boot, but then it failed and crashed into busybox. I think it's something to do with kernel 3.8.12 because I booted into GRUB and selected the advanced UBUNTU options and booted into kernel 3.8.11 it was able to successfully boot and I am going to try to remove Xorg-cracked from my system and see if it can boot properly on kernel 3.8.12

---

