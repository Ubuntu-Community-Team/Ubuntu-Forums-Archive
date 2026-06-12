---
title: "Locking down an office network with a gateway server"
date: 2010-08-04
forum: Server Platforms
---

### Post by jgz84 on 2010-08-04
I am looking for some advice on how best to lock down our office network to keep our employee's from wasting time on sites like facebook and youtube.  This will be my first time setting up a server as a gateway in a production environment so I thought I should get some suggestions on what the best packages would be to do this.  

I essentially need to lock down our network so that i can monitor what everyone is doing on the Internet and block it if needed. it doesn't have to be web based or have a bunch of gui's, im fine with command line, configs and log files,  but it would be nice.

I'm interested in commercial products as well as long as they are linux based.

Any suggestions would be great.

Thanks,

---

### Post by Iowan on 2010-08-04
The first thing that comes to mind (and I have no experience with it) is the Squid Proxy server. Some info is available in the [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/squid.html").

---

### Post by dmizer on 2010-08-04
> **jgz84 said:**
> I am looking for some advice on how best to lock down our office network to keep our employee's from wasting time on sites like facebook and youtube.  This will be my first time setting up a server as a gateway in a production environment so I thought I should get some suggestions on what the best packages would be to do this.  

I essentially need to lock down our network so that i can monitor what everyone is doing on the Internet and block it if needed. it doesn't have to be web based or have a bunch of gui's, im fine with command line, configs and log files,  but it would be nice.

I'm interested in commercial products as well as long as they are linux based.

Any suggestions would be great.

Thanks,

I've been using clearos which is a dedicated firewall distribution. You can find more information here -> [http://www.clearfoundation.com](http://www.clearfoundation.com)
It's super easy to block and monitor WAN and LAN access via the Web based interface.

I've also used Untangle before -> [http://www.untangle.com/](http://www.untangle.com/)
It's quite nice, but I prefer ClearOS.

There are a whole bunch of these. Here's a list in wikipedia -> [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

---

