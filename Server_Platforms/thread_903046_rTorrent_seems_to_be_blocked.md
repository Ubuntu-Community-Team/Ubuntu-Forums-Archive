---
title: "rTorrent seems to be blocked"
date: 2008-08-27
forum: Server Platforms
---

### Post by xravexheavenx on 2008-08-27
Well, I am running rTorrent on a dedicated box to run as a seedbox and it seems that it is being limited.  I have it running on another seedbox and it running just fine.  Same host and everything.  I con't quite figure out why speed is being limited.  I have worked with the .rtorrent.rc file and everything is fine in there.  I have even removed any kind of blocks due to iptables.  Any ideas?

---

### Post by cariboo on 2008-08-28
Have you tried cloning your config file?

Jim

---

### Post by chila on 2008-08-28
Yeah I seem to be experiencing the same problem. I have ubuntu server (8.04) on one computer and ubuntu desktop (8.04) on another with rtorrent installed on both. Rtorrent seems to work OK (sort of) on the desktop but for some reason I can't get it to work on the server. I have adjusted my iptables on the server but with no success.

One thing that is worth noting is that I am unable to connect to any tracker whatsoever on either system. Rtorrent connects to peers on both systems but will only download/upload when on the desktop but not on the server. I'm at a loss.

cariboo907, how do you clone the config file and what good will that do?

---

### Post by windependence on 2008-08-28
Do you have the same NIC card installed on both boxes?

Please post the contents of your /etc/resolv.conf on both hosts.

-Tim

---

### Post by chila on 2008-08-28
> **windependence said:**
> Do you have the same NIC card installed on both boxes?

Please post the contents of your /etc/resolv.conf on both hosts.

-Tim

Both systems use an integrated NIC, each with a different motherboard.

Also each resolv.conf is identical:

search hsd1.pa.comcast.net.
nameserver 68.87.64.146
nameserver 68.87.75.194
nameserver 68.87.71.226

---

### Post by mellowd on 2008-08-28
Are you using different ports on both? and have both these ports been forwarded?

---

### Post by chila on 2008-08-28
I'm using the same ports on both. I have to ports forwarded on the server only, since I intended to solely use it with rtorrent. The same thing happens regardless of whether the ports are forwarded or not.

It seems that I am able to connect to peers on both systems. I needed to enabled dht in order to connect to peers without a tracker. I am still unable to connect to any tracker though.

---

