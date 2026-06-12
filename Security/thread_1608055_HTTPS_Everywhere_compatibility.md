---
title: "HTTPS Everywhere compatibility"
date: 2010-10-28
forum: Security
---

### Post by JamButty on 2010-10-28
What is the current status of HTTPS Everywhere add-on for FF? I understand it was previously compatible, but it is not now (I am running 3.6.11 on LL).  [This]("http://www.boingboing.net/2010/10/27/sheep.html") article on firesheep has me a bit freaked.

---

### Post by OpSecShellshock on 2010-10-28
In order for FireSheep to intercept your session cookies, it would either have to be running in the same browser session that you're using to log into the affected sites (by you) or it would have to be run by another user on the same LAN who is also sniffing packets.

That said, there is an alternative to HTTPS Everywhere called Force-TLS, which is available in Mozilla's add-ons site. For that one, you do need to specify the sites yourself.

---

