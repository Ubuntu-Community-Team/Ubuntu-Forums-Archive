---
title: "Is it worth keeping Linpus Linux Lite?"
date: 2009-02-18
forum: The Cafe
---

### Post by daniel014 on 2009-02-18
I might be getting an Acer Aspire One netbook with the 120GB HDD. I have seen screenshots of Linpus, the distro it comes with but I am planning to install Ubuntu when I get the netbook anyway.

Is Linpus good? Should I keep it and dual boot?

---

### Post by 3rdalbum on 2009-02-18
Linpus is faster than Ubuntu (especially for booting) and gives you an extra hour of battery life.

I removed Linpus after a few days and put Ubuntu on. I thought Linpus would be alright once I got access to Fedora's repositories, but the package manager was simply BROKEN and almost nothing would install successfully. Updating the package list took absolutely forever as well - we're talking about 15 minutes. Ubuntu is very happy on this machine, but it could do with another 512mb of RAM.

---

### Post by Tux Aubrey on 2009-02-18
I agree with 3rdalbum about boot times and battery life with distros other than Linpus Lite.  There are a few tweaks you can do to improve the boot but battery life stays at 2hrs no matter what I do.  And the Linpus package manager is just awful (when it works at all) after using apt!

I installed Xubuntu 8.04.1 originally and it was fine and it was even better when I switched to e17 as the WM/DE. I'm not sure how Gnome or KDE would go.

The upgrade to 8.10 was a nightmare (but I eventually got there after many many tries) - but I suspect that has more to do with hardware (SDD) tweaks I did than 'buntu.

I did need to use Madwifi drivers for wifi under 'buntu.

The Moblin project may deliver us a faster kernel and some better compatibility - I booted the second Moblin alpha "demo" distro from a usb stick and it was less than 15 seconds to boot!  

But I'll stick with my Xubuntu+e17 until a Moblin-buntu-e17 base is ready.

---

### Post by daniel014 on 2009-02-18
> ...it could do with another 512mb of RAM

Do you have the 512MB RAM Aspire One or the 1GB version?

I will be getting the 1GB RAM version.

---

### Post by nothingspecial on 2009-02-18
Ubuntu runs smooth as a sausage on my wife`s 512 acer.

Linpus lasted about 20 mins. Horrible.

---

### Post by Vince4Amy on 2009-02-18
It's fine to keep but very limited. Even when you do get to the packages it's on the same level as Fedora 8.

I did initially put Fedora 10 on there but the graphics were really slow using the intel driver.

I then put Ubuntu on it which worked well and an update broke it so I knew it was a bad idea to even think of trusting Ubuntu again.

OpenSuSE had various problems with wireless.

Debian I couldn't install from a USB Flash drive without it complaining about there being no CD.

I'm now running it with Arch and XFCE and it's really fast. Though use WICD for network stuff.

---

### Post by 3rdalbum on 2009-02-18
I've got the 512mb version; that was literally the only Aspire One with Linux that I could get (I thought it was the only one available?) and actually one of only two Linux-based netbooks I could get.

Tux Aubrey: I'm using Gnome. Well, it's the netbook remix interface, but there's still a full copy of Gnome running underneath. Doesn't run too well with 512mb of RAM and it thrashes the SSD a bit, but it runs and it's flexible enough for me.

---

### Post by s.fox on 2009-02-18
I like to use Linpus Lite, of course i did hack away at it to make it more usable, such as enabling the normal desktop via the desktop switcher. 

Without customizing the OS iIts good enough just to check emails,  browse the web and type up a few notes.  If you want to do anything other than that I would probably say either hack it apart or install a new OS.   I would probably say Kubuntu is the best bet,  though others may disagree.   

I do not and would not recommend that you use Linpus as your main OS  if you intend to do anything other than check emails,  browse the web or typre up a few quick notes, as the repositories are limited.  With my customized version of the OS it is a danger that if I install any of the updates from acer then it will undo all my hard work,  and may even break it completely.  

I suppose it boils down what you want to do with it.  Either way a great online community I look at is [here]("http://www.aspireoneuser.com/forum/"), though i take no responsibility for anything that happens if you follow any of the turorials on that site.

-Ash R

---

### Post by Rotaj on 2009-02-18
As with most things, taste is a matter of exposure to other views, whether it is music , literature, art, or even OS's. 

Linpus offers a starting point. 

I am currently using Linux4one. Everything works and it is nice but it is not the right fit for me. Waiting to see if Tux's labors on this machine will be instituted into the next release of OzOS. 

An interesting viewpoint to take is, would there be any question if it were regarding XP?

---

### Post by gymophett on 2009-02-18
To be quick.
Linpus sucks.
Go with Ubuntu.

---

### Post by daniel014 on 2009-02-19
Actually, never mind, I think I'm getting the MSI Wind U100.

Thanks anyway for your opinions :)

---

### Post by gnomeuser on 2009-02-19
It depends, if you don't need to do any other tasks than what can be done in the specialised interface then I would keep it. It is stable, the setup is all done for you (remembering that a raw install of any distro is likely very suboptimal for any netbook without significant tweaking and understanding of the platform).

If you however intend to use it as a regular laptop, then you may want to do an install of a more regular desktop Linux distro. You should examine what special requirements are for the model you end up picking. This includes such things as picking optimal partition schemes and filesystems, Fedora kernel maintainer Dave Jones had some nice posting on his blog on this subject you may want to search for them.

I would recommend starting out with the distro that is shipped on your netbook, then if you hit any showstopper issues, research the requirements and install a distro you are comfortable with.

---

