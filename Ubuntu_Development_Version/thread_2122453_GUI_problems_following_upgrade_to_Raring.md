---
title: "GUI problems following upgrade to Raring"
date: 2013-03-05
forum: Ubuntu Development Version
---

### Post by DrDaveyAtoms on 2013-03-05
Hi,

I am experiencing some serious issues with the gui following my upgrade to raring. 

Immediately following the upgrade I had no gui whatsoever and fixed this by removing xorg.conf file as suggested in a thread on this forum. This resulted in a gui appearing but in low resolution like low graphics mode. Also, I had no taskbar/menus etc. only the icons of the files saved on the dektop.

To try to fix this I followed more suggestions from this forum and purged all traces of flgrx from the system. When I rebooted this resulted in the resolution returning to normal. however, I still did not have any menus or taskbar etc. I then downloaded the most recent ATI graphics card legacy drivers (13.1) from the ATI site and installed those. After rebooting the system came back to life with the poor resolution once more. 

As you can see, I have been following the advice given on a number of threads but to no avail. I am nearing my wits end with this problem and I am considering a fresh install. Since this is not the first time I have had issues with upgrades and installations with Ubuntu (been using it for about three years) I am considering trying another distribution for this fresh install. It might not be any better but I doubt it can be worse.

Does anyone have any suggestions as to how I can restore my beloved Ubuntu setup to its former glory?

---

### Post by Bucky Ball on 2013-03-05
*Thread moved to **Ubuntu +1 (Raring)***

Be aware that Raring Ringtail is not released until late April so expect breakages and a steeper learning curve. To restore Ubuntu to it's former glory you might try reinstalling the release you were using before (a stable one).

---

### Post by ibjsb4 on 2013-03-05
If your looking for stability why are you upgrading to a version thats still under development?  The final release of 13o4 is not till April.

---

### Post by dino99 on 2013-03-05
right click on the desktop to open a terminal, and run:  unity --reset (if you are logged as unity) or gnome-shell --replace (for GS) or gnome-panel --replace (for gnome-classic aka fallback)

---

### Post by DrDaveyAtoms on 2013-03-05
> **ibjsb4 said:**
> If your looking for stability why are you upgrading to a version thats still under development?  The final release of 13o4 is not till April.

It wasn't my intention to upgrade to 13.04. 

I upgraded to 12.10 initially and I encountered the situation described above. At that point it I thought it may have been due to an incomplete installation and as I could not use any graphical interface I upgraded from the terminal. 

The result is that I have ended up with a version which is at the bleeding edge. This is absolutely not what I wanted as I was content to use 10.04LTS until the support was recently withdrawn.

---

### Post by ventrical on 2013-03-05
> **DrDaveyAtoms said:**
> It wasn't my intention to upgrade to 13.04. 

I upgraded to 12.10 initially and I encountered the situation described above. At that point it I thought it may have been due to an incomplete installation and as I could not use any graphical interface I upgraded from the terminal. 

The result is that I have ended up with a version which is at the bleeding edge. This is absolutely not what I wanted as I was content to use 10.04LTS until the support was recently withdrawn.

I thought support for Lucid  was suppossed to be up to April, 2013?

What graphics card are you using?

---

### Post by DrDaveyAtoms on 2013-03-05
> **dino99 said:**
> right click on the desktop to open a terminal, and run:  unity --reset (if you are logged as unity) or gnome-shell --replace (for GS) or gnome-panel --replace (for gnome-classic aka fallback)

Thanks dino. This has not solved all of my problems but it has improved matters somewhat.

When logged into unity and I run the command you have suggested I get the following message: ERROR: the reset option is now deprcated .

If however I log in through gnome-panel and run the command you have suggested then the menus and taskbars do indeed return! However, the resolution remains rather poor. This situation remains the same even after a reboot but I no longer have to run the gnome-panel comand.

---

### Post by ibjsb4 on 2013-03-05
Well, there is no way to downgrade.  You could do a fresh install of the latest LTS (12o4). And if you want a desktop that looks like 10o4 you can install the gnome-classic desktop.

---

### Post by DrDaveyAtoms on 2013-03-05
> **ventrical said:**
> I thought support for Lucid  was suppossed to be up to April, 2013?

What graphics card are you using?

Yes you are correct, sorry. However, I knew it was either finished or about to finish. No matter.

lspci returns that I am using AMD ATI Radeon HD 4300 series.

---

### Post by serdotlinecho on 2013-03-05
@[**[COLOR=#000000]DrDaveyAtoms[/COLOR]**]("http://ubuntuforums.org/member.php?u=1012154") unity --reset will not work on 12.10 and 13.04, read [this :)]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html")

---

### Post by DrDaveyAtoms on 2013-03-05
> **serdotlinecho said:**
> @[**[COLOR=#000000]DrDaveyAtoms[/COLOR]**]("http://ubuntuforums.org/member.php?u=1012154") unity --reset will not work on 12.10 and 13.04, read [this :)]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html")

Thanks for the info and link. Good to know. I will have to try this when I am at home as I am behind a proxy at work and can't add repositories.

---

### Post by zika on 2013-03-05
> **dino99 said:**
> right click on the desktop to open a terminal, and run:  unity --reset (if you are logged as unity) or gnome-shell --replace (for GS) or gnome-panel --replace (for gnome-classic aka fallback)```
unity --reset
```does not work since 12.10. &#8222;reset&#8220; option is &#8222;canceled&#8220;...
Since I'm lazy to write, see: [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html) ...
Ups, @serdotlinecho already answered. I should learn to read messages in reverse order...

---

