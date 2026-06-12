---
title: "Ubuntu over Debian for a server?"
date: 2006-02-28
forum: Server Platforms
---

### Post by batkins on 2006-02-28
Are there advantages to using Ubuntu over Debian for a server?  I use Ubuntu at home, but on a system that won't require much user interaction, should I stick with Debian?

---

### Post by JELaVallee on 2006-02-28
[QUOTE=batkins]Are there advantages to using Ubuntu over Debian for a server?  I use Ubuntu at home, but on a system that won't require much user interaction, should I stick with Debian?[/QUOTE]
Ubuntu can definitely run as a production or small/mid-business (SMB) server.  For SMB it's really ideal and I use one at home as a media, file, print and scan server in a headless mode.  I still run X on occasion for remoting/VNC'ing access, but it's really a very easy to maintain box.

The wiki has a section on the Ubuntu Instant Servers project [here]("https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/UbuntuInstantServer?highlight=%28server%29%7C%28ubuntu%29").

Their project launchpad is [here]("https://launchpad.net/products/ubuntu-instant-server")

Anyway... good luck!

cheers,
Etienne

---

### Post by jezjones on 2006-02-28
I use ubuntu on my desktop and laptop and on my dev servers at home.
However at work my dev server is debian because i wanted to ensure that it was very lean, and most of the software had to be built anyway so there was no use of the package management system. For instance to put a lamp type system together with oracle access was much easier from a minimal install of debian (i.e. without X).

Ubuntu is really good but i still think for complete control use debian.

I know this is just my opinion and i am happy for others to tell me why i should use ubuntu.

Jez

---

### Post by krewemaynard on 2006-02-28
I chose Ubuntu over Debian for my work serer simply because Sarge wouldn't recognize the SATA drives; Ubuntu did. The regular releases and Debian foundations don't hurt either. :)  I used to use Gentoo (which I still love, btw), but it got to be too much overhead and upkeep.

---

### Post by trentend on 2006-02-28
Speaking as a newbie, looking to deploy servers in a commercial environment, I chose Ubuntu for a number of reasons.

1. Based on Debian.
2. Good package management.
3. Available as server version, but also (I know it's really primarily a desktop distribution, but allow me the conceit given that this is the server forum) with Gnome and KDE based flavours (allows one basic skill set to provide deployment for all possible types of user/application).
4. Has a large and established community, with substantial distribution specific documentation (the various server configuration guides on howtoforge.com are my favourites).
5. Seems to have more momentum than any other current distribution, with essentially all of the software that I anticipate using expressly having some level of ubuntu support.
6. The critical factor: Regular release dates and guaranteed support - means security fixes are available for modern (where this is measured in months, rather than years as compared with Debian) hardware/software combinations.

It's not all been plain sailing, as I've been unable to get the 64bit version to work on my hardware (although this is less critical while Xen only comfortably supports 32bit).  On the other hand the improved server support in the next release looks potentially killer.

---

