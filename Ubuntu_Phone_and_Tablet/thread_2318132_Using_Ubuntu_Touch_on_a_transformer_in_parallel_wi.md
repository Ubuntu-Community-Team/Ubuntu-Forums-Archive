---
title: "Using Ubuntu Touch on a transformer in parallel with Ubuntu Desktop. Is it possible?"
date: 2016-03-23
forum: Ubuntu Phone and Tablet
---

### Post by LuK_green on 2016-03-23
Hi. I have Lenovo Yoga Pro 2 and it's a transformer. It can go from a laptop into a tablet and it has a touchscreen. Windows 8.1 that ships with the device supports working with the device in a tablet position but Ubuntu, unfortunately, doesn't. So now I practically can't use tablet mode. But as I know there is an Ubuntu version suited for working with touchscreens. There is a constant flow of news about Ubuntu Phones and Ubuntu Tablets. What I would like is for Ubuntu to go into a Ubuntu Desktop mode in a laptop position, and to go into Ubuntu Touch mode when in a tablet position. But I couldn't figure out even how to install Ubuntu Touch on my Ubuntu Desktop, let alone the question of them living together and switching from one to another. Do you think this is even possible? If so, how could it be done?

---

### Post by grahammechanical on 2016-03-23
> But I couldn't figure out even how to install Ubuntu Touch on my Ubuntu Desktop,

We do not do that. We cannot do that. Forget that approach. Ubuntu Touch is now officially Ubuntu for Devices and at this point of development we should think of it as a separate OS from Ubuntu Desktop.

To start with, at present the Ubuntu for Devices images are built mainly for ARM CPUs. There are versions for x86 CPUs and I have even seen a video demonstrating Ubuntu for Devices running on an x86 tablet.

The situation is this. Install Ubuntu and we do not get "convergence." That is a switch between desktop and tablet modes that you would like. Install Ubuntu for Devices and we may very well get convergence but at present without the default desktop applications that we expect with a desktop OS.

The long term aim is to have one Ubuntu code base which will be Ubuntu desktop when installed on a desktop. Ubuntu tablet when installed on tablet and switching to desktop mode if bluetooth keyboard and mouse are connected and the tablet is connected to a monitor (touch screen or not) by HDMI cable. Ubuntu phone when installed on a phone.

The implementation for that is future. There are some hopes that something like this will be available by the release of Ubuntu 16.10 but. learning from past mistakes, the developers will not release the code until it is ready for release. No one is promising anything by the release of 16.10.

We might learn something from the next Ubuntu Online Summit where the developers discuss their desires and intentions for Ubuntu 16.10. The schedule is not yet finalised.

[http://summit.ubuntu.com/uos-1505/](http://summit.ubuntu.com/uos-1505/)

Look for sessions on convergence.

Regards.

---

### Post by Jon_Thomas on 2016-03-31
Would it be simpler at this point to just use the KDE Netbook interface?  I have tried it in the past and it seems like a natural fit for touch interface.

Either that or the latest Gnome 3, which I have tried on my own tablet.

---

