---
title: "Ubuntu 7.10 Server"
date: 2008-03-13
forum: Server Platforms
---

### Post by keenboy on 2008-03-13
I need to build a server for somebody to run samba for win2k clients, cups and exim.

Normally we use debian stable. I was just wondering whether Ubuntu server 7.10 would be a worthy contender as a new replacement for debian?

Obviously ubuntu is built on a debian framework and poses most of the benefits of debian.

I would just like some reassurance of stability, security and reliability of 7.10 server running the above packages.

Any feedback from people who have achieved this or problems encountered would be good.

I suppose the question really is:

Ubuntu 7.10 Vs Debian Etch - which is best?

---

### Post by Harlequin on 2008-03-13
Not having used Debian Etch I can only comment on 7.10 - Its running 2 servers for me at the moment all fine.

I see no reason not to recommend it.

---

### Post by faulkes on 2008-03-13
There is no "best" perse.  I can't comment on exim, however it runs samba and cups 
just fine.  WIll you also be requiring LDAP in order to create a PDC?

It offers all of the items you're asking about, stability, reliability, security on par with
debian does.

I have 7.10 running on dell blades doing a variety of tasks, works wonderfully.

Faulkes

---

### Post by jonabyte on 2008-03-13
I have been enjoying using Ubuntu, since i added a couple over the past few months.
I would recommend using it.

---

### Post by Paul Weaver on 2008-03-13
I've got about 20 servers at work running a variety of 6.06, 7.04 and 7.10, from 7.5T file servers to simple web frontends, 32bit and 64 bit. Currently fighting the corporate juggernaut, who want us to "standardise" on Redhat. 

The only problem I've had with stability is a cheap logitech webcam, which works swimmingly on my (7.10 32bit) laptop, but kernel panics on a 32bit DL360. My gut tells me it's an issue with either USB1 on the server, or a conflict with the USB KVM dongle. It's on the list of things to do.

Next month the next version of Ubuntu will be released, and will have 5 years of support (security updates) for the server build.

I run Debian etch at home as my mythtv box, having used Debian since potato. Had a few problems with my Wintv PVR-250 which may be heat related, or disk related, but then my version of etch is very old (last updated while it was still in testing) and I'm looking at cleaning the whole thing out, getting a new disk, and installing ubuntu with Myth 0.21 on it in the next month or so.

---

### Post by netlogic on 2008-03-13
Not everyone needs are the same. This has been asked so many times in many years. It all depends on the hardware, apps, and preferences of package management. If you are planning to avoid the compiler, you want the very fast release cycle distros that have the wide hardware support. At the current time, Ubuntu offers it. They might not in the future. We don't know. Debian used to be bleed edge with hardware drivers. If you are managing many standard x86 servers, Ubuntu might be better, because more likely you are going to compile less apps by yourself. Ubuntu has a bigger community and release cycles are faster. If you are planning to have a dedicated functional server, why do you have the urge to constantly upgrade? The famous old school sysadmin term, "don't fix if it isn't broken."  Don't drive your friend's BMW if you are likely to crash it. If you work with copy/paste developers who copy paste others latest codes, you need very fast release cycle distros to have the latest and greatest. When choosing a distro, you can't go by and say, what is the best? You have to try different distro yourself and know the differences. Sometimes, distro philosophies change as project managers and leader of the projects change too. Fedora has become less bleeding age in the past few releases and focused on the stability. The best thing to do is use whatever you know inside and out if it is going to be a production server.

---

