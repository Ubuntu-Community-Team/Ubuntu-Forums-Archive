---
title: "Desktop vs Server"
date: 2008-03-12
forum: Server Platforms
---

### Post by FlemmingJ on 2008-03-12
hi

I have setup an Ubunutu  Desktop 7.10. It has to work as fileserver, sole.
Before I procees I'd like to know what I would gain by using an Ubuntu Server 7.10 instead. E.g. performance and feature wise.

nay comments most welcome. Thanks a lot.

regards Flemming

---

### Post by renzokuken on 2008-03-12
you probably wouldnt gain much, Server version has all the server packages installed by default, but doen't come with a GUI (unless you install one)

Desktop will come with a range of apps that you wont use as a file server, but not all the server software, but this is easily installed via Synaptic.

In all honesty, there really isnt much difference if you're only using it as a fileserver, you can turn Server into Desktop and Desktop into Server simply by using apt/synaptic to install/uninstall specific software

---

### Post by njparton on 2008-03-12
I use the desktop distro to power a home built NAS and it works fine.

Now that I have it set up I've stopped the gdm service to stop gnome loading by default and I administer it via putty/SSH and webmin.

gnome is still there if I need it but I rarely do.

If you're new to linux go for the desktop edition :wink:

Performance differences will be negligable (if any) unless you have an old PC or push your hardware to the limit (and are running a desktop).

---

### Post by hyper_ch on 2008-03-12
the server edition has its kernel also tuned towards server tasks...

---

### Post by rickyjones on 2008-03-12
> **hyper_ch said:**
> the server edition has its kernel also tuned towards server tasks...

Could you post some example optimizations that the server kernel provides versus the desktop kernel?

Thanks,

-Richard

---

### Post by renzokuken on 2008-03-12
[http://www.enterprisenetworkingplanet.com/netos/article.php/3710641](http://www.enterprisenetworkingplanet.com/netos/article.php/3710641)

that may explain a few things

---

### Post by njparton on 2008-03-12
If you're just setting up a fileserver then the performance you see in reality will be much more reliant on the performance of your network, the network interfaces at each end, the file system used on the server etc etc.  Optimisations in the server distro compared to the desktop distro will be in no way as important for you.

For example, I have a gigabit network at home using CAT6 cabling.  The NICs at each end and the switch in the middle are all jumbo frame capable and this has been implemented.  The NAS drives shared are formatted using ext3 via a 3ware raid 1 array.

I get up to 70MB/s read and 35MB/s write performance from my Vista x64 (no SP) PC.  I've also tried the xfs file system and I got 50MB/s read and write so you can see the difference this soft of thing can make.

Don't worry about the distro for your needs focus elsewhere to improve performance :)

---

### Post by vpsville on 2008-03-12
> **rickyjones said:**
> Could you post some example optimizations that the server kernel provides versus the desktop kernel?

Thanks,

-Richard

The server can address more than 4 GB of RAM on 32bit processors.  The Desktop edition is limited to 4GB by default I believe.

The Desktop also has a graphical shell installed, which you don't really want on a server.  You can shut it off.

Thats about the only difference you'd notice on a personal server.

---

### Post by hyper_ch on 2008-03-13
also desktops can use more than 4gb using pae - which is not enabled by default.

---

### Post by njparton on 2008-03-13
The 4GB RAM issue isn't really relevant to just a file server.

You only really need that amount of ram if you're running _lots_ of services or doing something very intensive such as video editing.

Lots of people only use 512MB ram in fileservers without any problems.

---

