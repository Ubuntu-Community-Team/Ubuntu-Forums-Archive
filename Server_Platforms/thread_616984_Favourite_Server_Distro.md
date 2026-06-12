---
title: "Favourite Server Distro"
date: 2007-11-18
forum: Server Platforms
---

### Post by Mineral on 2007-11-18
I know this is a ubuntu forum, but I assume some of you would use other versions of linux for servers. I am new to linux and I want to set up a server at some stage running linux. Would you recommend I just stick with ubuntu for my server or are they better distros I could choose?

Thanks for any help.

---

### Post by HermanAB on 2007-11-18
Well, Mandriva has better wizards, but if you don't care much for wizards, then any distribution except maybe DSL and Puppy Linux will do!

I can tell you which distro is the worst: RedHat.  Running RHEL5 is like discovering the secret of time travel and going back 3 years - almost as bad as BSD.

---

### Post by Mineral on 2007-11-19
lol, well lucky I asked, because I was going to try redhat. Well this isn't an immediate concern of mine, so I will see what some others say.

---

### Post by netlogic on 2007-11-19
For home, go bleeding edge for the constant improvements toward applications. Of course, that means things will break. However, CentOs (free clone of RHEL), Debian (the original aptitude), and FreeBSD are great choices if your goal is to be very stable and making decisions for your company. I don't think having outdated packages are bad idea.  If this is for your company, you should buy certified RHEL or Suse Enterprise servers. Ubuntu recently started this, so I don't know what well it works.  The certified hardware servers will install out of box without knowing too much how kernel modules work. Also, they constantly update drivers, but they will lack latest features. I don't think outdated packages are a bad thing. If you are managing many nodes, you want things to work out of the box. The bleeding edge isn't good idea. Most workers will like you more when everything works and things don't break. Last thing you want is wondering if you broke it or your distro broke it.

So...

Servers
Home: Debian Unstable, latest Ubuntu,  and Fedora (super bleeding edge RHEL)
Work: RHEL, CENTOS, Xandros, and Suse Enterprise.
Work vanilla firewall: FreeBSD, and OpenBSD are good choice. You don't want to constantly upgrade firewalls. You only want to do them once every three to four years unless you have an insomnia.
For hardcore work firewall: just buy a rack unit. Roll your own special full feature firewall seems to be too much work.

Desktop (just in case you want others opinions about this) 
Work: Ubuntu LTS, CentOS, Xandros, Debian (stable branch). Suse Enterprise is so bloated.  I don't suggest their desktop.
Home:  Ubuntu is excellent.  You can also go through many other Linux at distrowatch.com

if your goal is quick and easy, go Xandros, but you have to pay few dollars. Setting shares and permissions on Xandros is samething as Windows. They have a hacked version of KDE KONQUEROR that works just like Windows file manager.

my 2cents

---

### Post by Gouki on 2007-11-19
I always used Debian for home servers. Don't really have access to the datacenter where I work, but the only thing remotely close to GNU/Linux in there is Z/OS for the mainframes.

So, Debian is my choice. 

Even on my two NSLU2 (Linksys). Running Debian for ARM architecture.

---

### Post by Mineral on 2007-11-19
Ah, thanks for all the replies. It will just be a home server, just for my own purposes for now. I just want to start learning about linux, and my first experiences after using ubuntu are good. Again, Thanks.

---

### Post by wirelessmonkey on 2007-11-20
I'd vote Slackware for stability and security, followed closesly by SuSE (opensuse 10.3 has really impressed me!) for ease of use.

---

### Post by p_quarles on 2007-11-20
+1 for Debian (the stable one). Nothing against anything else, but the stable version of Debian is built like a brick outhouse. You could say the same of CentOS, RHEL, Slackware or *BSD, but if you're familiar with Ubuntu, learning the few small differences in Debian will be a piece of cake. 

Ubuntu server edition itself will also work just fine for learning the ropes. It's much more bleeding edge than Debian Stable, though, so you can't expect the same stability.

---

### Post by prodezigner on 2007-11-21
Well, I was a big fan of Trustix 2.0 way back when, then some silly company bought 'em, put out 3.0 (they're at 3.0.5 right now), and practically ruined it. They're even killing the distro as we speak... literally, End of Life.

Ubuntu Server Ed. and CLI all the way for me. Right now I have LAMP + SSH + SAMBA + TorrentFlux installed, but I'm switching to SSH + SAMBA + rTorrent for my home server needs. I may even write a how-to on this little adventure.

---

### Post by Chayak on 2007-11-21
Home servers: Debian, Ubuntu, CentOS
Work servers: CentOS, RHEL, OpenBSD, Trixbox (for PBX).

If I have to cooperate with a windows network then I'll likely use SuSE just because I can install it to authenticate off a windows domain.  I know just about any linux distro can be made to but when it comes to administering large networks the less time I spend doing something the better as time quickly adds up.

---

