---
title: "Browsing from Vista gives &quot;No Route to Host&quot; when browsing to LAMP server"
date: 2009-07-08
forum: Server Platforms
---

### Post by Chris of Arabia on 2009-07-08
I've not had the LAMP server running for a couple of months (been busy with other things), but when it was last running, I had no problem browsing to the server across my home LAN. Nothing that I can think of has changed in the set-up, it just doesn't work as it did.

I can still:

Make an SSH connection using PuTTy

FTP into www root using FileZilla

Ping the server (5ms response)

but cannot make a browser connection and constantly receive a "No route to host" message. Can anyone make any suggestions on what to look at?

Edit: Should have said that browsing on the server locally works fine and I have a static IP of 192.168.0.100 set on the server

---

### Post by swerdna on 2009-07-08
So do you mean this address in the browser evokes the error message: [http://192.168.0.100?](http://192.168.0.100?)

---

### Post by Chris of Arabia on 2009-07-08
Exactly.

---

### Post by Chris of Arabia on 2009-07-08
Problem solved. I had one of those lightbulb moments.

I'd forgotten the ISP had been having proxy issues, and the browser was set to use one of their proxies. Just needed to add 192.168.0.100 to the list of addresses the proxy _wasn't_ to be used for... :oops:

---

### Post by swerdna on 2009-07-08
Excellent

---

