---
title: "Linuxs Networks - Windows Networks"
date: 2007-05-10
forum: Server Platforms
---

### Post by SomethingCronic on 2007-05-10
Hi, hopefully someone here with experience of Linux only networks can help me out here as my experience is mainly with Windows domains.

I've been looking around find an alternative to Windows Update Services for Linux but can't quite work out how it would work.For those that may not know WSUS is a central server app that will download security updates (among others) from Micro$oft that can then be checked in and distributed to other PCs on the network. 

A central 'apt' server sounds like a good idea as to control what updates would be installed and prevent the requirement for them to be root to install them, but I can't find anywhere that mentions it. Does it exist?

Also, does anyone know of a good alternative to OpenLDAP or NIS. From what I gather NIS does not encrypt authentication so would not be ideal for a business environment.

Thanks,

---

### Post by craigp84 on 2007-05-11
Easy questions first:

NIS is used by hundreds of thousands, if not millions of businesses world wide. It's proven and workable. It's not perfect by a long shot, but it is easy to recruit talent capable of supporting it.

I wouldn't recommend NIS for new deployments though.

OpenLDAP is just one specific implementation of LDAP. There are others such as [http://directory.fedoraproject.org/](http://directory.fedoraproject.org/). OpenLDAP has proven to be an excellent LDAP server, you should really think twice before choosing another implementation. It is the software behind the (current) largest LDAP directory ever created in the world (in fact i think it runs the top 4 or 5), and has great speed + stability.

Now for the interesting bit. Apt. You've got a few options here.

**Simplistic:**

Every host goes to the ubuntu repos for it's updates, but does so through a proxy server (sudo apt-get install squid, configure in /etc/squid/squid.conf) which is *only* used for downloading packages, and is configured to cache the (somewhat large - couple of meg sometimes) packages on disk for reasonable periods of time (several days at least).

This is quick and easy to setup - configure the clients by adding:

```
Acquire::http::Proxy "http://your.proxy.server.here:3128";
```

To "/etc/apt/apt.conf".

This route is unlikely to give you much hassle. Coupled with the "unattended-upgrades" package on the clients, you'd be setup before lunch time :-)

Down sides would be the inability to run acceptance tests against the incoming patches. It depends on how big your site is whether this is an issue or not, but you'd cron the updates of critical hosts for out of hours anyway.

**More Interesting:**

[http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)

Hope this helps,

-c

---

### Post by rich.bradshaw on 2007-05-11
I have two computers, so I'm not really doing this on a big scale (!), I just rsync /var/cache/apt/archive on them both, so that they both have the same apt cache, this way, which ever does it first lets the second get it off it, and vice versa.

Is there a better way to do this on the scale I am doing it?

I imagined before symlinking this directory to a main one on a server.

---

### Post by craigp84 on 2007-05-11
Sounds good to me.

---

### Post by SomethingCronic on 2007-05-12
Thanks Craig, that certainly answers my questions. Do you happen to know of any good graphical front-ends to OpenLDAP? 

One other question. The idea of having a central LDAP server is to centrally administer PCs. Is there an equivalent to Group Policy where I can restrict or 'kiosk' PCs so that (for example) menus or programs are restricted?

Thanks

---

### Post by craigp84 on 2007-05-12
> Do you happen to know of any good graphical front-ends to OpenLDAP? 

I'm not 100% sure, although for quick edits i have a copy of LAT (ldap administration tool) installed. I find it's pretty quick for adhoc edits, and also allows me to drag in .ldifs etc. It's fairly basic, but i scratches my itch.

Most of the tools available are a simple "apt-get install" away anyway, so you can afford to install them, play around with, and if they don't suit, then "sudo dpkg --purge <package-name>" will completely remove it from your system again.

> where I can restrict or 'kiosk' PCs 

There is indeed. If you're using Kubuntu, (K?)it's Kalled Kiosk. For normal gnome-ubuntu, it's called sabayon - and they're both just an apt-get away.

---

### Post by SomethingCronic on 2007-05-13
Excellent! Always nice to have a few more toys to play around with :)  Thanks.

---

