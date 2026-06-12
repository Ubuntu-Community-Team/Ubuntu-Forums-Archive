---
title: "Lack of desktop environments in one system"
date: 2013-08-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Jonathan Andrew Upton on 2013-08-24
At one point I was using both Linux Mint and Ubuntu on one computer, and I noticed that with Ubuntu, there was Unity, and all of the other desktop environments (e.g. KDE, LXDE, Xfce) were within the derivatives; however, Linux Mint comes pre-installed with Cinnamon, GNOME, KDE, MATE and Xfce in one system.

Why cannot Ubuntu come with GNOME, KDE, LXDE, Unity, Xfce, etc. so that Ubuntu users could have the choice in future? :)

---

### Post by Cheesemill on 2013-08-24
*Thread moved to **Ubuntu, Linux and OS Chat**.*

*Not a support request.*

It's done this way to keep the size of the OS download low.

There's nothing to stop you installing any DE you want on a normal Ubuntu installation.

Also the more different DE's you have on the same system the higher the chance of them conflicting with each other. Even if you could download Ubuntu with all the DE's installed most people wouldn't use it as most people only tend to use one DE.

---

### Post by ibjsb4 on 2013-08-24
Its easy to add the different desktops to you current install.  For Xubuntu, lubuntu and gnome-classic:

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:
```
sudo apt-get install lxde xfce4 xfce4-goodies gnome-panel
```

And choose your desktop at login.

---

### Post by vasa1 on 2013-08-24
> **Jonathan Andrew Upton said:**
>  ... however, Linux Mint comes pre-installed with Cinnamon, GNOME, KDE, MATE and Xfce in one system. ...
Are you absolutely sure about this?

---

### Post by Cheesemill on 2013-08-24
> **vasa1 said:**
> Are you absolutely sure about this?

+1 to this.

I've just been to the Mint download page and you have to chooses which DE you want when you download.
What makes this any different from the way Ubuntu does things?

---

### Post by 3rdalbum on 2013-08-24
There's so much wrong in the original post.

Linux Mint does not have all those different desktops preinstalled. Each copy of Mint comes with one desktop. You can install others after you've installed the base system.

Ubuntu comes with one desktop. You can install others after you've installed the base system.

The only difference is that you can only install Mate or Cinnamon on Ubuntu by using PPAs (they are not in the regular repositories), and it's very nearly impossible to get Unity to work on Linux Mint.

Linux Mint's ability to install different desktops comes directly from Ubuntu. And, to give credit where it's due, Ubuntu got it from Debian.

---

### Post by grahammechanical on 2013-08-24
Please also think about the word "environment." Unity is not a desktop environment. It is a User Interface. It runs on the Gnome 3 desktop environment. It does not use the Gnome 3 UI called Gnome 3 shell.

From the beginning a decision was taken that Ubuntu would be built upon Debian Linux and use the Gnome DE. That decision has not changed. And because this is Open Source Software those who would like to use other desktop environments are able to do that. So, we have Kubuntu (KDE), Xubuntu (Xfce), Lubuntu (Lxde) and also Ubuntu Gnome which uses Gnome 3 shell. And then there are others that are only slightly related to Ubuntu, such as Linux Mint.

Ubuntu could come with all those options that you wish but it would take a lot of development work to bring it about and to maintain. Someone has to do the work.

---

### Post by PaulW2U on 2013-08-24
> **Jonathan Andrew Upton said:**
> [COLOR=#000000]Linux Mint comes pre-installed with Cinnamon, GNOME, KDE, MATE and Xfce in one system.[/COLOR]I wouldn't want to explore the application menus will all those duplicated applications. :(

> **Jonathan Andrew Upton said:**
> Why cannot Ubuntu come with GNOME, KDE, LXDE, Unity, Xfce, etc. so that Ubuntu users could have the choice in future? :)
Although Canonical provides the infrastructure and some resources to the various flavours I suspect that they really want us all to be using Ubuntu (Unity) so why would they provide alternative DEs all on one installation DVD?. I'm pretty certain that the flavours very much wish to preserve their own identity especially Kubuntu which has a commercial relationship with [Blue Systems](http://www.blue-systems.de/).

---

### Post by Jonathan Andrew Upton on 2013-08-24
> **PaulW2U said:**
> I wouldn't want to explore the application menus will all those duplicated applications. :(


Although Canonical provides the infrastructure and some resources to the various flavours I suspect that they really want us all to be using Ubuntu (Unity) so why would they provide alternative DEs all on one installation DVD?. I'm pretty certain that the flavours very much wish to preserve their own identity especially Kubuntu which has a commercial relationship with [Blue Systems]("http://www.blue-systems.de/").


Well if in doubt, you could always install different desktop  environments through the Terminal, so that you have your choice straight  away when you boot up in future.

To be perfectly honest, Canonical does not provide 100% development for the Ubuntu derivatives: they develop and support them, but the specific communities do most of the work on the systems. Blue Systems do development for most derivatives that use the KDE desktop environment. Canonical provides Unity, but they previously provided GNOME; many feel that Canonical are trying to compare themselves to Apple, but I am a fan of Unity, so I am probably not the right person to say. :lolflag:

---

### Post by deadflowr on 2013-08-24
> **Jonathan Andrew Upton said:**
> .
Why cannot Ubuntu come with GNOME, KDE, LXDE, Unity, Xfce, etc. so that Ubuntu users could have the choice in future? :)

Choice isn't always a great or easy thing.
Look at all the threads and posts on whether or not someone should run 32-bit vs 64-bit.
And then imagine how bad it would be if you were given more arch choices.

And besides, why make just Ubuntu offer choices, why not make Xubuntu offer KDE, or Lubuntu offer Gnome?
Those distros are going to exist separate from Ubuntu regardless of whether or not Ubuntu gives an option to select a desktop, so why not make them follow suit.

Whether you like Unity or not, only coming with Unity shows they have confidence in it.
It's hard for me to think others who offer choices have that conviction.

---

### Post by Roasted on 2013-08-26
I wouldn't mind seeing one DVD that has more things packaged together like openSUSE, which with their DVD ISO asks which environment you want and goes to town from there. But it would be just another ISO to maintain, so I get it.

Since I use multiple types of *buntu distros I used to get pretty meh about spinning up a new flash drive installer any time I wanted to use a different one. I ended up making a custom flash drive with about 10 ISOs on it using an application known as MultiSystem.

---

### Post by grahammechanical on 2013-08-26
Too much choice at installation time is thought to complicate things for new users. I tried SuSe years and years ago and all the options almost freaked me out. I am glad that Ubuntu did not put me through that when I first installed back in 2007.

Ubuntu Studio is working to give its users a choice of desktop to be installed at installation time. There would only be one installed (I think).

This is the comment from the blueprint.

> [ubuntustudio-dev] Add options to install differente DEs in ubiquity  (one is on ISO, the rest can be installed if an internet connection  exists): TODO

[https://blueprints.launchpad.net/ubuntu/+spec/ubuntustudio-s-installer](https://blueprints.launchpad.net/ubuntu/+spec/ubuntustudio-s-installer)

This came about, I understand because a user asked if he/she could use Ubuntu Studio with the Unity user interface. There are now blueprints for Unity, Gnome and KDE.

[https://wiki.ubuntu.com/UbuntuStudio/PermanentBlueprintOverview](https://wiki.ubuntu.com/UbuntuStudio/PermanentBlueprintOverview)

Regards.

---

### Post by Jonathan Andrew Upton on 2013-08-27
> **deadflowr said:**
> Choice isn't always a great or easy thing.
Look at all the threads and posts on whether or not someone should run 32-bit vs 64-bit.
And then imagine how bad it would be if you were given more arch choices.

And besides, why make just Ubuntu offer choices, why not make Xubuntu offer KDE, or Lubuntu offer Gnome?
Those distros are going to exist separate from Ubuntu regardless of whether or not Ubuntu gives an option to select a desktop, so why not make them follow suit.

Whether you like Unity or not, only coming with Unity shows they have confidence in it.
It's hard for me to think others who offer choices have that conviction.


Personally I think that these derivatives' existences are pointless, as they are Ubuntu but with different desktop environments. If Ubuntu offered different desktop environments by default or through the Ubuntu Software Centre, what they wish for would have been granted. Remember Gobuntu? That was an official derivative of Ubuntu that ran Free Software; it was discontinued when Ubuntu began to include Free Software into it's system.

---

### Post by cortman on 2013-08-27
> **Jonathan Andrew Upton said:**
> Personally I think that these derivatives' existences are pointless, as they are Ubuntu but with different desktop environments. If Ubuntu offered different desktop environments by default or through the Ubuntu Software Centre, what they wish for would have been granted. 

What? You *can* install any DE from the Ubuntu repositories, but that doesn't make the derivatives pointless. What if you want a system with only what you need for your DE, and not all the Unity/Gnome cruft as well? What if you don't have reliable internet available to install other DEs?
What would be pointless would be for Ubuntu to include all those DEs you mention in the ISO. It would be absolutely huge.

> **Jonathan Andrew Upton said:**
> 
Remember Gobuntu? That was an official derivative of Ubuntu that ran Free Software; it was discontinued when Ubuntu began to include Free Software into it's system.

?? Ubuntu has always included Free Software. Anything licensed under the GPL can be considered free software.

---

### Post by codingman on 2013-08-27
> **Jonathan Andrew Upton said:**
> Well if in doubt, you could always install different desktop  environments through the Terminal, so that you have your choice straight  away when you boot up in future.To be perfectly honest, Canonical does not provide 100% development for the Ubuntu derivatives: they develop and support them, but the specific communities do most of the work on the systems. Blue Systems do development for most derivatives that use the KDE desktop environment. Canonical provides Unity, but they previously provided GNOME; many feel that Canonical are trying to compare themselves to Apple, but I am a fan of Unity, so I am probably not the right person to say. :lolflag:What are you trying to say here? First your saying that Ubuntu should come with more DE's and then you're fixing your own problem. Don't spam the forums!

---

### Post by SeijiSensei on 2013-08-27
> **Jonathan Andrew Upton said:**
> Personally I think that these derivatives' existences are pointless, as they are Ubuntu but with different desktop environments.

That's certainly not true when it comes to the difference between Ubuntu and Kubuntu.  KDE is not just a different desktop environment from GNOME or Unity.  KDE also includes an array of programs of its own written to use the Qt libraries rather than GTK+.  A vanilla Kubuntu installation will have rekonq rather than Firefox, Dolphin rather than Nautilus, kmail rather than Thunderbird, Konsole rather than GNOME Terminal, etc., etc.  Even including just GNOME and KDE would result in substantial duplication of applications and libraries.   For someone without much Linux experience this would be a bit overwhelming.  Sure a user could try both alternatives for everything and pick and choose among them, but most people are happy with the one program per task approach.  If you find you want to try Chromium instead of rekonq, it's just an apt-get away.

---

