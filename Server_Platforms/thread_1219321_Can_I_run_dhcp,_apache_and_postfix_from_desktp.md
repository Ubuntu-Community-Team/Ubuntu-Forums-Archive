---
title: "Can I run dhcp, apache and postfix from desktp?"
date: 2009-07-21
forum: Server Platforms
---

### Post by RayTheRat on 2009-07-21
I've been beating my head on a Ubuntu Server v9.04 install that's supposed to replace my old ClarkConnect (RedHat 7.3 or so) server/gateway/whatever.

I've been able to install things like dhcp-server through apt-get and I can connect to the outside world thru my dsl line (I run this server in my home.)  But I can't get the eth1 or wan0 or whatever the inside network should be called.

I tried following the directions on this page:
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server) but no joy...dhcp isn't working, static ip/gateway/dns server addresses can't get thru the 16-port router, then the Ubuntu server box and out onto the dsl line.  Right now I'm switching cables and addresses so I can connect from at least 1 workstation.

I'm now downloading the 8.04.3 Desktop version (it seems like people are pleased with it) and even if the code isn't optimized for server use, is it still possible to run server apps like Apache, PostFix and Majordomo as background tasks and administer the thing with a gui interface?  The cli interface takes me back to the days when I patched mcp code on mainframes with a 110 baud teletype.  Yeah, I can do it, but it takes forever and there's no visual representation of what's really happening.  I know this is the old "real unix" vs Windoze argument, but I just need something to work so I can do MY work.

If there's a writeup on any of this or if someone who's done this could offer advice, I'd be very grateful.

---

### Post by cariboo on 2009-07-21
What is it exactly that you want your server to do? Supply dhcp for the rest of the computers on the network? Do you already have a router?

To answer your original question, yes

---

### Post by RayTheRat on 2009-07-21
Among other things, I'd like the server (while running a gui front end) to supply dhcp services for the other computers on the network, run Apache webserver, Postfix and Majordomo.  

All the other boxes on the network (save 1) runs Windoze XP.  

Thanks,

---

### Post by HermanAB on 2009-07-22
Linux is Linux is Linux...

Use whatever version your are comfortable with. The so called 'server' versions are marginally optimized for batch processing.  The actual difference in performance is immeasurably small - quite academic really.

---

