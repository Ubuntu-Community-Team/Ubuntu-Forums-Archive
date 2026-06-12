---
title: "Limiting bandwidth/Installing mod_bandwidth"
date: 2006-06-25
forum: Server Platforms
---

### Post by linuxpenguin on 2006-06-25
I said before I was setting up an Apache server.  Now it's all up and running (check it out @ [http://www.linuxpenguin.net]("http://www.linuxpenguin.net") if you'd like).

Anyways, I need to limit the bandwidth on my server - I found out it sometimes messes with the voice quality on my Vonage phone.

I found out about the mod_bandwidth module which should do this, but the site's creators don't exactly have the best English it seems, and the documentation is for older versions of Apache (your "Install LAMP Server" option set me up with Apache 2.x, and the instructions are for 1.3x).  Also it looks like there's some variation with the different folder/file locations.

The documentation can be found here: [http://www.cohprog.com/v3/bandwidth/doc-en.html#](http://www.cohprog.com/v3/bandwidth/doc-en.html#)

Could someone tell me how to install mod_bandwidth on Ubuntu 6.06 with Apache 2.x, or maybe even just point me to a more recent/better written document on how to install it?

---

### Post by linuxpenguin on 2006-06-26
Anyone?

---

### Post by linuxpenguin on 2006-08-30
Please?

---

### Post by SSTwinrova on 2006-08-30
It's possible that it's not compatible with 2.x, and that's why the official documentation hasn't been updated. Wouldn't you just be able to run another program that will throttle bandwidth on specific ports??

---

### Post by linuxpenguin on 2006-08-31
> **SSTwinrova said:**
> Wouldn't you just be able to run another program that will throttle bandwidth on specific ports??

Maybe. . . what programs are there to do this?

---

### Post by linuxpenguin on 2006-11-27
Hello?

---

### Post by dbott67 on 2006-11-27
Haven't used either, but I'd be interested in what you find out about it:
```
sudo apt-get install shapecfg
```
or try CBQ:
```
sudo apt-get install shaper
```

> NAME
       shapecfg - Traffic Shaper for Linux

SYNOPSIS
       shapecfg attach shaper-device other-device
       shapecfg speed device speed

DESCRIPTION
       shapecfg is a program to limit bandwidth on a virtual network interface.

SETUP
       A shaper device is configured using the shapecfg program.  Typically you will do something like this:

       shapecfg attach shaper0 eth1

       shapecfg speed shaper0 64000

       ifconfig shaper0 myhost netmask 255.255.255.240 broadcast 1.2.3.255 up

       route add -net some.network netmask a.b.c.d dev shaper0

       The shaper should have the same IP address as the device it is attached to for normal use.

GOTCHAS
       The shaper shapes transmitted traffic. It&#8217;s rather impossible to shape received traffic except at the end (or a router) transmitting it.

       Gated/routed/rwhod/mrouted all see the shaper as an additional device and will treat it as such unless patched. Note that for mrouted you can run mrouted tunnels via a traffic shaper to
       control bandwidth usage.

       The shaper is device/route based. This makes it very easy to use with any setup BUT less flexible. You may well want to combine this patch with Mike McLagan <mmclagan@linux.org>&#8217;s patch
       to allow routes to be specified by source/destination pairs.

       There  is  no  "borrowing"  or "sharing" scheme. This is a simple traffic limiter. I&#8217;d like to implement Van Jacobson and Sally Floyd&#8217;s CBQ architecture into Linux one day (maybe in 2.1
       sometime) and do this with style.

       (CBQ was added to Linux in the 2.1 series. On Debian systems, see the iproute package for the necessary userspace tools. Support for the simple traffic shaper is  still  present  as  of
       2.4, and, while it is less flexible, most people will probably find it easier to set up.)

SEE ALSO
       More documentation can be found in /usr/share/doc/shapecfg/.

AUTHOR
       This manual page was stitched together from the original author&#8217;s documentation by Christoph Lameter <christoph@lameter.com>, and added to by Colin Watson <cjwatson@debian.org>, for the
       Debian GNU/Linux system (but may be used by others).


-Dave

---

### Post by linuxpenguin on 2006-11-27
Interesting, I'll have to check that out!

Thanks!

Although, interestingly enough, so far even with a decent amount of visits every day (this month's average so far is about 90 pages a day, not bad for a little-known site that was down for a couple weeks and was just brought back online the end of last month) I've noticed nothing as far as Internet slowdowns or problems with the VoIP line.  I think this is due to the server's compression programs - it compresses the page with gzip before it sends it out.

I'll still check it out though - I wanted to use SSH for BitTorrent while I'm away at school (the college I'm at blocks BT downloads to preserve upload bandwidth) so this can help me prevent the server from cutting into my upload bandwidth too deep when I'm running BitTorrent and keep it from making the VoIP line all static-y.

---

