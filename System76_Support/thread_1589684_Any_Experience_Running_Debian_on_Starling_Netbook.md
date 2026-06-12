---
title: "Any Experience Running Debian on Starling Netbook???"
date: 2010-10-06
forum: System76 Support
---

### Post by hilltop_yodeler on 2010-10-06
I've come across a reasonably priced used Starling netbook that's for sale, and is about one year old.  Although I do run Ubuntu on my desktop at work, most of my machines are running [CrunchBang Linux]("http://crunchbanglinux.org/"), which is built from Debian Squeeze, and this is what I would be installing on the Starling.  OpenBox is the window manager that I use, which also works great on a netbook because you can control the menu sizes very easily.

My concern is regarding all of the drivers that need to be installed for the Starling.  I see that there is a [System76 netbook repository]("http://planet76.com/repositories/") available.  All of the files in the repository are .deb files, and even though I would not be running Ubuntu, I'm assuming that I should be able to install these drivers successfully on a Debian system running on the Starling, correct?  

Does anyone have any experience with this?  

Thank you in advance for your help.

---

### Post by oOarthurOo on 2010-10-07
It would depend on what the package dependencies of that driver package are. The fewer, the higher the chance of success. Provided there is source provided in addition to deb files you could always just create your own deb.

---

### Post by isantop on 2010-10-07
The whole driver is written in python, and is open source, so you can look inside and find out what the system is doing. From there, you can create a script, program, or deb, depending on what you want.

Unfortunately, the driver only runs on Ubuntu and it's derivatives (Kubuntu, Xubuntu, etc.). It is possible to modify the program to be able to run, but it can be tricky, and everything may not work properly. Primarily, I'm concerned about the webcam and wireless. If you use the latest r8192se_pci realtek driver. You may need to download and compile this from source. The webcam is now supported out of the box by Ubuntu, but for crunchbang, you may need the latest uvc code. Barring those issues, though, I think crunchbang would run fine on this system.

---

### Post by ranch hand on 2010-10-07
I am not really trying to hijack this thread but I am wondering if there is any possibility of Sys76 developing drivers for Debian.

That is why I checked this thread.

With the way Ubuntu seems headed I think there may be more and more interest in Debian and other Debian off shoots.

---

