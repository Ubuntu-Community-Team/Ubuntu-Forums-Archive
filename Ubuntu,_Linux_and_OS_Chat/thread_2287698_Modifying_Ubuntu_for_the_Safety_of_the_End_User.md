---
title: "Modifying Ubuntu for the Safety of the End User"
date: 2015-07-21
forum: Ubuntu, Linux and OS Chat
---

### Post by RocketPenguin on 2015-07-21
Helping the school's IT guy, and he has placed my on a task of re-purposing ~60 really old and slow Eee Asus Netbooks. I have found an OS (EasyPeasy) that runs really well on it, and would need help restricting a user account on it. These will be for students, and so the only access they need is internet (Chrome and Firefox), gimp and LibreOffice. Also need to be able to mount drives. They shouldn't be able to change settings, use the webcam, torrent (Transmission), etc. Basically, the only thing they should be able to do is log in, be able to open either a web browser, gimp, or a word processor, and save things to flash drives. Nothing more. How would i accomplish this?

EDIT: Also shouldn't be able to change/disable wifi. That will be set by the admin (Me/the IT guy) and will never change. SHouldn't be able to view important things either such as mac and IP addresses.

---

### Post by Vladlenin5000 on 2015-07-21
You have a commendable task ahead. I salute you :guitar:

A few comments...

- With 60 machines, hopefully the same model, you want to do one and image it.
- EasyPeasy is dormant, I'm afraid. And [this]("http://sourceforge.net/projects/ubuntu-eee/files/Developers_Releases/") is a huge red flag, the latest _alpha_ being released before Ubuntu 12.04. EasyPeasy seems to be based on the old Ubuntu Netbook Remix. You're certainly aware you shouldn't use unsupported, EoL releases without any possible security updates.
- One possible solution to buy that old underpowered toys a couple of years of life is to use Ubuntu 12.04 or at least something based on it that has also LTS status. Some will certainly suggest Lubuntu **14.04 LTS**, the Lubuntu based LXLE or Bento Linux.
- Considering that any of the previous alternatives has its caveats, an older looking, even less productive desktop that the unpolished UNR, precursor of the current Unity, being the worse problem, -and- considering the standard Ubuntu runs acceptably in that hardware (Atom + 1GB RAM) I would start by testing the current LTS in a live session. Try lighter alternative only if the standard Ubuntu proves to be too hardware intensive for such machines.

- Most if not all the users restrictions you want to enforce are already taken care of if the users are regular, non admin (non root) users.
- You can run any network connection without even any user accessible indicator but perhaps there are better or more elegant solutions.
- Automount for external USB devices is standard, nothing to do here.

---

### Post by RocketPenguin on 2015-07-21
> **Vladlenin5000 said:**
> You have a commendable task ahead. I salute you :guitar:

A few comments...

- With 60 machines, hopefully the same model, you want to do one and image it.
- EasyPeasy is dormant, I'm afraid. And [this]("http://sourceforge.net/projects/ubuntu-eee/files/Developers_Releases/") is a huge red flag, the latest _alpha_ being released before Ubuntu 12.04. EasyPeasy seems to be based on the old Ubuntu Netbook Remix. You're certainly aware you shouldn't use unsupported, EoL releases without any possible security updates.
- One possible solution to buy that old underpowered toys a couple of years of life is to use Ubuntu 12.04 or at least something based on it that has also LTS status. Some will certainly suggest Lubuntu **14.04 LTS**, the Lubuntu based LXLE or Bento Linux.
- Considering that any of the previous alternatives has its caveats, an older looking, even less productive desktop that the unpolished UNR, precursor of the current Unity, being the worse problem, -and- considering the standard Ubuntu runs acceptably in that hardware (Atom + 1GB RAM) I would start by testing the current LTS in a live session. Try lighter alternative only if the standard Ubuntu proves to be too hardware intensive for such machines.

- Most if not all the users restrictions you want to enforce are already taken care of if the users are regular, non admin (non root) users.
- You can run any network connection without even any user accessible indicator but perhaps there are better or more elegant solutions.
- Automount for external USB devices is standard, nothing to do here.

They are all the same, so yes, they would be imaged.

And yes, I know about that. I went and installed 10+ Linux distros including lubuntu, Ubuntu, mint, etc. And they all lag/run with bugs/are too much for these netbooks. The only OS' that did work is easypeasy, puppy Linux, porteus, and I think toutou was the last. I would prefer easypeasy because it is Ubuntu based. The only other decent running os was android. Elementary OS ran alright, but had graphical glitch errors.

I am not too fond of the fact that easypeasy is alpha, no longer supported, etc, but it seems to work the best/is Ubuntu based, which is something I know better than any other flavor. Of course, I could try on the other mentioned distros, but that would be a serious learning curve for me.

---

### Post by Irihapeti on 2015-07-21
Not all EeePC netbooks are created equal. What are the hardware specifications of these particular ones?

---

### Post by sammiev on 2015-07-21
> **linux junkie said:**
> 

I am not too fond of the fact that easypeasy is alpha, no longer supported, etc, but it seems to work the best/is Ubuntu based, which is something I know better than any other flavor. Of course, I could try on the other mentioned distros, but that would be a serious learning curve for me.

This would be the part I would be worried about but I know where you are coming from.

---

### Post by RocketPenguin on 2015-07-23
> **Irihapeti said:**
> Not all EeePC netbooks are created equal. What are the hardware specifications of these particular ones?


Sorry for late reply, haven't been able to look at them for the past few days. They are Eee PC Asus 1005ha netbooks.
Specs are as follows (From [Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220551")):

General
Brand
ASUS
Series
Eee PC Seashell
Model
1005HA-PU1X-BK
Part#
90OA1BB14111131U11HQ
Color
Crystal Black


Operating System
OS Provided
Windows XP Home


Processor
CPU Type
Intel Atom
CPU Speed
N280(1.66GHz)
CPU FSB
667MHz
CPU L2 Cache
512KB


Chipset
Chipset
Intel 945GSE


Display
Screen Size
10.1"
Widescreen Display
Yes
Display Type
WSVGA
Max Resolution
1024 x 600
Display Feature
LED backlight


Graphics
Graphics Processor
Intel GMA950
Video Memory
Shared system memory


Memory
Memory Speed
DDR2
Memory
1GB

---

### Post by Bucky Ball on 2015-07-24
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a good idea going for a spin that has poor support. Easypeasy is not supported by Canonical, nor is it officially supported on these forums, although you could post in 'Ubuntu/Debian based' section about it. I wouldn't go there as when it comes to breakage you will be pretty much on your own. 

Where I would go, and a steeper learning curve but worth it, is for a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD"), customise, then clone and create ISO for install on other machines.

With the mini.iso, you get the Ubuntu base kernel, that's it. You install the rest. In other words, once installed, you reboot to a login cursor, log in and the rest is up to you. A blank slate. You could install whatever desktop environment easypeasy uses and only the software you're after. For instance, on first boot, presuming EPeasy used lxde as the desktop environment, you could run something like:

```
sudo apt-get install lightdm firefox pcmanfm lxde
```

That would give you a desktop environment, a desktop manager, a file manager and a web browser. You could also install Synaptic Package Manager (apt-get install sypnaptic) for a graphical package manager. Research to see what else you might need, make a list prior to the install so you know what you are doing and prepare a full 'sudo apt-get install' line containing all apps you want to drag in. I find it better to start with the basics and pull stuff on as required. 

Once adequately tweaked, roll it out. :)

PS: You could go lighter and forget the desktop environment and just go for a window manager like openbox. Good luck.

---

### Post by Irihapeti on 2015-07-24
Those netbooks are probably better than the one that I have, which is an EeePC 900 with 1GB RAM and a grand total of 20 GB(!) storage.

I do more or less what Bucky Ball is describing - minimal install, add graphics and either Xubuntu-minimal or Openbox, and then the stuff that I want. It's not the fastest thing in the west, but it's more than adequate for me when I'm out and about.

---

### Post by Geoffrey_Arndt on 2015-07-24
It might also be interesting to test an install of Enlightenment desktop (E17) or (E19).   Bodhi Linux is based on Ubuntu, and puts out a beautiful distro that runs fast on older, lesser hardware.   Worth a shot, as the Bodhi is sure a lot nicer to look at than Lubuntu or Openbox, Fluxbox etc.  Just go to [http://www.distrowatch.com](http://www.distrowatch.com) and see if it's something you'd want to check out before making final choice.

---

### Post by BazBear on 2015-07-27
I was going to say that I am running Lubuntu 14.04.2 on that same model netbook, Eee PC 1005ha and it runs pretty well; but then I recalled I had upgraded the RAM to 2GB even before I tried any version of Linux on it. The minimal install idea described above is probably the best option (assuming that buying and installing 60 2GB RAM cards is out of the question).

---

### Post by sudodus on 2015-07-28
1 GB RAM should be enough to run Lubuntu pretty well. See this link

[Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

---

