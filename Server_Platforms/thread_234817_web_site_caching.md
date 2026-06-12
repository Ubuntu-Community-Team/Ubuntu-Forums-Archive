---
title: "web site caching"
date: 2006-08-12
forum: Server Platforms
---

### Post by rekahsoft on 2006-08-12
Hi all...i have just got a server and i want to have it cache (AKA save) all the websites that are visited by computers on my network...how do i do this? Note i have a router...so would i have to have the server behind the router?

---

### Post by fnjordy on 2006-08-12
Check out the software package called Squid, if you want virus checking in addition have a look at HAVP.

---

### Post by rekahsoft on 2006-08-12
ok...now i will have to have the server set as a gateway so i can do this right? so basicly the flow will be:
**internet > server > wireless router > network computers**
Is that right?

---

### Post by fnjordy on 2006-08-13
Not necessary although an option.  Squid can transparently web cache, in which case it might need to be the gateway machine although it does not need to be, but more often you just configure your web browser to point to Squid instead.  Check out the "Connection Settings" in Firefox.

The Squid FAQ has a question on [intercepting web traffic]("http://www.squid-cache.org/Doc/FAQ/FAQ-17.html").

---

