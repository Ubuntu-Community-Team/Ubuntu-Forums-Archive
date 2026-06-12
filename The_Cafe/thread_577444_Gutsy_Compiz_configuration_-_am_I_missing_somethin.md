---
title: "Gutsy Compiz configuration - am I missing something?"
date: 2007-10-16
forum: The Cafe
---

### Post by metromari on 2007-10-16
I wanted to configure the Compiz on my Gutsy system. There was an "Open GL window manager" option or some such thing on one of my Gnome menus. But every time I clicked the icon, nothing would happen. This worked in Feisty, but not Gutsy. It turns out this is part of Gnome Compiz Manager, and GCM apparently is not part of the Compiz project:

[http://compiz.org/Gnome_Compiz_Manager](http://compiz.org/Gnome_Compiz_Manager)

The page for GCM that is linked from the Compiz webpage has not even been updated since January:

[http://compiz.org/Gnome_Compiz_Manager](http://compiz.org/Gnome_Compiz_Manager)

Okay, so maybe that explains why GCM doesn't work. So I turned to Compiz Settings. That's in universe--strange, I wouldn't think you would need to go to universe to configure something that's turned on by default in the base system. Whatever. I loaded up Compiz Settings, and it's an overwhelming heap of settings. All I wanted to do was configure the feature that's like OS X Expose. Apparently I get an Expose like thing when I move my mouse pointer to the upper-right corner, but there doesn't seem to be a way to configure that. I turn to the Compiz website:

[http://compiz.org/Compiz-Settings](http://compiz.org/Compiz-Settings)

and I'm greeted with a nice warning: "NOTE: All the links are dead, this project is abandoned and there is no support or updates for it!"

Maybe the whole Compiz website is hopelessly out of date. DistroWatch and Wikipedia both agree that 0.6.0 is the latest Compiz release, but the website says the development release is 0.5.2.

Am I missing something here? Is there some easy way to configure Compiz that I am missing? It seems to me to be a very promising project--better than OS X eye candy, even. But if there's no way to configure even basic options without getting lost in a huge pile of settings, then it seems to me that turning it on by default in Gutsy was a big mistake.

---

### Post by cogadh on 2007-10-16
Gutsy has Compiz Fusion, not regular Compiz or Beryl. The info you found likely relates to the regular Compiz. If you install the "compizconfig-settings-manager" package, that should give you what you want. You have to have the Universe repository enabled to get it.

---

### Post by argie on 2007-10-16
Also, you're looking for the Plugin called Scale.

---

### Post by metromari on 2007-10-16
Cool, that's a start. I've been confused by all the talk about Compiz merging with Beryl (I think) and didn't realize there is a separate Compiz Fusion...will take a look at CCSM.

---

### Post by jr.gotti on 2007-10-16
[apt:compizconfig-settings-manager](apt:compizconfig-settings-manager)

Click the above link to install CCSM
 
Then right click on the desktop, click change desktop background, go to visual effects, and click custom.

---

### Post by frsrblch on 2007-10-16
Guys, your timing is absolutely amazing.  You fixed my problem moments before I searched it.

---

### Post by Nano Geek on 2007-10-16
> **jr.gotti said:**
> [apt:compizconfig-settings-manager](apt:compizconfig-settings-manager)

Click the above link to install CCSM
 
Then right click on the desktop, click change desktop background, go to visual effects, and click custom.Whoa, I didn't know you could do that.
That's cool!

---

### Post by 23meg on 2007-10-16
> **cogadh said:**
> Gutsy has Compiz Fusion, not regular Compiz or Beryl. 

No, Gutsy has regular Compiz by default. The extras that comprise Compiz Fusion are separately installable.

> **cogadh said:**
> You have to have the Universe repository enabled to get it.

Universe is enabled by default.

---

### Post by cogadh on 2007-10-16
From the release notes on Gutsy:
> Compiz Fusion is enabled by default and will bring 3D desktop visual effects that improve the usability and visual appeal of the system. Ubuntu 7.10 automatically detects whether the hardware is capable of running compiz; if not, it falls back to normal desktop. Additional effects can be enabled in "System/Preferences/Appearance" under the "Visual Effects" tab. There you can also disable the effects entirely.
If you had the Universe repositories enabled prior to running an upgrade, they will still be enabled, otherwise they are not (at least that's what happened with my upgrade).

---

### Post by 23meg on 2007-10-16
Right, perhaps we do have some bits from Fusion.

[QUOTE=cogadh]
If you had the Universe repositories enabled prior to running an upgrade, they will still be enabled, otherwise they are not (at least that's what happened with my upgrade).[/QUOTE]

That's the way it's meant to work. With fresh installs, Universe and Multiverse are enabled by default in Feisty and Gutsy.

---

