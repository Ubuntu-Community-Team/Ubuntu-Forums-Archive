---
title: "ubuntu server and dynamic ips"
date: 2007-10-15
forum: Server Platforms
---

### Post by qbeans on 2007-10-15
I'm not yet a Ubuntu user.  I'm just about to set up a dedicated server (for a single web site), and I'm considering a non-Windows OS and server software.  I clearly have a lot to learn.

The first question is that of dynamic ips.  Is overcoming this hurdle an easy thing?  Or is there a huge learning curve involved?

Thanks.

---

### Post by KCPokes on 2007-10-15
Dynamic IPs are not difficult if you are behind a router.  Easiest way is to set up a static IP for your server (since you are behind your router you are on a private network), set up Apache to listen on that IP, and forward all port 80 traffic, on your router, to your linux server.  From there you can expand to name-based virtual hosts.  ;)

---

### Post by fatbastard spice on 2007-10-15
If you're behind a router your router may have dynamic ip update functionality, or if you don't have it at the router, there's a number of tools you can use to update dyndns or the like. I've been using ipcheck for a while, but now that i've had a look at what else is in the repositories, i may have a play with ddclient.

---

### Post by qbeans on 2007-10-15
Okay, let me get this straight:

In real lay terms, my router speaks with the outside world on a dynamic address, but it communicates on the inner, private network using a fixed ip address?

Then in real lay terms, how does a computer on the outside find the fixed address behind the router?

---

### Post by MJN on 2007-10-15
It doesn't, at least not directly.

You would typically use a 'dynamic DNS' service which serves to point a domain name at your ever-changing public (and dynamic) IP address that your ISP assigns to your router.

For example, if your domain is qbeans.com then you could have, say, a DNS record of [www.qbeans.com]("http://www.qbeans.com") in a dynamic DNS service (Google for providers) which points to your current public dynamic IP address. You would usually run a small script on your PC to periodically check that your dynamic IP address on the router hasn't changed - if it has then it updates the record accordingly. Some routers are able to do this themselves (with a limited number of dynamic DNS services).

So now we have the situation where an external machine can always find your router, regardless of its current IP address, simply by using the name [www.qbeans.com]("http://www.qbeans.com") - it will always point to the correct (latest) IP address. You then tell your router to forward any web traffic (i.e. that destined to port 80) that it receives to your internal machine (which you would statically address with a private address known only to, and reachable by, your router).

That's it in a nut shell - have a Google round for terms such as 'dynamic dns' for more articles than you could ever wish for!

It's a common solution to a common problem - many people here (me included) are running on a dynamically-allocated IP address.

Mathew

---

### Post by qbeans on 2007-10-15
Mathew:

That was a great, informative reply, and not without my sincerest thanks.

-dt-
q-beans.ca

---

