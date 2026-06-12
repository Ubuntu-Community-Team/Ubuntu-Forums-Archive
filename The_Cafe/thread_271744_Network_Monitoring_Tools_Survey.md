---
title: "Network Monitoring Tools Survey"
date: 2006-10-05
forum: The Cafe
---

### Post by braddock on 2006-10-05
I spent some time trying out various tools from the repositories for monitoring network traffic.  I was just looking for something simple, preferably console based, that would show instantaneous bandwidth usage overall and/or by connection.

I thought I would post my results here for general consumption.  Some of these tools I hadn't heard of, and are really nice finds.

iptraf
I love iptraf, but it doesn't give a good instantaneous
picture, and is a bit more than I need for some things.

nload
This console app gives a VERY nice graph of overall instantaneous
traffic usage.  Another keeper.  However, it does not provide
connection-based breakdowns like iftop (I think it just uses kernel stats).

iftop
Much like jnettop, BUT it provides a graphical ASCII bar for each
connection showing normalized net usage.  This makes it FAR clearer!
Very nice tool...this is a keeper

jnettop
Very straightforward - gives an immediate and fairly instantaneous
view of top bandwidth bandits.  But iftop is better unless I am missing something.

netspeed
This is a Gnome Panel Applet, but it is quite nice.  It will show you
up/down speeds in the panel, and has a Device Details menu option
which will display a very nice and detailed real-time usage graph.

netdiag
This is a set of tools intended for network diagnosis and throughput
testing.  They seem simple yet hard to use, and undocumented.  Some seemed broken?
(Ubuntu 6.06LTS).

Anyone have other suggestions or comments?

---

### Post by hellmet on 2006-10-06
first of, thanks for throwing lite on various traffic tools dude..

---

### Post by henriquemaia on 2006-10-06
Some of the tools you posted are really useful. Thanks.

---

### Post by DAB4970 on 2012-05-20
Hey guys.  I installed NETSPEED package on my new 12.04 installation.  I'd like to actually see it in the sys tray on the panel.  Can someone suggest things to look for, additional packages to install?

---

### Post by alphacrucis2 on 2012-05-20
> **braddock said:**
> 

Anyone have other suggestions or comments?


nprobe

---

### Post by cariboo on 2012-05-20
This is a ***6*** year old thread, please start a new thread with more relevant applets, as some won't work with the current version of Ubuntu, especially panel applets. Thread Closed.

---

