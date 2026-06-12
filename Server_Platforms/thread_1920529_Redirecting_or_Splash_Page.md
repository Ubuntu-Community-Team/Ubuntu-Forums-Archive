---
title: "Redirecting or Splash Page"
date: 2012-02-05
forum: Server Platforms
---

### Post by phocus on 2012-02-05
Hello,

I am working on a project for which I am designing a hotspot of some sort. I am using a small nettop computer, running Ubuntu 11.10, which is using apache2 to set up its own server. The desired functionality of the hotspot is to be able to broadcast a website (html and php codes all included on a connected external hard drive) on its own wireless network so that users can connect to the website even when there is no internet access.

The problem I am running into now is that right now, in order for the user to view the website they are having to connect to my network, open up a browser and then type in the IP address of my nettop. I am looking for a way to redirect they instantly to my website right when they open up a browser (kinda like starbucks does with their log in page). It will not be to a separate authentication page, but to the actual homepage for the website. This is needed because it is ridiculous to have all users know my IP in order to access my site. Please if you have any idea how to do this or any advice, it is much appreciated!

Thank you,
phocus

---

### Post by howefield on 2012-02-05
Thread moved to the "*Server Platforms*" forum.

---

### Post by volkswagner on 2012-02-05
You may want to check out the list of available [CaptivePortals]("http://en.wikipedia.org/wiki/Captive_portal") available.

You may also be able to use [Squid as proxy server and force home page]("http://wiki.squid-cache.org/ConfigExamples/Portal/Splash").

---

### Post by phocus on 2012-02-06
I have a netgear n300 around somewhere I believe, if i were to use a router would I need to bother with Squid? I am still very new to this stuff, so looking at the link you provided for Squid intimidated me alittle, I wasn't able to follow much of the code example they provided...

---

### Post by volkswagner on 2012-02-06
I don't see that router on the DD-WRT compatible list.  If you use a router and flash it with DDWRT you can skip squid and use the built in hotSpot config.

---

