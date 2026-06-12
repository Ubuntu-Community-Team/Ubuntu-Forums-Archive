---
title: "Need something to use my laptop as a network bridge *only*"
date: 2009-10-13
forum: The Cafe
---

### Post by TheOnlyMrK on 2009-10-13
I need a small and simple distro that will basically fit on a CD, or 1GB flash drive, and all I need it to do is take the WiFi connection and bridge it to the Ethernet card so it can plug into my router and provide internet to the rest of the house. I was using Windows 7 (the current OS installed on the computer) to bridge connections as that was simple point and click to do, but after a few days the laptop would really start to freeze up to where it's so bad it can't handle the simple internet traffic and made the laptop overheat. It's a very crappy laptop that easily can reach 160F. So I need a very simple lightweight distro that can perform this simple task and preferably as easy to set up as logging into any normal router. I've seen a lot of Linux router distros but I'm clueless as what to choose because most of their websites are poorly made/documented.

Also I know this isn't really Ubuntu relevant, just this place is a lot faster/better at answering questions then Cnet Forums Linux section is and I kind of need help fast with this.

Laptop: Intel Celeron M at 1.6Ghz, 1GB RAM, 40GB hard drive.
Note: I can not use the hard drive as Windows 7 needs to stay on there due to the laptop is used as a GPS on road trips so we need Microsoft Streets & Trips.

---

### Post by pookiebear on 2009-10-13
[http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

I have used untangle but not sure how lightweight it is? It runs on a p3 however.

---

### Post by pookiebear on 2009-10-13
[http://en.wikipedia.org/wiki/Coyote_Linux](http://en.wikipedia.org/wiki/Coyote_Linux)

that one looks real lightweight.

---

### Post by ukripper on 2009-10-13
> **TheOnlyMrK said:**
> I need a small and simple distro that will basically fit on a CD, or 1GB flash drive, and all I need it to do is take the WiFi connection and bridge it to the Ethernet card so it can plug into my router and provide internet to the rest of the house. I was using Windows 7 (the current OS installed on the computer) to bridge connections as that was simple point and click to do, but after a few days the laptop would really start to freeze up to where it's so bad it can't handle the simple internet traffic and made the laptop overheat. It's a very crappy laptop that easily can reach 160F. So I need a very simple lightweight distro that can perform this simple task and preferably as easy to set up as logging into any normal router. I've seen a lot of Linux router distros but I'm clueless as what to choose because most of their websites are poorly made/documented.

Also I know this isn't really Ubuntu relevant, just this place is a lot faster/better at answering questions then Cnet Forums Linux section is and I kind of need help fast with this.

Laptop: Intel Celeron M at 1.6Ghz, 1GB RAM, 40GB hard drive.
Note: I can not use the hard drive as Windows 7 needs to stay on there due to the laptop is used as a GPS on road trips so we need Microsoft Streets & Trips.

Crunchbang can do the trick and it is based on ubuntu which is another plus. [http://www.pendrivelinux.com/crunchbang-linux-flash-drive-install-via-cd/](http://www.pendrivelinux.com/crunchbang-linux-flash-drive-install-via-cd/)

---

### Post by hessiess on 2009-10-13
> 
can not use the hard drive as Windows 7 needs to stay on there due to the laptop is used as a GPS on road trips so we need Microsoft Streets & Trips.


Why not just dual boot it?

---

### Post by pookiebear on 2009-10-13
or you can get an older linksys wap54 and set it for client/repeater mode. or a wrt54g and load wrt-dd (a linux firmware for it) it has some neat tricks you can do with it.

---

### Post by TheOnlyMrK on 2009-10-13
> **pookiebear said:**
> [http://en.wikipedia.org/wiki/Coyote_Linux](http://en.wikipedia.org/wiki/Coyote_Linux)

that one looks real lightweight.
I attempted to use Coyote Linux last night but the CD install requires to be installed to the hard drive, and I can't use the floppy drive install since the laptop doesn't have a floppy drive. So I'm skipping it for now but definitely not forgetting it, because I saw a few screenshots of it and it looked pretty good.
[ ]("http://en.wikipedia.org/wiki/Coyote_Linux")

---

### Post by TheOnlyMrK on 2009-10-13
> **hessiess said:**
> Why not just dual boot it?
If I can find a router distro that supports WiFi cards and dual-booting that would work great, but I was doubting their would be such a thing.

---

### Post by TheOnlyMrK on 2009-10-13
> **pookiebear said:**
> or you can get an older linksys wap54 and set it for client/repeater mode. or a wrt54g and load wrt-dd (a linux firmware for it) it has some neat tricks you can do with it.
I'm going to see if I can try that Untangle you recommended earlier, plus the main thing I needed it for was to use the WiFi card off the laptop to get internet. Are you saying theirs a way I could use some routers as a WiFi card? Because he has a few laying around.

---

### Post by amingv on 2009-10-13
> **TheOnlyMrK said:**
> If I can find a router distro that supports WiFi cards and dual-booting that would work great, but I was doubting their would be such a thing.

[Smoothwall]("http://www.smoothwall.org/") supports wifi and is very light and easy to use, though hardly customizable at all. Maybe give it a try?

---

### Post by hessiess on 2009-10-13
> **TheOnlyMrK said:**
> If I can find a router distro that supports WiFi cards and dual-booting that would work great, but I was doubting their would be such a thing.

Anything Linux based will be dual bootable with GRUB, would probably need some manual editing tho.

---

### Post by TheOnlyMrK on 2009-10-13
Well I'm going to try Untangle right now, and still have the choices of SmoothWall, Coyote Linux, or Crunchbang. So I'm hoping I can find something good out of all of those. I'm going to see if I can get one of them to install to my flash drive since I'm doubting any of these are able to dual-boot without some modding.

---

