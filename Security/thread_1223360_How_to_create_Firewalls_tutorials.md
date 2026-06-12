---
title: "How to create Firewalls tutorials"
date: 2009-07-26
forum: Security
---

### Post by upapilot on 2009-07-26
Hi guys,
I am looking forward towards creating a firewall for my Ubuntu and was looking for some good tutorials......could you please link some of them here? or perhaps write an entire tutorial right here? 
Any help will be appreciated ;)

---

### Post by sasho_zl on 2009-07-26
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Also at [www.shorewall.net]("http://ubuntuforums.org/www.shorewall.net") there is a good quick start guide for the configuration of the firewall.

---

### Post by bodhi.zazen on 2009-07-26
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

See the references as well ^^

The problem is that , IMO, at the end of the day, firewalls themselves are not very complicated. You do, however, need to know at least the basics of netwrok protocols and servers.

---

### Post by Cotopaxi on 2009-07-26
One thought:

There are two firewall graphic front-ends available:

Guarddog and

Firestarter.

I ran into violent problems with Firestarter, because it just blocked any internet connection attempt!

Following the recommendation from one member of this forum, I deinstalled Firestarter and configured my firewall with Guarddog.

As a network manager I am using &#8220;wicd&#8221;. This wicd actually deinstalls network-manager, but that's fine with me.

All the software is available via the repositories.

I hope this helps.

---

### Post by bodhi.zazen on 2009-07-26
> **Cotopaxi said:**
> One thought:

There are two firewall graphic front-ends available:

Guarddog and

Firestarter.

I ran into violent problems with Firestarter, because it just blocked any internet connection attempt!

Following the recommendation from one member of this forum, I deinstalled Firestarter and configured my firewall with Guarddog.

As a network manager I am using “wicd”. This wicd actually deinstalls network-manager, but that's fine with me.

All the software is available via the repositories.

I hope this helps.

ufw is installed by default, gufw is in the repositories, and +1 to guard dog, nice built in help.

---

