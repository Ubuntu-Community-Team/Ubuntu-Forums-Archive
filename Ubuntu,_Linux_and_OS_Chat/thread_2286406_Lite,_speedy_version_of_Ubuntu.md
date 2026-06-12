---
title: "Lite, speedy version of Ubuntu?"
date: 2015-07-11
forum: Ubuntu, Linux and OS Chat
---

### Post by baruch3 on 2015-07-11
I have two old Dell [Optiplex GX520]("http://www.cnet.com/products/dell-optiplex-gx520-celeron-d-326-2-53-ghz-monitor-none-series/specs/")s with Celeron 2.53ghz processors and 512 or 1gb RAM. I am trying to turn into computers that can run a speedy version of Ubuntu with primary job of having Firefox run as fast as possible and for it to strongly support Google Docs. I've installed the latest version of Ubuntu desktop 14.04.2 but it's just too slow. I was wondering if there is a lite, speedy version of Ubuntu that cuts out all the unnecessary junk and just focuses on turning it into a fast, speedy web browser.

I have heard of [Lbuntu]("http://lubuntu.net/") and I see that it's designed with this in mind but I don't know anyone running it or any reviews. I also also unaware of Ubuntu has it's own lite version that is optimized for older hardware

---

### Post by PhilGil on 2015-07-11
There are distros designed for very old machines that are even lighter, but Lubuntu is your best low-resource option amongst the 'buntus. Depending on your level of Linux experience you could also start from a minimal Ubuntu install and build from there. The biggest challenge is going to be your browser. Modern browsers such as Firefox and Chrome are far from lightweight; and can bring a system with 1GB of RAM or less to it's knees in short order. You might want to explore some of the lightweight browser options available, suck as Epiphany or Midori.

Remember that almost all Linux distros give you the option to try before you buy with a live USB/CD/DVD.

---

### Post by Bucky Ball on 2015-07-12
*Thread moved to **Ubuntu, Linux and OS Chat**.*

When it comes to the Ubuntu/Canonical supported family, yes, Lubuntu is where you want to go, or Xubuntu.

As mentioned, the [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") would suit best as far as lightness, depending on what you do with it, but that is a steeper learning curve. If you're willing, by all means, go there. That's all I use. ;)

The other you're thinking of is probably Ubuntu-core (there is also xubuntu-core and lubuntu-core). Not sure Ubuntu-core would be light enough, though. Lubuntu-core lighter than the regular Lubuntu.

---

### Post by Geoffrey_Arndt on 2015-07-12
Maybe good to go to [http://www.distrowatch.com](http://www.distrowatch.com) and peruse all the 100 or so distros on that site for info re use with ancient equipment.    I've read that Bodhi Linux (has ubuntu base), is fast and light.   Uses the Enlightenment (e17 or e19) desktops.

---

### Post by coldraven on 2015-07-12
This may be of interest: [http://www.theregister.co.uk/2015/07/09/lightweight_linuxes/](http://www.theregister.co.uk/2015/07/09/lightweight_linuxes/)

---

### Post by grahammechanical on 2015-07-12
Those machines have what Intel calls Dynamic Video Memory Technology. To put it another way. The system uses system memory as video memory.

[https://en.wikipedia.org/wiki/Dynamic_video_memory_technology](https://en.wikipedia.org/wiki/Dynamic_video_memory_technology)

And that will always have an effect on the user experience especially when visiting web sites that make excessive use of Adobe Flash elements. Do not build your hopes up. You will need a simple desktop environment without fancy effects to reduce the amount of system resources used by the system itself. And a simple web browser that does not try to do too much.

Regards.

---

### Post by kurt18947 on 2015-07-12
One not mentioned so far is Ubuntu-Mate. For a light distro I tend to prefer Xubuntu because I can set it up to fit my workflow  but Ubuntu-Mate works pretty well. I did have video issues when trying to install Mate on an HP 1000 mini and needed -nomodeset and -noacpi switches in order for it to work properly. Ubuntu-Mate is using about 400 MB. with Firefox open and about 330 without on a machine with 4 GB. installed.  I would think you'd be okay with 1 GB.+ RAM. Any chance of bumping up the RAM, perhaps via Ebay purchases? I've had quite good luck going that route, I just make sure that returns are permitted and as soon as possible after receiving it, I install the purchased sticks and run memtest on them for several hours. So far so good.

---

### Post by baruch3 on 2015-07-12
I've gone ahead and installed Lubuntu on both systems using the apt-get install lubuntu command. I rebooted and logged into Lubuntu. It is far speedier than Ubuntu and seems to have given these old PCs a new lease on life. I still have the option of logging into Ubuntu. Is there any downside to keeping Ubuntu on the system? Would things run more smoothly if I did a complete format and installed only Lubuntu? 

Thank you.

---

### Post by Bucky Ball on 2015-07-12
There is no downside. Lubuntu has a leaner set of default apps but you should find everything you are going to need. If you need anything else you can install from Synaptic Package Manager (at least that is the package manager Lubuntu used last time I looked). 

I'd go there and get rid of the Ubuntu bloat that you probably won't need. Lubuntu-core would be leaner again, but certainly, wipe the drive and install Lubuntu. Probably more upside and no downside on low spec machine. :)

If you have issues with the install please post a new thread in a support area (probably Installation & Upgrades). Good luck.

---

### Post by mastablasta on 2015-07-13
the downside is in desktop itself. for example Ubutnu may use some say network monitor that dispalys network status in fancy graphics. Lubuntu might use another monitor that will dispaly in more basic graphics the same info. the issue here is as you installed it you might not only have the "heavier" version of the two monitors, but also both versions running at the same time.

so reinstall will definitelly bring some clutter down. another option might be to just remove both desktops and then repeat the apt-get command to install only lubuntu.

---

### Post by baruch3 on 2015-07-13
> **mastablasta said:**
> the downside is in desktop itself. for example Ubutnu may use some say network monitor that dispalys network status in fancy graphics. Lubuntu might use another monitor that will dispaly in more basic graphics the same info. the issue here is as you installed it you might not only have the "heavier" version of the two monitors, but also both versions running at the same time.

so reinstall will definitelly bring some clutter down. another option might be to just remove both desktops and then repeat the apt-get command to install only lubuntu.

I've been looking for the commands to remove Ubuntu but the only ones I can find are for earlier versions and those commands error out. Thoughts?

BTW, the staff members using these machines report Lubuntu makes them useable.

---

### Post by vasa1 on 2015-07-13
> **baruch3 said:**
> ... I still have the option of logging into Ubuntu. Is there any downside to keeping Ubuntu on the system? Would things run more smoothly if I did a complete format and installed only Lubuntu?
...
The downside is that software you aren't using will keep getting updates (because the Ubuntu desktop is actively developed) and your menus maybe cluttered with (heavier) programs you don't use.

---

### Post by crl2 on 2015-07-31
I installed Lubuntu on a few old machines and my friends started using them with no help from me. All desktops should be like that! Unfortunately, here in France the keyboard and a few other things kept reverting to US. That happened also to Firefox, which came by default. It turns out that this implementation of FF uses an extension to set the language, and the extension doesn't get updated at the same time as the same program. I could fix the troubles after searching the web for solutions (and recommend another browser nobody has heard of) but in practice they make Lubuntu useless for people who don't live next door to a geek.

---

