---
title: "weird IP change related issues"
date: 2005-12-06
forum: Server Platforms
---

### Post by OneSeventeen on 2005-12-06
I've got some weird issues with changing IP addresses, here's some background info:

I've been simply modifying /etc/networking/interfaces with the proper IP and subnet mask, then running:
/etc/init.d/networking restart

This works immediately, but the first time I gave it a static IP, there was a program running in the background that would give it a new dynamic IP each time the initial one expired.  (Killing the process that did this fixed that problem, but I think rebooting may work as well.)

Now, I've assigned it a new static IP (I got one ending in 42, and the server name is Marvin!) and it was accessible while I was at work, but now that I'm home, I can't connect/ping/anything.

I can connect to other webservers in the same server room, just not my ubuntu box.  Could this be because I only filled out the IP and subnet?  Do I need to fill in more details?

Any help would be greatly appreciated.  (I'll be at work in about an hour, so I'll post if it is still available through that network.)

---

### Post by OneSeventeen on 2005-12-06
Okay, here I am, at my office, and I can connect just fine.
I got a call from a different building on campus, and they cannot connect to the webserver.

I then added the gateway to the /etc/network/interfaces file and all is well!

Don't forget, if you want your webserver visible to the world:
**Define the gateway option!**

---

