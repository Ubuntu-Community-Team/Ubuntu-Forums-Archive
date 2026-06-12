---
title: "installation of sguil"
date: 2011-08-18
forum: Security
---

### Post by lolek198787 on 2011-08-18
Hi,

Does anyone could writte for noob step by step how to install sguil and use it?

---

### Post by bodhi.zazen on 2011-08-18
This is not a package in the Ubuntu repos and so I suggest you use the sguil mailing list or RHEL/ Centos/Scientific as advised on their site.

[http://nsmwiki.org/Sguil_on_RedHat_HOWTO](http://nsmwiki.org/Sguil_on_RedHat_HOWTO)

Personally I do not install software on my system that lacks the proper documentation and this project seems to have little or no interest in documentation.

They claim "The most current install documentation can always be found under the docs directory of the included source." so I guess you should start by reading that.

---

### Post by Enigmapond on 2011-08-18
Right...I just downloaded and the docs are located in the doc file...and good luck with them. I would be wary of this but good luck...

---

### Post by Kinstonian on 2011-08-18
I installed it a long time ago when it was an absolute nightmare.  One of the most complicated installs I've ever heard of.  Fortunately it's a lot easier to get all the software working together with [InstantNSM](http://nsmwiki.org/InstantNSM), although I haven't used that in a while either.  For any questions check out the Sguil IRC channel on freenode, or try their mailing list.

---

### Post by lolek198787 on 2011-08-18
I shearch GUI Snort and i choose sguil. Maybe ther is better tool than that(easlier to install).

---

### Post by Kinstonian on 2011-08-18
> **lolek198787 said:**
> I shearch GUI Snort and i choose sguil. Maybe ther is better tool than that(easlier to install).

Sguil ties a bunch of open source software together to let you use different types of network based evidence to easily investigate alerts.  If you want to pretty much just see alerts in a GUI, check out BASE.

---

### Post by lolek198787 on 2011-08-20
ok, i installed snort, mysql and acidbase, but when I try to writte in mozilla url: localhost/acidbase I've got error 403: Forbidden

---

### Post by bodhi.zazen on 2011-08-20
> **lolek198787 said:**
> ok, i installed snort, mysql and acidbase, but when I try to writte in mozilla url: localhost/acidbase I've got error 403: Forbidden

sounds like a permissions problem. The files need to be accessible by the user www-data

---

