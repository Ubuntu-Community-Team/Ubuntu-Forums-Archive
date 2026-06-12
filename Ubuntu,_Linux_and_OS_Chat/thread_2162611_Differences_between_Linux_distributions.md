---
title: "Differences between Linux distributions"
date: 2013-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by henrybear327 on 2013-07-15
Hello:
*  When* I searched on the web, the results suggested that the biggest difference between different distributions is the desktop environment. But does this mean that the only difference between, for example, Ubuntu and Linux Mint is the desktop environment? Are there any minor system differences besides this?
* * Also, if I install different desktop environments, like installing Mate on Ubuntu. Does this provide the full feature from the Mate interface to Ubuntu? (I mean will there be any function missing if I install Mate on Ubuntu?)

---

### Post by snowpine on 2013-07-15
Welcome!

Here is a nice comparison of the differences between the top distros: [http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major)

To answer your specific questions, there are many minor differences between Mint and Ubuntu, but they are both based on the same "parent" distribution (Debian).

---

### Post by dannyboy79 on 2013-07-15
there are many differences between distributions. to name a few
+kernel
+desktop environment
+package management system
+installed firewall
+root privilages (sudo or not)
+installed software
+open source vs proprietary drivers
+proprietary codecs

Mate is a fork of Gnome 2. You can install any desktop-manager within your Ubuntu installation and at your login manager, you can choose the environment you want to boot into. I am not sure what Mate all installs on top of Ubuntu besides a bunch of media codecs for full multimedia support.

---

### Post by JKyleOKC on 2013-07-15
> **henrybear327 said:**
> *  When* I searched on the web, the results suggested that the biggest difference between different distributions is the desktop environment. But does this mean that the only difference between, for example, Ubuntu and Linux Mint is the desktop environment? Are there any minor system differences besides this?While the DEs are the most visible differences, there can be many other differences also -- and some of them, while not immediately obvious, are quite significant. For example, Debian and Red Hat are so different in the way they structure the system directory tree that "how-tos" written for one won't work on the other. And these differences are inherited by their descendants, so that setup instructions for a Mint package won't be correct if you are running a Mandriva system. This can be extremely frustrating at times, such as when someone tells you to change the runlevel settings -- which are meaningful only in Red Hat and its descendants, and have almost no effect in Debian and its offspring except for a few milliseconds during startup and shutdown -- to change from GUI to CLI operation.

> **henrybear327 said:**
> * * Also, if I install different desktop environments, like installing Mate on Ubuntu. Does this provide the full feature from the Mate interface to Ubuntu? (I mean will there be any function missing if I install Mate on Ubuntu?)This will depend on the specific package and distribution. Some functions' dependencies are hidden quite deeply (by accident, not by design) and get discovered only when things fail to work!

---

### Post by buzzingrobot on 2013-07-15
The biggest obvious difference probably is the desktop.  Other differences do exist.  Software versions vary.  Software installed by default varies. Some distributions make few, if any, changes to the software they provide, others do make changes.  Some distributions target the desktop, others are intended for server use, and others target other uses.  Distribution installation routines do differ, with some targeting new users and others assuming some level of experience. 

For common daily use, and certainly for a new user, these differences can usually be ignored. Any one one of the major desktop distributions is a good place to jump in.  as long as you stay with the software repositories provided for that distribution and to guidance and how-tos written for that distribution. Mixing and matching often ends badly.

MATE installed from the offical repositories at mate-desktop.org gives you MATE's features.  Sometimes, developers and packagers will remove or replace software in a desktop because they think it is faulty, or they don't won't to support it, or they just don't like it. E.g., Gnome-Shell in Ubuntu Gnome is a bit different that Gnome Shell in Fedora.

Linux Mint is based on Ubuntu but, over time, it has made some internal changes to support its Cinnamon desktop and for other reasons.  From a user point of view, the important thing is that tthe software in Ubuntu's repositories can be installed and used.

---

### Post by dannyboy79 on 2013-07-15
something to keep in mind also is support. ubuntuforums.org has a very active and mostly very helpful community and most people here won't help if you're running linux mint. i ran into an issue with Ubuntu Software Center when I was running Linux Mint, i posted my question over on their forums and got no hits after days, so Posted my question here and was told that these forums doesn't support Mint. I had the same reaction when I tried the official ubuntu IRC channel.

---

### Post by HermanAB on 2013-07-15
Linux is Linux is Linux...

The better you know Linux, the less the little differences will matter to you.  The important thing is to find a support forum that you feel comfortable in and then use that distribution.

This machine of mine is a Mac, but I always have at least two virtual machines running as well with Fedora, Ubuntu, Windows(!) and others.

---

### Post by BBQdave on 2013-07-15
Release cycles might be of interest to you :)

Of the two most popular releases Ubuntu based on Debian Linux and Fedora based on Redhat Linux:

Ubuntu releases **L**ong **T**erm **S**upport - **LTS**, every two years. These releases are supported for 5 years. Ubuntu does release every 6 months - more or less the progress of the next LTS.

Fedora is the test-bed for Red Hat Enterprise Linux - RHEL, and is released every 6 months with support for 13 months. Fedora regularly receives test updates, which involve your time to fix or track a fix. Fedora is the most recently released software in the Linux world - *bleeding edge*. If you are looking for long term support, you can purchase a subscription of RHEL or load for free, CentOS or Scientific Linux - both based on RHEL. As an example, the most recently released Fedora 19 will become soon to be released RHEL 7, CentOS 7 and Scientific Linux 7.

Personally, I think Ubuntu Unity is a well done user friendly system. I am enjoying the function and stability of Ubuntu Unity 12.04LTS - which will receive support thru 2017 :)

---

### Post by Cheesemill on 2013-07-15
Not a support request.

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by henrybear327 on 2013-07-15
Thanks for helping me out!!!!!!

---

### Post by ajgreeny on 2013-07-15
> **dannyboy79 said:**
> something to keep in mind also is support. ubuntuforums.org has a very active and mostly very helpful community [COLOR=#ff0000]and most people here won't help if you're running linux mint.[/COLOR] i ran into an issue with Ubuntu Software Center when I was running Linux Mint, i posted my question over on their forums and got no hits after days, so Posted my question here and was told that these forums doesn't support Mint. I had the same reaction when I tried the official ubuntu IRC channel.

Your comments surprise me a bit.

Whilst I accept that there are considerable differences between the two distros (Ubuntu & Mint) I often see answers to mint questions here, though sometimes with a warning that there could be problems resulting from the distro differences.  Don't forget also that the numbering system of ubuntu and Mint can be a bit confusing, ie Mint 13 is not the same base as Ubuntu 13.04, but is derived from Ubuntu 12.04.

In the past I used Mint for a while, but still mainly visited these forums, as the mint forum it was very much slower to get any response.  Provided you are not asking about a specifically Mint application, that is therefore not available directly from the ubuntu repos, I would be surprised if you got a refusal to assist with a query.

---

### Post by buzzingrobot on 2013-07-15
Lots of answers to Mint questions around here.  There is an entire section devoted to other distributions and OS's.

---

### Post by stalkingwolf on 2013-07-15
Main differences between distros ive seen are the desktop, i always install mate because i like it and it has the panel applets i want.The Office suite that is default. The default browser.and lately different default movie players and sound control applications.  Some of these differences are very minimal and ultimately come down to what makes linux great.  Choice.

---

### Post by monkeybrain2012 on 2013-07-15
> **ajgreeny said:**
> Your comments surprise me a bit.

Whilst I accept that there are considerable differences between the two distros (Ubuntu & Mint) I often see answers to mint questions here, though sometimes with a warning that there could be problems resulting from the distro differences.  Don't forget also that the numbering system of ubuntu and Mint can be a bit confusing, ie Mint 13 is not the same base as Ubuntu 13.04, but is derived from Ubuntu 12.04.

In the past I used Mint for a while, but still mainly visited these forums, as the mint forum it was very much slower to get any response.  Provided you are not asking about a specifically Mint application, that is therefore not available directly from the ubuntu repos, I would be surprised if you got a refusal to assist with a query.

Actually there is almost no difference between Ubuntu and Mint other than appearance. Kind of a bad example. :) 

There are some big differences between Ubuntu and Fedora, or archLinux, or even Debian (a lot more messy to setup IMO unless you stick with stable,--with ancient software) but no, not between Ubuntu and Mint. I tried Mint at one point in a different partition, then I erased it after a few weeks, wondering what was the point of having two almost identical distros on two partitions,--almost identical, except Mint has an uglier DE.

---

### Post by ibjsb4 on 2013-07-15
If your looking for a desktop that looks like mint, you can install the classic desktop to ubuntu 12o4 and get support here :)

[https://www.google.com/search?q=ubuntu+classic+desktop+12.04+pictures&client=ubuntu&hs=LNo&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=3zXkUbvENqy7jALX14GQDg&ved=0CCwQsAQ&biw=1280&bih=662](https://www.google.com/search?q=ubuntu+classic+desktop+12.04+pictures&client=ubuntu&hs=LNo&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=3zXkUbvENqy7jALX14GQDg&ved=0CCwQsAQ&biw=1280&bih=662)

---

### Post by Peripheral Visionary on 2013-07-15
Many Linux distros are built for **"niche" markets**.  They may not use the same kernel or include the same drivers.  Some distros are a good fit for older, modest hardware (Lubuntu, Xubuntu, Crunchbang, AntiX, etc) and some at new, high-end machines.  Some distros are aimed at little kids, some at high school kids and college kids, some for "casual users," some for geeks and some for technophobes.  Some for gamers, some for musicians, etc.  Some for business and some for home computers and laptops or netbooks.  Different distros fit different users.  Choose a distro according to your particular needs.

There are differences in **package management**, even among the popular "one size fits all" distros like Ubuntu, Mint, PCLinuxOS, OpenSUSE, Fedora, etc).  These differences matter because they try to resolve software dependencies with varying degrees of success and completeness.  Choose a distro and you're also choosing it's package management.

There are differences in **software repositories** from one distro to another, depending on their "niche" and/or a parent distro.  For home desktop users this is a really big deal.  Choose a distro and you're also choosing its repositories.  

There are differences in **support options**, like paid support services for server and desktop (Canonical, Red Hat, and SUSE offer these) and free community support for users (a distro's Wiki, forums, community).  Choose a distro and you're also choosing one of these options, and some are just better than others.

There are different **software tools** that developers choose for their distro, from it's boot manager (Lilo, Grub legacy, Grub 2) to it's desktop.  Many are unique to a single distro, like Ubuntu's Software Center and Linux Mint's Mint Updater.  Choose a distro and you're also choosing it's tool set.

---

### Post by mJayk on 2013-07-15
One this as I think someone mentioned before is the support community, and good documentation does not make up for a bad community. I feel really spoilt in the ubuntu support community.

---

