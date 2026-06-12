---
title: "Minimal XEN server"
date: 2007-09-13
forum: Server Platforms
---

### Post by Mr Wonka on 2007-09-13
Hi all,

I'm looking at building me a new and more powerful personal server in the near future and figure that now would be a good time to move to virtualisation for learning and experimentation. Here's what I want.

1) An ultra minimal host OS. I'm thinking that it shouldn't come to more then 100MB on disk. It needs to have **evms** so I can manage an attached SCSI array. I'm having real difficulty finding this part and am thinking it may have to be a [Linux from Scratch]("http://www.linuxfromscratch.org/") install.

2) XEN based (I've considered OpenVZ but I can only find installs for Redhat based distros.)

3) Preferably a very active project for security updates etc.

Has anybody come across anything like this? I'm basically after something like VMWare ESX (as closs to the metal as possible)  but built with OSS. I would like to use Ubuntu Server but it's just too fat.

Thanks
Adam

---

### Post by EmmEff on 2007-09-14
Why not just run XenExpress then?  That's essentially what it gives you.

The only potential hangup might be the evms part (this may not be included in the Express version).

---

### Post by Mr Wonka on 2007-09-17
I had a look at that, and much as I admire the work the xen people are doing I can't justify the cripple ware that XenExpress provides, nor afford XenEnterprise.

It doesn't look like I've got the knowledge to build me a custom system as yet. But I'm very surprised that there is not one already available.

---

### Post by ssam on 2007-09-17
a problem with linux from scratch is that it has no package manager to deal with updates. you would be responsible for listening out for security updates to the software you use, applying patches, testing, compiling, installing etc.

i would suggest gentoo, which gives you a similar level of control, but has a good package manager.

---

### Post by EmmEff on 2007-09-17
Gentoo would allow creating a minimal Xen server, but then it's necessary to carry along the baggage of the Portage directory tree and the full development environment to update it.

---

