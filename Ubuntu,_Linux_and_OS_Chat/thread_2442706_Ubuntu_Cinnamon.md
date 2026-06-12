---
title: "Ubuntu Cinnamon?"
date: 2020-05-06
forum: Ubuntu, Linux and OS Chat
---

### Post by bionic3epl on 2020-05-06
Does Ubuntu Cinnamon> [https://ubuntucinnamon.org/](https://ubuntucinnamon.org/) have 5 years and is it backed by canonical? Does it also have live patch and is it a Debian? How often does a new version of Ubuntu Cinnamon get released? Does it follow the same update & upgrade rules as the original Ubuntu does? Does it have AppArmor?

---

### Post by deadflowr on 2020-05-06
At this point in time Ubuntu Cinnamon is completely unaffiliated with Ubuntu.
It's not an official flavor of Ubuntu like Kubuntu or Lubuntu are.
It has no support from Canonical.

that said,
> Does it follow the same update & upgrade rules as the original Ubuntu does? Does it have AppArmor?
if based on Ubuntu then is should adhere to Ubuntu update system and if using the Ubuntu base apparmor would be installed and in use.

---

### Post by grahammechanical on 2020-05-06
I would like to add that Ubuntu is still based on Debian. So, any distribution that is based on Ubuntu is also related to Debian.

[https://ubuntu.com/community/debian](https://ubuntu.com/community/debian)

Regards

---

### Post by Frogs Hair on 2020-05-06
An announcement regarding a 20.10 release indicates they follow the Ubuntu release cycle. 
 [https://ubuntucinnamon.org/ubuntu-cinnamon-20-04-lts-focal-fossa-release-notes/](https://ubuntucinnamon.org/ubuntu-cinnamon-20-04-lts-focal-fossa-release-notes/)

---

### Post by guiverc on 2020-05-06
> **bionic3epl said:**
> Does Ubuntu Cinnamon> [https://ubuntucinnamon.org/](https://ubuntucinnamon.org/) have 5 years and is it backed by canonical? ..

No flavor of Ubuntu has 5 years of supported life (with minor exceptions, Ubuntu Kylin in the 16.04 cycle was granted 5 years support by Canonical, that was a once-off exception though).


If you read the release notes of Ubuntu 20.04 LTS you'll find the following

> [COLOR=#000000][FONT=Arial]Maintenance updates will be provided for 5 years until [/FONT][/COLOR][April 2025]("https://wiki.ubuntu.com/Releases")[COLOR=#000000][FONT=Arial] for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, and Ubuntu Core. **All the remaining flavours will be supported for 3 years.**[/FONT][/COLOR]

[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)

That is standard, only Ubuntu itself was extended from 3 years to 5, flavors have always remained at 2 or 3 years (again with exceptions, eg. Ubuntu Studio 18.04 was **not** a LTS release thus only had 9 months *supported-life* which could be extended via use of PPA to 3 years, ie. it's always best to read the release notes and not make assumptions).

---

### Post by contrast9390 on 2020-07-02
The Lubuntu 16.04 VM I have still has updates from Canonical. Since it's on the LTS base.

I understand the Lubuntu guys aren't maintaing lxde, but Canonical is providing updates for everything critical. You'd have to assume someone would write malicious code that is meant to interact with the lxde desktop.  So unlikely to worry about those things. Most people wouldn't want to be five years OOD with packages anyway. It's perfectly safe to use it for five years.  Ubuntu Cinnamon is literally just Ubuntu's base with the CInnamon Desktop and defaults.

---

### Post by guiverc on 2020-07-02
If you're on your installed system, you can use the `ubuntu-support-status` tool to view the actual package status for your installed system (ie. to explore gain information about your actual systems's support status).

(note: I just noticed my system (*groovy*) has removed that tool & it was replaced with `ubuntu-security-status` which provides less detail but is somewhat more streamlined)

---

### Post by grahammechanical on 2020-07-03
Can we install snap apps on Ubuntu Cinnamon?

> Main Desktop (Maintained by **Linux Mint** and Debian**)**

The plot thickens! :)

Regards.

---

### Post by exploder on 2020-07-03
Why not just use Mint? You get the Ubuntu base with Cinnamon releases right from the developers. As I understand, there is a tutorial on using snaps in Mint if you really want to do that.

---

### Post by monkeybrain20122 on 2020-07-04
What is the difference between Ubuntu cinnamon and Linux Mint?

---

### Post by exploder on 2020-07-05
I think the differences are that snaps are disabled by default, theme and Mint tools. I have not looked at Ubuntu Cinnamon very closely though.

---

### Post by grahammechanical on 2020-07-05
But why call it "Ubuntu" cinnamon? Why use the name Ubuntu? Is this a "cunning plan" to fool users into thinking it is Ubuntu when it is Mint?

In researching this question I read a 2013 interview of Clement Lefebvre. 

[https://www.networkworld.com/article/2170903/q-a--clement-lefebvre--the-man-behind-linux-mint.html](https://www.networkworld.com/article/2170903/q-a--clement-lefebvre--the-man-behind-linux-mint.html)

He does not like Gnome. He says 

> Now, it is important to understand one thing: GNOME changes every six  months and its components often break compatibility with previous  versions of themselves. This means for instance that  gnome-settings-daemon doesn't speak the same language or that  gnome-bluetooth doesn't answer the same DBUS calls between versions 3.2,  3.4, 3.6, 3.8 of GNOME.

And this regarding Cinnamon

> It has become a complete desktop environment (mostly by necessity and for compatibility/portability reasons). I

I am guessing that Clement Lefebvre is slowly working towards a complete fork of Gnome and a version of what he thinks Ubuntu should be without Gnome 3 and Gnome 3 shell.

>  Cinnamon won't be a frontend to GNOME anymore but a complete desktop environment with its own backend.

Unity 7 was Ubuntu's frontend to Gnome 3 but Unity 7 is no more and Ubuntu is Gnome 3 and Gnome 3 shell with Cannonical branding. It suits me. I am not complaining.

Regards

---

### Post by uninvolved on 2020-07-05
By the way, if you want to know if AppArmor is installed just run "*apparmor_status*" from the terminal. If you run it with elevated permission, you can see how it is configured.

---

### Post by monkeybrain20122 on 2020-07-06
> **grahammechanical said:**
> 


Unity 7 was Ubuntu's frontend to Gnome 3 but Unity 7 is no more and Ubuntu is Gnome 3 and Gnome 3 shell with Cannonical branding. It suits me. I am not complaining.

Regards
 

unity7 is still maintained by the [community]("https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev") and it is just one sudo apt install ubuntu-unity-desktop away and then logout and login (if use touchpad also install xserver-xorg-input-synaptics) I am happily using it right now on Ubuntu20.04 (and 18.04 before). Much smoother, faster and a lot more functional than gnome shell. Gnome shell is unusable for many users without tons of hacks in the form of poorly maintained addons (many of which will break when next gnome shell releases, the internet is littered with dead gs addons)

Ubuntu 20.04 has a long life ahead and by the time it reaches eol god knows what new alternatives will be available. Gnome shell is frustrating to use for me. In focal unity7 uses nemo to draw the desktop and it is extremely easy and smooth to go all the way to use it as the default file manager. This is exactly what I  am doing right now (the new nautilus is pita for simple things like making a .desktop launcher in ~/.local/share/applications works) There have been talks to fork unity away from gnome which breaks everything everytime a new release comes out, if there are other shells available and more or less compatible with older gnome all the better.

---

