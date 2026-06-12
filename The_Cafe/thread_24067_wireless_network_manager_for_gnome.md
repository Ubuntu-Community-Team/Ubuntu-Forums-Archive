---
title: "wireless network manager for gnome?"
date: 2005-04-05
forum: The Cafe
---

### Post by im_ka on 2005-04-05
is there something like kwifimanager for gnome?

[http://kwifimanager.sourceforge.net/](http://kwifimanager.sourceforge.net/)

there are a lot of cafes and restaurant in vienna that provide wlan access to guests, so it'd be cool to scan for networks (no, i'm not a wardriver) with ubuntu.

---

### Post by im_ka on 2005-04-05
to answer my question:

wifi radar
[http://gnomefiles.org/app.php?soft_id=332](http://gnomefiles.org/app.php?soft_id=332)

gonna see how it works and maybe create a deb (never done it before)

---

### Post by Dragonfly_X on 2005-04-05
cool signature!

---

### Post by poofyhairguy on 2005-04-05
[QUOTE=im_ka]is there something like kwifimanager for gnome?

[http://kwifimanager.sourceforge.net/](http://kwifimanager.sourceforge.net/)

there are a lot of cafes and restaurant in vienna that provide wlan access to guests, so it'd be cool to scan for networks (no, i'm not a wardriver) with ubuntu.[/QUOTE]

Well. I've been spending a lot of time on this, and so I'll tell you what I know.

Fisrt of all, there are Gtk projects that aim at creating the software you want. The one you found looks good, but there is also:

[http://gkismet.sourceforge.net/](http://gkismet.sourceforge.net/)

and 

[http://www.ubuntuforums.org/showthread.php?t=18466&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=18466&highlight=wireless)

A bigger problem then finding a program is getting your card to use "monitor" mode so you can scan for access points. If you have an Orinoco card, then these sites can help you.

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

[http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html)

If you have a prism card, you must work some holy power and get the hostap drivers to work.

If you used NSIDSWRAPPER to get your card to work, I don't think there is any way to turn on monitor mode (besides buying a new card).

I am personally stuck at the "change the drivers for my wireless cards" part, but there is tons of advice on the forum of how to do it. If I ever figure out an easy way to add monitor mode to my Orinoco card, that I will make a howto in the wiki...

---

### Post by im_ka on 2005-04-05
[QUOTE=poofyhairguy]Well. I've been spending a lot of time on this, and so I'll tell you what I know.

Fisrt of all, there are Gtk projects that aim at creating the software you want. The one you found looks good, but there is also:

[http://gkismet.sourceforge.net/](http://gkismet.sourceforge.net/)

and 

[http://www.ubuntuforums.org/showthread.php?t=18466&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=18466&highlight=wireless)

A bigger problem then finding a program is getting your card to use "monitor" mode so you can scan for access points. If you have an Orinoco card, then these sites can help you.

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

[http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html)

If you have a prism card, you must work some holy power and get the hostap drivers to work.

If you used NSIDSWRAPPER to get your card to work, I don't think there is any way to turn on monitor mode (besides buying a new card).

I am personally stuck at the "change the drivers for my wireless cards" part, but there is tons of advice on the forum of how to do it. If I ever figure out an easy way to add monitor mode to my Orinoco card, that I will make a howto in the wiki...[/QUOTE]

well, i use ndiswrapper for my rt2500 based cheapo conceptronic card. i know there is a linux driver available, but it's still fresh and not in hoary... so i was too lazy to compile it myself. maybe i should use the native driver then.

---

### Post by homerhomer on 2005-05-03
Here's a deb that I rpm/deb hacked to work with hoary
[http://kazakshan.homeip.net/ubuntu/wifi-radar_1.9.3-2_i386.deb](http://kazakshan.homeip.net/ubuntu/wifi-radar_1.9.3-2_i386.deb)

---

### Post by poofyhairguy on 2005-05-03
[QUOTE=homerhomer]Here's a deb that I rpm/deb hacked to work with hoary
[http://kazakshan.homeip.net/ubuntu/wifi-radar_1.9.3-2_i386.deb](http://kazakshan.homeip.net/ubuntu/wifi-radar_1.9.3-2_i386.deb)[/QUOTE]

Thanks. I was working on that, but the going was pretty ruff. I'll test your deb tomorrow.

---

### Post by jonny on 2005-05-03
I use ndiswrapper with a Dell Truemobile card (Broadcom chipset).  Scanning works fine on that - sudo iwlist scan shows me all the nearby access points - so ndiswrapper isn't the problem.

I've tried various gui tools, but they all lack two important bits of funtionality:

1. I rarely want to just switch to a new wireless access point.  I also want to change my domain name, swap between dynamic and static ip addressing, mount some network drives, change my default printer and amend my firewall settings.

2. As a security measure, one of the networks that I commonly use doesn't broadcast its ESSID.  I need to be able to select this network, even though it doesn't appear in  any scanning list.

If it's any comfort, Windows is much worse at meeting these requirements (it offer automatic drive mapping, but you need to reboot after changing your network settings), and my colleague's Apple notebook is no better, than Linux, either.

There must be millions of people around the globe who, like me, regularly switch between networks for file and print sharing, and not just internet access.  I find it hard to believe that no major OS offers it as an out-of-the-box standard.  I'm tempted to dust down my programming skills - scarcely used since the 1980s, I'm afraid - just to tackle this problem.  Linux has the the raw functional components, they're just not joined up.

---

