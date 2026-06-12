---
title: "[SOLVED] Ip Masquerading explanation"
date: 2007-07-26
forum: Server Platforms
---

### Post by Andruk Tatum on 2007-07-26
My house currently has a fileserver setup for house members and a few guests.  I am attempting to setup ICS/IP masquerading on the server (so the landlord does not have to go wireless).

I took a look at the Ubuntu Server Guide (good stuff in there).

What does the "/16" in this command mean?

sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o ppp0 -j MASQUERADE

Any links, etc to detailed explanations would be great.

Thanks!

---

### Post by Andruk Tatum on 2007-07-26
[http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#Historical_background](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#Historical_background)

Found the answer.  Thank you to everybody on #ubuntu and wikipedia.

And you people for hosting this now pointless post.  Feel free to delete it if you so choose.

---

### Post by Tautoa on 2007-07-26
If you post the answer that you found, not only are you contributing back to the community, but also, anyone with the same problem, will not find this thread to be so pointless :)

---

