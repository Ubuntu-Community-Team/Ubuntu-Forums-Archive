---
title: "VPN or some remote access solution..?"
date: 2010-11-10
forum: Server Platforms
---

### Post by taseedorf on 2010-11-10
I don't run Ubuntu server edition, however, I do run a lot of the same services on my desktop version.  I figured this the best appropriate place to post my question.

With that being said, I would like remote SSH (among other things)  to my machine via...wherever I happen to be.  (For the most part I will be accessing services using my Android cell phone.)   Is it my understanding, that I would simply use port forwarding to forward the correct ports and then voila. Is there a way to run a secure connection to my home router, and then from there....go off onto what service I would like?  Some sort of VPN from my phone to my home, and then once connected I can execute whatever service I would like?  Curious if I can do those as to NOT have a bunch of ports open on my router.  I would like a VPN to my router, then from there have it connect to various ports on my computer...depending on what service I requested.  Is that possible?>  What would be the best solutions for remote access to a wide variety of services?  SSH, webtorrent, RDP....  I know how to implement them all but I am curious if I can do this with only showing one port open to the internet.

---

### Post by NathanBC on 2010-11-19
What VPN clients are available on Android?  The answer to that will probably guide the overall solution.

OpenVPN is supported on Ubuntu and works well for me.  You would install and configure that on your Ubuntu desktop, forward the OpenVPN ports on your router to your Ubuntu desktop, then configure your client devices and connect.  Once connected you should have the same level of access as if you were on your home network.

Again the VPN solutions supported by Android will ultimately guide the overall solution.

---

### Post by NathanBC on 2010-11-19
There is an Android group in the Ubuntu forums.  Maybe one of them is doing something like this?

---

