---
title: "Will Ubuntu 14.04 support tablets"
date: 2014-04-03
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxmint7771 on 2014-04-03
I have downloaded Ubuntu 14.04 and I love it but I'm wondering whether it supports tablets or not?

---

### Post by 3rdalbum on 2014-04-04
What exactly do you mean by that?

There is an Ubuntu Touch image that can be installed onto Nexus tablets, but not any other sorts of tablets as far as I know.

You can install regular Ubuntu onto x86-based tablets (the ones that run Windows 8) because they are ordinary PCs. However the user interface is not entirely optimized for touch.

If you simply want to plug your tablet into your computer, then yes any Android tablet will plug into Ubuntu for modifying the internal storage or internet tethering.

---

### Post by linuxmint7771 on 2014-04-04
I thought that everY Ubuntu iso will support touchscreens from Ubuntu 14.04 onward!! Isn't that what Mr shuttleworth said in 2011?

---

### Post by mikewhatever on 2014-04-04
It will probably work on [x86]("http://en.wikipedia.org/wiki/X86") tablets, if you can find any. Most tablets are [ARM]("http://en.wikipedia.org/wiki/ARM_architecture") based, and it's hardly possible to support all variations.

Instead of asking a generic question, I'd rather ask about a specific tablet, ... perhaps the one you might be interested in.

---

### Post by grahammechanical on 2014-04-04
> **linuxmint7771 said:**
> I thought that everY Ubuntu iso will support touchscreens from Ubuntu 14.04 onward!! Isn't that what Mr shuttleworth said in 2011?

Touch screens are not the same things as tablets!!. Ubuntu 14.04 desktop most likely does support touch screen monitors. I do not own a touch screen monitor so I cannot speak from personal experience. 

But you specifically asked about Ubuntu 14.04 supporting tablets. The intention from the start has been to make it possible for OEMs to pre-install Ubuntu on their mobile devices for retail. It has never been the intention to make Ubuntu available for installation for mobile devices in the same way that Ubuntu is available for installation on desktop and laptop machines. That is expecting too much from a small organisation that does not charge for the download and installation of Ubuntu.

The Ubuntu developers do have a convergence strategy which will produce one Ubuntu code base whether Ubuntu is running pre-installed on mobile devices or in an ISO image from installation on desktops/laptops but that will not happen for 14.04. May be 14.10 or 15.04.

[http://www.omgubuntu.co.uk/2013/10/system76-touchscreen-ubuntu-laptop-available-pre-order](http://www.omgubuntu.co.uk/2013/10/system76-touchscreen-ubuntu-laptop-available-pre-order)

---

### Post by 3rdalbum on 2014-04-05
> **linuxmint7771 said:**
> I thought that everY Ubuntu iso will support touchscreens from Ubuntu 14.04 onward!! Isn't that what Mr shuttleworth said in 2011?

It would have been very stupid of him to say that. Ubuntu has always supported touchscreens, and you can use a touchscreen with Ubuntu today. What he has said is that Ubuntu Desktop will have a user interface optimised for touch (Unity 8). While Unity 8 is present on Ubuntu Touch, it is not ready for Ubuntu Desktop. Work is ongoing.

---

### Post by linuxmint7771 on 2014-04-05
So you are saying that i can already install and run Ubuntu on tablets and convertible laptops. Is that right?

---

### Post by 3rdalbum on 2014-04-07
> **linuxmint7771 said:**
> So you are saying that i can already install and run Ubuntu on tablets and convertible laptops. Is that right?

No, you asked about touchscreens. Tablets have touchscreens, but they are not the same thing.

Laptops or tablets that have x86 CPUs can run Ubuntu; basically, if they can run Windows 8, they can run Ubuntu since these devices are just PCs. The touchscreen may or may not work depending on drivers. Ubuntu supports touchscreens, but it just comes down to whether the touchscreen on that tablet has a Linux driver.

If you have a tablet with a non-x86 CPU, for instance a Nexus 7 or an iPad or a Samsung Galaxy Tab, these tablets have ARM CPUs and do not work the same way as PCs. Ubuntu requires a special version to run on a Nexus 7 (Ubuntu Touch) but there is no version for iPads or Galaxy Tabs. You can't just download an Ubuntu ISO and install it to an ARM tablet the way you would with a PC. If you are looking at a tablet that runs Android or Windows RT (not Windows 8) then usually you can't get Ubuntu to run on it.

---

### Post by SurfaceUnits on 2014-04-07
The Gnomenu extension makes Gnome3 very touchy


[[img]http://i62.tinypic.com/b3v9g7_th.png[/img]](http://i62.tinypic.com/b3v9g7.png)

---

### Post by hello-p on 2014-06-09
Heya. I have just upgraded to 14.04 ubuntu from 13.04. Anyone know how to "enable ubuntu touch' ??

I am runnung 14.04 on a laptop with a wacom digitizer touch screen ( uses a stylus ) and of course this works as you would expect has done since I installed 12.04 on it some time ago... But ! - how do I get all the nice new 14.04 stuff working? Perhaps because it isn't multi - touch I just don't get it ? Or am I just a 'sudo apt-get touch' away from making this toughbook CF-19 into a hardnut tablet ?

Thanks

HP

---

### Post by grahammechanical on 2014-06-09
Please understand that Ubuntu Touch is not the same as Multitouch on Ubuntu. We are trying to avoid confusion and unrealistic expectations of what Ubuntu can do.

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

> [COLOR=#333333][FONT=Ubuntu Beta]Some applications support 2 finger gestures. However, note that 2 finger gestures require [/FONT][/COLOR][extra setup]("https://wiki.ubuntu.com/Multitouch/TouchpadSupport")[COLOR=#333333][FONT=Ubuntu Beta] for touchpads in Ubuntu. Also please note that your system may not be supported out of the box, or at all.[/FONT][/COLOR]

[https://wiki.ubuntu.com/Multitouch/TouchpadSupport](https://wiki.ubuntu.com/Multitouch/TouchpadSupport)

Please explain what you mean by "all the nice new 14.04 stuff."  Mobile devices use touch and swipe gestures and Ubuntu phones and tablets (when they appear for retail) will also operate by touch and swipe gestures.

None of the mobile touch and swipe code is in 14.04 because 14.04 is an LTS release and the code is not finished and no one wants unfinished code in an LTS release. We do not know exactly when the convergence of the Ubuntu mobile device code into the Ubuntu desktop code will be complete. Sometime between now and the release of 16.04 is about as accurate as it can get.

Part of the convergence strategy is to replace the X display server with the Mir display server that is being specially written by Ubuntu developers. So, there is a big switch over coming but it will not come to 14.04. Right now we can install on the desktop the core apps from Ubuntu for phones/tablets but they are still very much under development and apps like the phone dialer will not work if our desktop motherboard does not have the electronics to act as a mobile phone.

Ubuntu mobile devices will run on Mir with Unity 8 which is Unity 7 re-written to run on Mir. All that code will eventually come to Ubuntu on the desktop and along with it all the phone/tablet applications.

We install the touch core apps on the desktop through a PPA. In my experience the best results come from also installing the Ubuntu SDK.

[https://wiki.ubuntu.com/Touch/CoreApps/PPA](https://wiki.ubuntu.com/Touch/CoreApps/PPA)

Regards.

---

### Post by scollar1971 on 2014-06-16
I am playing with a older tablet trying to find a distro that 'it' likes the tablet is a HP Slate 2 it's ARM based atom 1.5ghz 2gb of ram .... Ubunto 14.04 installs nicely with support for hardware effortlessly however it is too demanding on the processor and it crawls ..... I've tried lubunto (because I know it and quite like it) however because 'onboard' does not become available during install I can't seem to.complete install ... Any help or suggestions would be greatly appreciated

---

