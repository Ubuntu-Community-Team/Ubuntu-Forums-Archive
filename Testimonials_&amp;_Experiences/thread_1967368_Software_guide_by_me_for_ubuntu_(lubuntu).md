---
title: "Software guide by me for ubuntu (lubuntu)"
date: 2012-04-28
forum: Testimonials &amp; Experiences
---

### Post by vanquishedangel on 2012-04-28
Hello I am creating this as sort of a one stop shop guide by a moderately experienced user for new people just looking around, I had alot of questions when I started with linux so I decided to make this. Most of the guides and software recommended sucked in my opinion so here is my list.

First off I like Lubuntu because I like fast and many of the softwares in their are good but some are not useful to me. So I install Lubuntu and then get rid of these.

Delete list
1.gnumberic (need full office)
2.abiword (need full office)
3.audatious (mplayer can handle this)
4.gnome-mplayer (need better gui, it is nice but smplayer is better for me)

install list
1.libreoffice (full office suite)
2.varnish (http accelerator)
3.sdparm (for scsi devices)
4.bleachbit (cleaner for debian systems, clean files)
5.playonlinux (a front-end to wine with scripts to install windows software)
6.uget (a downloader program, front-end)
7.aria2 (accelerated downloader program)
8.smplayer (frontend to mplayer that looks nice)
9.gufw (graphical front-end to ubuntu firewall)
10.clamtk (antivirus scanner for linux, native, front-end)
11.catfish (searches for files)
12.clamd (antivirus daemon)
13.gtk orphan (clean out orphaned packages that are installed but can be risky)

then I run in terminal "sudo apt-get build-dep wine varnish playonlinux uget aria2 mplayer bleachbit sdparm libreoffice ufw gufw clamav clamtk smplayer chromium-browser cups catfish evince gpicview guvcview leafpad xpad pidgin xfburn sylpheed transmission clamd deborphan gtkorphan osmo simple-scan

This gives you a more powerful firewall than anything in windows, a good antivirus, a great mediaplayer, accelerated downloader manager (chromium gets interrupts on slow connections) a file searcher, a cleaner as good as ccleaner, and a full office suite.

this may also install Firefox but I don't use that browser anymore. some of these may need configurations to reach their full potential this is just a list for people looking for software to install that just converted from windows or that are new to ubuntu (lubuntu). some disto's may already have similar programs installed but I like light and flexabile ones

I go to school so this set up works well for me.

---

### Post by km3952 on 2012-04-28
I believe the purpose behind Lubuntu is to use the best smaller applications available to do that which most users would want to do. Also, I think they are trying to stay with just GTK based applications.

Good luck with your modifications, & enjoy.

---

### Post by vanquishedangel on 2012-04-28
> **km3952 said:**
> I believe the purpose behind Lubuntu is to use the best smaller applications available to do that which most users would want to do. Also, I think they are trying to stay with just GTK based applications.

Good luck with your modifications, & enjoy.

thank you, everything is from the repo's and most of the applications are the original ones just a few are subtracted and some added for functionality reasons, and the build-dep is to increase their compatibility and functions

---

