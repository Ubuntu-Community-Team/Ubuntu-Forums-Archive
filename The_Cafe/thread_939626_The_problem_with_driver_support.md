---
title: "The problem with driver support"
date: 2008-10-06
forum: The Cafe
---

### Post by davidryder on 2008-10-06
One of the biggest problems IMO with linux is Wireless card support - which isn't any direct fault of any specific distribution but I wonder if it has anything to do with all the different distributions?

Is it more difficult for manufacturers to develop drivers when there are so many distributions to code for or is it something else?

---

### Post by Tomosaur on 2008-10-06
> **davidryder said:**
> One of the biggest problems IMO with linux is Wireless card support - which isn't any direct fault of any specific distribution but I wonder if it has anything to do with all the different distributions?

Is it more difficult for manufacturers to develop drivers when there are so many distributions to code for or is it something else?

Not really - drivers are managed and executed by the kernel (which is the same across distributions, excepting kernel version - which would just be like saying 'this drivers requires Windows 2000 or later, so isn't really an issue), so it is either laziness, or the developers just don't really care whether Linux users can use their hardware.

There is no difference between a driver that can be used on Ubuntu and a driver that can be used on Gentoo - **if** the developer isn't a moron and does something ridiculously distro-specific (and I'm struggling to think of something they could or would do).

The only real issue is the package manager for the distro - and even this isn't really that big of an issue for drivers. The package manager just provides a uniform way to install stuff - but it is not REQUIRED for the package manager to be used.

The number of distributions and desktop environments is really more of an issue for actual applications. Even catering just to the 2 most popular DEs (Gnome and KDE) is a pain. This is a real problem which needs to be addressed before commercial developers are likely to start taking Linux seriously. The good news is that there is work ongoing in this area.

So no - there is no REAL reason for proprietary driver developers to not develop a version for Linux. Yes there are minor problems depending on kernel version and so on - but nothing really that would stop wireless driver developers releasing Linux drivers.

---

### Post by jrusso2 on 2008-10-06
That does not explain why Linux constantly breaks drivers that were working. 

Intel is open source and it still is broken often.

Atheros was working and then was broken, etc.

---

### Post by LaRoza on 2008-10-06
> **jrusso2 said:**
> That does not explain why Linux constantly breaks drivers that were working. 

Any change will result in breaking, look at Windows and OS X. This is not a Linux issue.

> 
Intel is open source and it still is broken often.


Works perfectly for me.

---

### Post by Tomosaur on 2008-10-06
> **jrusso2 said:**
> That does not explain why Linux constantly breaks drivers that were working. 

Intel is open source and it still is broken often.

Atheros was working and then was broken, etc.

This could be a number of issues. The first is deprecation - where a function is removed or made obsolete by a new function. Unless the driver developers keep up to date, things will eventually begin to fall apart. Updating the kernel or various libraries can cause this - but it's not a Linux issue, just one of the problems that software developers have to overcome regardless of OS. The reason this problem doesn't appear to affect Windows so obviously is that the Windows devs are REQUIRED to make things backwards compatible (people pay for Windows, Microsoft has no right to just make stuff stop working with a system update). This means that old functionality needs to at LEAST be emulated in newer versions of Windows. This leads to bugs, security issues, and general unnecessary garbage building up over time. It is also why on Windows, you have the option of running stuff in compatibility mode for older versions of Windows.

Linux devs on the other hand, are under no real obligation to allow old stuff to keep working, so if something gets deprecated or removed, then software devs need to keep up to date. In reality this isn't quite as harsh as that, but these things do happen. There are only really two choices - keep the kernel and core libraries backwards compatible forever (which is a maintenance nightmare in itself, but also leads to other problems which propogate throughout the Linux universe and generally detract from the whole), or do what is best for Linux in general and allow third-party devs to keep up. The Linux way allows everything to be kept lean and mean, rather than old, insecure, and crappy.

On the other hand - open-source drivers are constantly under refinement. If they're still in beta (which many are - perpetually), then you should expect breakage and problems while improvements are ongoing. Sometimes stuff will stop working for a particular segment of users with a very particular piece of hardware - very rarely does a complete breakage occur for everyone.

It's just a case of either-or really. Either you follow the 'ensure compatibility' model, where newer versions of the OS and libraries allow older drivers to function (which leads to security issues, maintenance issues, and other problems), or you keep focused on what is important and allow lazy developers / inactive projects to become redundant and obsolete. At the end of the day it comes down to driver developers - it is their job to ensure their drivers work, not the people who develop the libraries and OS which the driver relies on.

---

