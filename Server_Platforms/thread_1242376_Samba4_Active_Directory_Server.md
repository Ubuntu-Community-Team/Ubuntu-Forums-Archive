---
title: "Samba4 Active Directory Server"
date: 2009-08-17
forum: Server Platforms
---

### Post by gnomeuser on 2009-08-17
I have recently been put to an interesting little research exercise, my city' IT department runs all their stuff on Windows servers using Active Directory and Novell Groupware. However they are increasingly interested in saving money and moving support burdens to a more competetive environment so I have been asked to see what they can do.

So far the road that seems the most appealing would seem to be replacing their existing AD server with something running Linux and serving their standard Windows XP clients (a 100% switch to Linux on all machines in one go is simply unrealistic). The choices here seem to be going with SLES 11 and Zenworks or anything such as a Ubuntu Server LTS plus Samba4.

The latter is the option I like the best simply because I am not tied to Novell for support and the code is open. Sadly Samba4 is still in alpha and the required bits of AD are likely not yet finished. However I have heard that the exact scenerio I have been asked to look at, serving XP Professional clients should work.

For now we have determined that the best course might be to implement a prototype to see if this is worth exploring and investing in as well as something we get to roll out in a reasonable timeframe.

So does anyone have any experience with Samba4 and Active Directory as a server and is there an up to date PPA for Samba4 builds available.

---

### Post by koenn on 2009-08-17
Are you seriously considering rolling out alpha software in a production environment ?

---

### Post by gnomeuser on 2009-08-17
> **koenn said:**
> Are you seriously considering rolling out alpha software in a production environment ?

We just want to prove that it can be done, present a viable alternative even in an early form. Samba has a good track record for stability so we are pretty confident that in a couple of years Samba4 will be stable enough. That time frame fits the current deadlines nicely as I am to understand.

Consider this proof of concept.

---

### Post by trondhuso on 2012-08-22
Samba4 has now entered Beta-stage.

---

