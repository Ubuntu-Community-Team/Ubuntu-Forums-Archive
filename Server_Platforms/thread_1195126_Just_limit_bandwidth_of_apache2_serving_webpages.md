---
title: "Just limit bandwidth of apache2 serving webpages"
date: 2009-06-23
forum: Server Platforms
---

### Post by mathgirl on 2009-06-23
:) I have apache2 serving webpages, but my ISP punishes me if download too much too fast :(  I'd like to throttle apache's bandwidth and all the answers I've see in google are huge things like squid-cache.  Is there something simple I could do? :confused:

---

### Post by alastair on 2009-06-23
A google search for "apache throttle" shows one or two pages of interest.

---

### Post by mathgirl on 2011-02-22
I've been looking into this on and off for years and never found anything straightforward that works on my ubuntu server.

Apache modules that either don't compile, don't work once installed on ubuntu, or don't actually throttle bandwidth in an understandable way:
mod_cband
mod_bwshare
mod_bw
mod_throttle

Things that are just overkill:
putting open-wrt on a router and using it to shape traffic
complicated scripts that involve writing 'iptables' over and over

If anybody is a fan of one of those modules and knows how to get it working in Ubuntu, a little hand-holding would be nice... :)

---

### Post by tgalati4 on 2011-02-22
Find a new ISP.

Or get into open-wrt.  It was made just for that purpose, among other things.

---

### Post by mathgirl on 2011-02-23
> Find a new ISP.

Where I live there's only DSL from the phone company and cable internet from the cable company.  For the speed I need, I have no choice but to go with cable which sniffs packets, limits speeds when they can tell a file is large, and, of course, puts heavy restriction on serving files from your home network.  Has 'find a new ISP' ever been real advice for residential users?

> Or get into open-wrt. It was made just for that purpose, among other things.

Flashing the firmware on my router and learning how to use a hardware-specific distro is a lot of effort to go through for something that should be simple.  I don't want sophisticated traffic shaping abilities, I just want to share my files and not get my internet cut off every time some wget robot tries to scrape my site.

Anybody who runs apache on their home computer runs the risk of being hammered by scraping scripts unless they learn how to hack their routers?

---

