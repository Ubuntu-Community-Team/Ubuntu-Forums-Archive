---
title: "Revert to KDE from Unity on oneiric (11.10) fails"
date: 2011-10-06
forum: Ubuntu Moblin Remix
---

### Post by OldAlgis on 2011-10-06
I've installed on my netbook a beta version of oneiric (11.10) kubuntu.  I wanted to use the netbook for presentation at SIG meetings. On installation the default display is "special" Unity desktop, whilst the same version on the desktop PC is the KDE, which is more familiar and therefore better for me.

Whilst booting there is an option to revert to KDE, but that is just ignored.  Am I "hard wired" to Unity or can I make my netbook play with the "ordinary" KDE desktop?  Is ignoring the choice of KDE from the drop down menu a bug or is it intentional?  Any advice and ideas, please.

TIA,

---

### Post by ubun2geek on 2011-10-07
```
sudo apt-get install kubuntu-desktop
```
Hope this helps!

---

### Post by OldAlgis on 2011-10-08
> **ubun2geek said:**
> ```
sudo apt-get install kubuntu-desktop
```
Hope this helps!
Thank you for the message. It does help that someone bothered to answer! Unfortunately it does not infivsyr how to boot to kde-desktop.

The apt-get message to the suggested command is "kubuntu desktop is already the newest version".  Apparently the kde desktop is already installed. 

The 11.04 kubuntu had an option in the login screen to revert booting to kde (or to gnome in case of ubuntu). I've downloaded the nightly build yesterday and I find that this option has been completely eliminated from the booting dialog. 

The GUI System_Settings -> Login_Screen -> Theme seems to be a possible option to change the login behaviour, but how to preceed (and is it the right way)?

I think that many netbook users will wish to have the ability to switch to a "standard" (viz. kde) desktop, so it would be usefull to provide them (and me!) with a how-to.

Thanks again,

---

### Post by philinux on 2011-10-09
> **OldAlgis said:**
> Thank you for the message. It does help that someone bothered to answer! Unfortunately it does not infivsyr how to boot to kde-desktop.

The apt-get message to the suggested command is "kubuntu desktop is already the newest version".  Apparently the kde desktop is already installed. 

The 11.04 kubuntu had an option in the login screen to revert booting to kde (or to gnome in case of ubuntu). I've downloaded the nightly build yesterday and I find that this option has been completely eliminated from the booting dialog. 

The GUI System_Settings -> Login_Screen -> Theme seems to be a possible option to change the login behaviour, but how to preceed (and is it the right way)?

I think that many netbook users will wish to have the ability to switch to a "standard" (viz. kde) desktop, so it would be usefull to provide them (and me!) with a how-to.

Thanks again,

At the login screen when you highlight your user name there should be a tab at the bottom of the screen to select the session to kde. 

Is it this that is not working?

---

### Post by OldAlgis on 2011-10-09
> **philinux said:**
> At the login screen when you highlight your user name there should be a tab at the bottom of the screen to select the session to kde. 

Is it this that is not working?

In an earlier version in the "development branch" (daily build) the option tab was there, but it did not work.  Now the version dated 2011-10-07 (which I downloaded last Sunday) does not have that option at all.  Just to be sure, this is a kubuntu login screen that is seen when auto-login is not enabled.

Let me check it once more on my netbook - just in case I have gone computer-blind, which is a possibility.

I am thoroughly confused... I have just rebooted the netbook twice. First I chose to login with password, rather than auto-login. Then verified that the login screen had no options that used to be in the bottom right hand corner of "natty" login dialog.  

But to my surprise both times the netbook booted into the KDE, so now I am not able to get back to Unity.  Very confusing..  Perhaps I should wait a few days till the official release date. Is there a CLI option for the change of desktop, per chance?

Thanks for your interest - much appreciated!

---

### Post by Alwimo on 2011-10-09
When logging in, there is a cog/gear icon to the right of the name you click on to change what DE you start up.

EDIT: Or I seem to have misunderstood.

---

