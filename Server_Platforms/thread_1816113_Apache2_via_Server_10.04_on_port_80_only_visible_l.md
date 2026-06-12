---
title: "Apache2 via Server 10.04 on port 80 only visible locally"
date: 2011-08-01
forum: Server Platforms
---

### Post by tycatte on 2011-08-01
A little background first.

I recently put together a server at home from spare parts. I'm running 10.04 and the latest version of apache. Also I have SQL and samba. 

For the most part this is built to be a learning experience. The samba file server is the primary idea, but since it's here I want to build and play around with a web site. 

However, while i can access it locally from any computer on the network (both with my dyndns addy, and with the ip address) I am unable to see the default apache (It Works!) page from outside. I have opened port 80 on my router (N300 wnr2000v3) but no dice. canyouseeme.org times out, however I can ssh into the machine remotely and VNC through that.(didn't use port 22 but one over 1500 if that matters)(I can also ssh in using the dyndns address, so i know it works.) I opened that port the same way, and it worked. 

UFW is turned off, netstat says that 80 is listening. 

So at this point I'm trying to diagnose where the fault is. I've verified with my ISP that they don't block anything. leaving me with the possibilities of router not working correctly or something I've missed with apache. The .conf files are all default at the moment. I suppose it could be my modem as well, though that was initially set up to do complete pass through. NOTE:httpd.conf is empty, I'm not sure if that is correct or not.

I've been digging through the forums for a week to no avail. Any help or suggestions would be awesome.

Ty

---

