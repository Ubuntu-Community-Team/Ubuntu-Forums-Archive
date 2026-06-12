---
title: "Xenial Xerus is now open for development"
date: 2015-10-27
forum: Ubuntu Development Version
---

### Post by novatillasku on 2015-10-27
Xenial Xerus is now open for development
[https://lists.ubuntu.com/archives/ubuntu-devel/2015-October/038956.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2015-October/038956.html")

---

### Post by v3.xx on 2015-10-27
So are you running it?

---

### Post by flocculant on 2015-10-27
> **v3.xx said:**
> So are you running it?

are you?

---

### Post by QDR06VV9 on 2015-10-27
Ew Ew Ew Pick me!:D
Nah he is way to cautious!!(Joke)

---

### Post by sammiev on 2015-10-27
Time to play...

[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

---

### Post by novatillasku on 2015-10-27
And there's Daily Build!
[http://cdimage.ubuntu.com/daily-live/current/]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by grahammechanical on 2015-10-27
Some of us switched our repositories to xenial on wily release day. A new lsb-release file was among the first updates after willy release. 

> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial


Some of us weren't waiting for an ISO image to be built. Although we are still waiting for the moderators to change the welcome banner on this section of the forum. :)

---

### Post by tista on 2015-10-27
@sammiev,

Thanks for the info of daily-build... :)
OK. Let's play.

Regards.

---

### Post by kansasnoob on 2015-10-27
I think the last of the daily builds was added to the QA Tracker earlier today:

[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds)

I hope I can get an installation of Ubuntu running on this hardware:

AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

Fresh installs of Wily failed (nomodeset would work but X was borked post-install with both nouveau and nvidia drivers):

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147)

As did upgrades from Vivid:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1508157](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1508157)

That upgrade bug should be all fixed within the next 24 hours.

---

### Post by v3.xx on 2015-10-27
> **flocculant said:**
> are you?

Got virtualbox loaded from the repositories on mate 16o4 with a 16o4 guest.

---

### Post by PaulW2U on 2015-10-28
> **grahammechanical said:**
> Some of us switched our repositories to xenial on wily release day. A new lsb-release file was among the first updates after willy release.
I was there from Wily release day+1 :)
> **grahammechanical said:**
> Some of us weren't waiting for an ISO image to be built. Although we are still waiting for the moderators to change the welcome banner on this section of the forum. :)
Now changed. :)

I was using Wily from about two months into the development cycle and the only problem that I had was that a couple of applications wouldn't run for a few hours awaiting other updates to become available. It's great to see how things have changed from the 11.04, 11.10 and 12.04 days when I was faced with endless problems before I headed for the apparent safety of Kubuntu and Xubuntu.

For the Xenial cycle I'm very much back with Ubuntu. So far so good but I'll be rebooting every other day or so just to make sure that whatever I have installed is bootable.

---

### Post by balloons on 2015-10-28
Stopping by to say, devel pushed my install over the edge, and I'm all Xenial now after upgrading today. I still get this fun bit though :-(

W: Conflicting distribution: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) devel InRelease (expected devel but got xenial)
W: Conflicting distribution: [http://security.ubuntu.com](http://security.ubuntu.com) devel-security InRelease (expected devel-security but got xenial)
W: Conflicting distribution: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) devel-updates InRelease (expected devel-updates but got xenial)
W: Conflicting distribution: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) devel-backports InRelease (expected devel-backports but got xenial)

---

### Post by grahammechanical on 2015-10-28
I have had both a standard repository wily and a devel repository wily from the beginning. The devel wily rolled over to xenial but it was stuck on the 4.0.0 kernel and never got the 4.1.0 kernel and only got the 4.2.0 kernel after xenial began to get updates. Strange stuff happens at times.

---

### Post by zika on 2015-10-28
> **balloons said:**
> Stopping by to say, devel pushed my install over the edge, and I'm all Xenial now after upgrading today. I still get this fun bit though :-(

W: Conflicting distribution: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) devel InRelease (expected devel but got xenial)
W: Conflicting distribution: [http://security.ubuntu.com](http://security.ubuntu.com) devel-security InRelease (expected devel-security but got xenial)
W: Conflicting distribution: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) devel-updates InRelease (expected devel-updates but got xenial)
W: Conflicting distribution: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) devel-backports InRelease (expected devel-backports but got xenial)To put it most simple: there is no real devel branch and files on server(s) but only redirection (a.k.a. symbolic link) so this is just warning that that has really happened. Once we get rolling distribution devel be real branch and xenial and such will be branches that will have limited lifetime... So, that is what should be expected and it is OK.
Update: It is nice that we can use devel also in PPAs so that devel points to the latest branch in each and every PPA be it Vivid, Wily or Xenial... ;) Nice.

---

