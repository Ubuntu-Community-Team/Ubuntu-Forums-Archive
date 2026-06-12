---
title: "Unable to Connect to server remotely"
date: 2013-06-10
forum: Server Platforms
---

### Post by RGM79FP on 2013-06-10
So I just got some old computers that support Ubuntu quite nicely. Recently I installed Ubuntu Server 12.04 LTS and now I have deceided that I wanted to start playing with it :KS. 
Now the issue:
I cannot connect to my the server remotely, I am assuming it has something to do with the router and/or settings in Ubuntu. Regardless, I was able to connect locally through my own router with no problems. But once I would leave and connect from somewhere else I was unable to connect (I would get a "Connection Timed out").

I tried:
Enabling some port forwarding in my router

Updating SSH Server

and no luck thus far. 
Any advice would be nice

---

### Post by Lars Noodén on 2013-06-10
So just to be sure, you have openssh-server installed and running and you can connect to it from other machines on the same LAN.  But if you try to go through the router, it times out?

The obvious problem is one you've already addressed: port forwarding on the router.  You might double check to make sure the settings are correct.  Can you connect via the external IP number from another machine on the same LAN?

Also, you might see if you have a nasty ISP that is blocking port 22. Try a scanning service to see if port 22 is blocked by your ISP: [http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by d4m1r on 2013-06-10
What kind of internet do you have (DSL/cable)? What kind of router? Can you write down your home IP and ping it from somewhere else?

Need more info to help yah out.

---

### Post by SeijiSensei on 2013-06-11
One quick test to check if port 22 is blocked is to forward some other port on the router, say 2222, to the server's port 22, then connect remotely via ssh with "ssh -p 2222 user@host".

---

