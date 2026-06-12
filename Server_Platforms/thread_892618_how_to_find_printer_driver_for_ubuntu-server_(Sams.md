---
title: "how to find printer driver for ubuntu-server? (Samsung ML-2510)"
date: 2008-08-17
forum: Server Platforms
---

### Post by stairwayoflight on 2008-08-17
Hello,

I have a Samsung ML-2510 laser printer. I can configure it using the graphical printing administration dialog from ubuntu-desktop.

However I am having difficulty configuring it from ubuntu-server. I have installed only ssh, cupsys, and elinks packages. When I connect to cups' web admin interface on [http://localhost:631/](http://localhost:631/), I can browse foomatic printer drivers but my model isn't listed.

It is listed explicitly by the system-config-printer utility shipped with ubuntu-desktop. (Of course I am using Hardy in both cases.)

I would like to install the package(s) with the necessary drivers/filters.

---

### Post by stairwayoflight on 2008-08-18
Well, I didn't find exactly what I was looking for, but I solved my problem. I'm posting about it in case it helps anyone else.

The best how-to I found on cups configuration for debian/ubuntu is:
[http://forums.debian.net/viewtopic.php?t=10438](http://forums.debian.net/viewtopic.php?t=10438)

Thanks to Tina for a great job.

The reason for my initial question was two-fold:
1) The printer "just works(tm)" in ubuntu-desktop...although I couldn't find my printer mentioned in the "installed files" property of installed packages, I knew the driver had to be there somewhere!
2) The page at Open Printing cites various problems and bugs users experienced with the drivers supplied by Samsung. I wanted to use the driver I already knew worked.

After some more digging around, I reread the [Open Printing page](http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2510) and found what I had missed the last time around--one user said the new drivers on the Samsung site apparently had fixed the bugs people were complaining about.

---

