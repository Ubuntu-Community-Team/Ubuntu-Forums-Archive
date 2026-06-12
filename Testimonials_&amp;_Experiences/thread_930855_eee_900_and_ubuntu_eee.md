---
title: "eee 900 and ubuntu eee"
date: 2008-09-26
forum: Testimonials &amp; Experiences
---

### Post by michaelkahl on 2008-09-26
Today I got my Asus 900 16gb.  I know this model gets poor reviews and alot of hate, but it was cheap and fits my needs.
I just installed Ubuntu eee and everything seems to work so far.  I'm reading guides and figuring out what tweaks I will do to help extend battery life.  
I'll report back in a couple of days with some feedback on battery life with Ubuntu.

---

### Post by Crafty Kisses on 2008-09-26
I'm glad everything is working thus far.

---

### Post by michaelkahl on 2008-09-26
Thanks!
As for the battery, I started at 3:50 pm from a full charge and at 6:30pm shut it down with 20% left.  I was using it most of the time.  Trying to figure out how to tweak the power.  This resulted in me leaving it in performance mode most of the time. Anything else kicked it down to 112MHz and firefox would crash instantly.  Leaving it at 900 kept everything stable.  Also during this time WiFi was up and I was at 50% brightness.
The wireless works, but the reception seemed better in Xandros.  Xandros also showed me multiple AP's for the same wireless network at school.  I could pick the one with the strongest signal.  Ubuntu doesn't give me that out of the box.  Does anyone know how I can get that?
All-in-all I am happy with Ubuntu eee and the netbook remix.  It's awesome.
I know it's not vanilla ubuntu, but still thought I'd share my experience here for the community.
:guitar:

---

### Post by wolfen69 on 2008-09-26
i've never used netbook remix, but debianeeepc on my 2G surf is awesome. it absolutely flies. i use wifi-radar and it sees all networks in my area.

---

### Post by michaelkahl on 2008-09-26
> **wolfen69 said:**
> i've never used netbook remix, but debianeeepc on my 2G surf is awesome. it absolutely flies. i use wifi-radar and it sees all networks in my area.

I will keep an eye on that but one thing concerns me.
[http://wiki.debian.org/DebianEeePC/Bugs/2.6.26](http://wiki.debian.org/DebianEeePC/Bugs/2.6.26)
Seems that there is an issue with my model and they are potentially harmful.  I know that this SSD is slow, so I take that into consideration while using this machine.  So far there aren't a lot of hang-ups.

---

### Post by wolfen69 on 2008-09-26
that is with the 2.6.26 kernel. i believe i am using 2.6.25

---

### Post by michaelkahl on 2008-09-27
I'll just have to look into it and see how I can get it with the older kernel.

---

### Post by michaelkahl on 2008-09-27
Two days and...
I've learned several things:

1. For MY needs I uninstalled Flash 10 beta, and installed 9.  School needs dictate this.

2.  Be careful with the repo's on Ubuntu Eee.  While it's essentially Ubuntu it is a custom kernel.

3.  Using ext2 file system, disabling log files, setting noatime in fstab, and disabling cache/browser histroy in Firefox improve battery life and reduce SSD read/writes.

4.  Either Adblock or Download Helper addons cause Firefox to crash, not sure which.  Uninstalling both stabilized things out.

5.  Battery life is good, I'm getting 3.5 hours on average after performing the above tweaks.  Prior to that I was getting somewhere just shy of 3 hours.  I know some atom based books get better, but this Eee was much cheaper than some of those and fits my needs.

Hopefully this helps anyone looking to run Ubuntu Eee on any Eee pc.  
Good luck to those who try and thanks to those who are putting a lot of hard work and effort into the project.  It is GREATLY appreciated.

---

### Post by mpc350 on 2009-03-08
Just a quick response / plug for Ubuntu Netbook Remix:  I installed it yesterday on my Eee 900A with Atom processor.  Everything worked flawlessly the first time out of the box.  Battery life is 4~ hours.  I love how the interface is customized for tiny screens and simplicity.  Also to mention, I am using the pre-release Jaunty UNR.  I am happy as a clam with this release.  It really should ship with the Eee instead of Xandros, which I fear will give Linux a bad rep for first time non-Windows users.

---

