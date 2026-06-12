---
title: "Network blocked via Network Adapter?"
date: 2014-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by MasterNetra on 2014-04-23
I was wondering how if its possible (and how probable) it is to be blocked from a network based on your network adapter somehow. I ask because I use the local library for internet and a few days ago I suddenly was unable to connect with my internal wireless adapter (a bcm4311 as I recall) but when I plugged in my USB Wireless Adapter they connected just fine. (On Ubuntu 14.04 btw) I dunno if for some reason and somehow being blocked (I doubt it but want to be sure) or something is going with my adapter or it's drivers. Haven't been able to test it on another network yet. Which will be a priority, but I just want to get some thoughts on the matter. Tried removing and reinstalling the driver/firmware and no luck. :/

---

### Post by King Dude on 2014-04-23
Test on another network. And why would the library have blocked you in the first place? Unless you were looking up something inappropriate... :lol:

Could they block you? Sure, it's possible. Networking isn't my specialty, but I believe network adapters have unique addresses which would allow for being blocked. Would they block you? Probably not without a good reason.

---

### Post by coffeecat on 2014-04-23
> **MasterNetra said:**
> I was wondering how if its possible (and how probable) it is to be blocked from a network based on your network adapter somehow.

Easy. All wireless routers (that I've used) have the ability to deny specific wireless NICs based on their [MAC address]("http://en.wikipedia.org/wiki/Mac_address"). But to be able to block a specific device, the router admin would need to detect the MAC address from the router's DHCP routing table first. So in the scenario you describe it is possible. But is it probable? I haven't a clue.

---

### Post by MasterNetra on 2014-04-30
Well I've connected to a my wireless router at home (it's not connected to the net as I don't have it at hom, but I've at least connected with the router itself) without a problem. So it seems like I'm blocked on that device. I was on Furcadia, which has you downloading "patch" and "dream" data in order in order to load into places, when I was blocked... Maybe they thought the patch/dream stuff was illegit stuff (you can't use the data other then to "load" into the area via the furcadia client). I was dream hopping alot. Checking out what's new (hadn't played in years). The Data for each area thens to range from less then 1MB to 30MB or so and can be encrypted (to help keep people from taking and using the patch/dream data that the makers work hard to make).

---

### Post by cariboo on 2014-05-01
Not that I'm advocating this package, but there is mac changer software available in the repositories, maybe give it a try, to see if they are actually blocking your access, or if it is due to some other reason.

---

### Post by MasterNetra on 2014-05-01
It would seem there is some other reason. Changed the mac address, but still same problem. Unless someone has another idea on how I could be blocked on a specific wireless adapter and not others then I have no clue what the problem could be. Maybe some weirdness between Driver,Ubuntu, and the router?

---

