---
title: "Server not accessable from internet"
date: 2010-07-01
forum: Server Platforms
---

### Post by gold7598 on 2010-07-01
So here's the deal.  I recently reformatted an old PC and threw Ubuntu server on it and have been using dyndns.com to allow me to host my own web portfolio and use it as remote storage via SSH.  The server has been running (with the occasional hiccup) since December.  Recently (at least I hope so, I've only noticed it just this week). It seemed my server had gone down (I currently live away from the location my server is at most of the time), so I called up someone at the physical location and asked them to look into it and handle it like usual. Typically restarting the networking, stopping shorewall (I installed it and then switched over to something else and havn't gotten around to removing it, so I just stopped it from running at boot) or even just rebooting the machine will do the trick.  However this time is different. After my very small bag of tricks remotely, the server is still dead from the outside world, but somehow completely fine on my local intranet. I've headed home (the physical location) to figure out what's up.  What I've come up with:  The server is running (except for this error) normally. My routers settings have not been changed, all ports are allowed that need to be. My server can ping out to sites like google. My server cannot be accessed at all from outside the intranet (web browser/ssh/ping). My server can be accessed as usual from inside the intranet.  My server is running 10.4 and notifies me of no software packages that need be updated. My website is in .aspx, and the required steps have been taken to host .aspx sites.  Any help would be appreciated.

---

### Post by dlepiane on 2010-07-01
Okay, quick questions.

1) Is your server accessible by IP address?

2) What's the last time the host record was updated with DynDNS and is the IP address correct?

3) Is SSH working but not HTTP?  Can you get either service working on alternate ports?

You seem like you've done your homework so the answer sounds mostly likely to be your ISP is blocking your traffic.  

A tool like hping2 ([http://www.hping.org/](http://www.hping.org/)) can help test this theory.  Do a traceroute to your host (hopefully that responds) to get the number of hops, then use hping to do a traceroute but with the desired port number and if those packets get dropped earlier than the expected number of hops, you can be 100% certain is the ISP.

---

### Post by gold7598 on 2010-07-01
Somehow my last post was cut, but the long and short. Couldn't access at all from outside on any port, the dyndns seemed current. And somehow after taking a 50 minute break to watch new Futurama it fixed itself after an outage of at least 2 days. This makes me think it was my ISP doing something, but I have 2 outside sources (I'm locked into my intranet) that verify my site being functional again. So... umm... /shrug...

---

### Post by lisati on 2010-07-01
> **gold7598 said:**
> Somehow my last post was cut, but the long and short. Couldn't access at all from outside on any port, the dyndns seemed current. And somehow after taking a 50 minute break to watch new Futurama it fixed itself after an outage of at least 2 days. This makes me think it was my ISP doing something, but I have 2 outside sources (I'm locked into my intranet) that verify my site being functional again. So... umm... /shrug...

Is your server on a dynamic address by any chance? The dynDNS folks have a client you can set up on your server that will automatically contact dynDNS every so often to update your details. Some routers have an option to do the update too. These options can be useful if your public IP address is likely to change every so often.

---

### Post by CharlesA on 2010-07-02
> **lisati said:**
> Is your server on a dynamic address by any chance? The dynDNS folks have a client you can set up on your server that will automatically contact dynDNS every so often to update your details. Some routers have an option to do the update too. These options can be useful if your public IP address is likely to change every so often.

That would probably be the best thing to do, if it isn't already set up.

---

### Post by gold7598 on 2010-07-02
> **lisati said:**
> Is your server on a dynamic address by any chance? The dynDNS folks have a client you can set up on your server that will automatically contact dynDNS every so often to update your details. Some routers have an option to do the update too. These options can be useful if your public IP address is likely to change every so often.


It was among the first things I did, after trying to get a script to run hourly to do so I just broke down and installed whatever it was that did that... (Sorry, been a while and I don't remember the package name)

---

