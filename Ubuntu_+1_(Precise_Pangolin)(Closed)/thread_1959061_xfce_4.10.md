---
title: "xfce 4.10"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rburkartjo on 2012-04-15
has anyone been able to install xfce 4.10 preview release successfully in 12.04

---

### Post by Gregory Lee on 2012-04-15
I have a version of xfce4 which was listed as an add-on for "Gnome Desktop Environment" in Software Center.  I used it for a couple of days about a week ago.  Seemed to work  --  not very interesting.  I got a version of KDE the same way and am using that now -- it's pretty cool.  However, my post of a few days ago about this got moved away, so I guess we're not supposed to discuss these alternative shells, though they're part of 12.04.

---

### Post by neu5eeCh on 2012-04-15
There is an XFCE master who lives in this forest (is it Dagobah?) who goes by the name of Toz. Seek him, and you shall find your answers young apprentice.

---

### Post by Bucky Ball on 2012-04-15
> **Gregory Lee said:**
>  However, my post of a few days ago about this got moved away, so I guess we're not supposed to discuss these alternative shells, though they're part of 12.04.

Ubuntu is a base system/kernel. The desktop environment is totally by choice. Kubuntu, Xubuntu, Edubuntu, Ubuntu Studio, Ubuntu, *Buntu ... all the same underneath. The flavours drag in the desktop environment and the apps. That's it. 

Try a minimal install. You decide what you want ... but it will always be a Ubuntu base install driving it.

Hoping you get what I mean ... ;)

---

### Post by xebian on 2012-04-15
> **rburkartjo said:**
> has anyone been able to install xfce 4.10 preview release successfully in 12.04

I don't see it so 'am not sucessfull.  But seriously, where is it?

Am using one right now from Porteus 4.9 which I'm told will be 4.10?

---

### Post by xebian on 2012-04-15
> **VTPoet said:**
> There is an XFCE master who lives in this forest (is it Dagobah?) who goes by the name of Toz. Seek him, and you shall find your answers young apprentice.

I think it's lucazade?  Someone with a similar name remastered a Porteus with 4.9.

---

### Post by Toz on 2012-04-15
> There is an XFCE master who lives in this forest (is it Dagobah?) who goes by the name of Toz. Seek him, and you shall find your answers young apprentice.
LOL.

I've installed and am running 4.10pre2 in precise (12.04) beta 2. See: [http://ubuntuforums.org/showpost.php?p=11844051&postcount=10]("http://ubuntuforums.org/showpost.php?p=11844051&postcount=10").

I took the hard road - built from git. It is possible, yes. There are a few gotchas you need to be aware of. In that same thread, drfox has built it using the prepackaged tarballs. 

Also, I'm only running it on a VM at the moment (I quite like my 11.10 xubuntu install with 4.8 ) just to see what its about and what the changes are.

---

### Post by drfox on 2012-04-15
I downloaded the fat tarball from here:
[http://archive.xfce.org/xfce/4.10pre2/fat_tarballs](http://archive.xfce.org/xfce/4.10pre2/fat_tarballs)
And installed in this order:
[http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building)

Don't forget to build thunar-volman

You will need to download some -dev dependencies from synaptic, but the error messages you get (if you don't have them) are pretty self-explanatory if ./configure fails

Working fine for me. Have fun!
Larry

---

### Post by drfox on 2012-04-15
If you run into any dependencies you can't figure out, write me.
Larry

---

### Post by xebian on 2012-04-15
> **drfox said:**
> I downloaded the fat tarball from here:
[http://archive.xfce.org/xfce/4.10pre2/fat_tarballs](http://archive.xfce.org/xfce/4.10pre2/fat_tarballs)
And installed in this order:
[http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building)

Don't forget to build thunar-volman

You will need to download some -dev dependencies from synaptic, but the error messages you get (if you don't have them) are pretty self-explanatory if ./configure fails

Working fine for me. Have fun!
Larry

I find it hard to believe Xubu devs have no ppa for latest xfce?

---

### Post by clifford junior on 2012-04-15
maybe one of you guys can help while im here. i've put xfce-desktop (4.8) on my 12.04 install and i seem to like it a lot.

however im a bit confused. as photography is a part of my work i've colour calibrated my monitor using dispcalGUI and thats fine while using unity as the profile loads on startup and i can confirm this with the colour setting in system settings.

does xubuntu have a similar setting? thank you.

---

### Post by Toz on 2012-04-15
> **clifford junior said:**
> maybe one of you guys can help while im here. i've put xfce-desktop (4.8) on my 12.04 install and i seem to like it a lot.

however im a bit confused. as photography is a part of my work i've colour calibrated my monitor using dispcalGUI and thats fine while using unity as the profile loads on startup and i can confirm this with the colour setting in system settings.

does xubuntu have a similar setting? thank you.

How does the profile load on startup on unity? Does the program start and automatically setup the profile? Do you have to pass it an argument indicating the profile you want to use? 

With xfce, you can setup apps to autostart in 'Settings Manager->Session and Startup->Application Autostart'.

---

### Post by neu5eeCh on 2012-04-15
> **xebian said:**
> I find it hard to believe Xubu devs have no ppa for latest xfce?

I don't.

It's hard to believe they managed to get tarballs out. Mind you, XFCE is my fav desktop.

---

### Post by Gregory Lee on 2012-04-15
> **VTPoet said:**
> I don't.

It's hard to believe they managed to get tarballs out. Mind you, XFCE is my fav desktop.
I guess no one is listening.  You don't have to go get tarballs or install any ppa.  Just bring up Software Center, find "GNOME Desktop Environment with extra components", look under Add-ons to find "Meta-package for the Xfce Lightweight Desktop Environment (xfce4)", check the Add-on box, install.

---

### Post by teachop on 2012-04-15
> **Gregory Lee said:**
> I guess no one is listening.  You don't have to go get tarballs or install any ppa.  Just bring up Software Center, find "GNOME Desktop Environment with extra components", look under Add-ons to find "Meta-package for the Xfce Lightweight Desktop Environment (xfce4)", check the Add-on box, install.
You are seeing 4.10?

---

### Post by neu5eeCh on 2012-04-15
> **teachop said:**
> You are seeing 4.10?

Yeah... what _he_ asked. 4.10?

---

### Post by budluva04 on 2012-04-15
the latest version of xfce in the 12.04 is 4.8...not 4.10, so you CANNOT install xfce4.10 from software center, sorry

xfce4:
  Installed: (none)
  Candidate: 4.8.0.3
  Version table:
     4.8.0.3 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages

---

### Post by Gregory Lee on 2012-04-15
> **teachop said:**
> You are seeing 4.10?
I said it was 4 -- that's all I know.  Is there something special about 4.10 we might like to know about? (Never mind -- I see that the version now in 12.04 is 4.8 and that 4.10 is due to be released in a preliminary version on 4/28.)

---

### Post by Toz on 2012-04-15
Here is a link to the 4.10 roadmap: [http://wiki.xfce.org/releng/4.10/roadmap]("http://wiki.xfce.org/releng/4.10/roadmap"). Toward the bottom of the page is a list of planned features (grouped by module) and their completion percentages. Some of the more prominent new features:
- reworked application finder
- panel deskbar mode
- mime type editor
- menu editor
- reworked settings manager presentation
- improved pointer settings options
- easier method to install themes
- window tiling 
plus a number of bug fixes.

---

