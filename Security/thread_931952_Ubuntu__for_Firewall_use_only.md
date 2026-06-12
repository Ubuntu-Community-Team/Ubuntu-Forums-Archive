---
title: "Ubuntu  for Firewall use only"
date: 2008-09-27
forum: Security
---

### Post by racsw on 2008-09-27
Hello,
For our new office, I would like to buy a new computer with nothing more than two ethernet cards to be used only as a firewall between the Modem and Router and a Linux OS.
I don't have an IP guy, but have Linux experience, but I do not want to waste my time with complicated setups or configurations.
I need a Firewall system that's designed to do exactly that, and can be maintained with a minimum of effort or time, but will be a very effective deterrent and efficient firewall.
I've looked at IPCOP, b ut I used to use Ubuntu, so I wanted to ask if this was a feature that could be implemented with the current version.
If anyone has any constructive, helpful suggestions, I would truly appreciate it.

Regards,
Robert

---

### Post by koenn on 2008-09-28
buy a firewall. Seriously.

I find it perfectly reasonable to use a pc as a firewall, but if you're buying a new PC just for that purpose, just buy a firewall. Will probably cost less, and will consume less power, will produce less heat and noise, ... Also, your "I don't want to waste time on configuration" and "I'd like this built in in the next release of Ubuntu" suggests you're actually considering using a full blown desktop system as a firewall. You don't want all that on a firewall, as any exploitable bug in any of the software is a potantial hole in your security. Bad idea.

get a fiewall with a user friendly web interface. you'll be better of.

---

### Post by racsw on 2008-09-28
I've decided to get a Dell Optiplex off of Craigs List for small amount, and install SmoothWall Express on it, which is a full hardened Linux firewall system.  I already own the Yoggie PICO SOHO Pro firewall linux device, but it has a problem with IMAP mail systems, so that eliminates that.

Thanks for your help.
Robert

---

### Post by warchief_ryan on 2008-09-28
If I was going to do this or if you had an IT guy that could, I dont see a problem with using Linux. The prices from what ive seen would be competitive with firewalls you can buy, and other aspects like power consumption or noise will depend on the parts you get.

The configuration will be the most important part both of the firewall and to harden the system, the time it takes the configuration depends on you. And I wouldn't suggest just using UFW, id be iptables directly. Unless you use a distro dedicated for the task.

---

### Post by DemonBob on 2008-09-28
Just to throw my favorite firewall distro out thier. I've tried Smoothwall, but find pfsense, based off of FreeBSD to be more to my liking, i'd give both a try and see which suites your needs better.

---

### Post by kevdog on 2008-09-28
Seriously if you buy a linksys router and flash it with ddwrt, you could write your own iptables rules directly -- a lot less power consumption, probably just as cheap as a computer, and serves the same purpose.  Im not saying what you want to do is invalid, however it just seems like overkill.

---

