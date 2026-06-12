---
title: "linux and webhosting"
date: 2010-02-10
forum: Server Platforms
---

### Post by userkiller on 2010-02-10
Hi guys am looking forward on building my own web hosting business. i really would love you guys to tell me what i really need to learn in order maintain,set up and administrated servers.

And sorry for my nubish english.

---

### Post by tlsarles on 2010-02-10
that's kind of a tall order.
To start, the LAMP stack.
DNS
Backups / Disaster Recovery

Security should not be taken lightly when dealing with other people's data. Some sort of a Cisco firewall / IDS/IPS would also be good.

SSL

.... probably some other stuff....

---

### Post by userkiller on 2010-02-10
Okay thanks you, i mean i can already set up a local web site, by looking at howtoforge, i also know like around 50 commands, learning more as we speak.:D

---

### Post by dragos2 on 2010-02-10
By having a good internet connection ;)

Then you can think to provide some high uptime, like at least 99%(1 maximum
hour of monthly downtime) which involves quite some knoledge and maybe
equipment.

Try more specific questions, many people from here worked hard for their knoledge
so asking a smart question will most likely trigger smart answers.

Good luck.

Dragos

---

### Post by userkiller on 2010-02-10
> **dragos2 said:**
> By having a good internet connection ;)

Then you can think to provide some high uptime, like at least 99%(1 maximum
hour of monthly downtime) which involves quite some knoledge and maybe
equipment.

Try more specific questions, many people from here worked hard for their knoledge
so asking a smart question will most likely trigger smart answers.

Good luck.

Dragos

Like for the web hosting business every company just seen to use centos why is this?

---

### Post by noway2 on 2010-02-10
If I recall correctly, centos is basically an older, stable version of red hat.  It is widely used because it is stable and known to work well and be compatible.  On the downside, it lacks some of the cutting edge features.  On the upside, being a Red Hat product, it is easy to get and justify commercial (paid) support.

---

### Post by userkiller on 2010-02-11
> **noway2 said:**
> If I recall correctly, centos is basically an older, stable version of red hat.  It is widely used because it is stable and known to work well and be compatible.  On the downside, it lacks some of the cutting edge features.  On the upside, being a Red Hat product, it is easy to get and justify commercial (paid) support.

I also found out that people use cent os because it compatible with cpanel.

---

### Post by jrssystemsnet on 2010-03-18
> **noway2 said:**
> If I recall correctly, centos is basically an older, stable version of red hat.Uh, not exactly.

CentOS is a free clone of Red Hat Enterprise Linux, which is a for-pay distribution.  (As opposed to Fedora, which is basically the bleeding-edge beta version of RHEL, but is free-as-in-beer.)

What the CentOS guys do is download the source for the entire RHEL distro, then compile it and redistribute the binaries themselves.  So it's the same codebase as RHEL, but without the support from Red Hat the company (and without paying $$$ to Red Hat the company).

RHEL is basically the Microsoft of the Linux world (as in, "nobody ever got fired for using Microsoft"), so you see a lot of knee-jerk RHEL usage, and a lot of knee-jerk CentOS usage amongst the folks that have the same tendency to want "the business linux" but don't want to pay for it.

Frankly, I prefer Debian or Ubuntu to any other distros of Linux, money aside.  But you have to make your own choices based on your own needs, one size does not necessarily fit all.

---

