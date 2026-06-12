---
title: "Program firewall or Router firewall"
date: 2009-09-07
forum: Server Platforms
---

### Post by Cardale on 2009-09-07
I am trying to figure out wheather I should let my server act as its own firewall or my router.  I recently found out about DMZ I'm leaning in that direction as it would take a load off my routers 240mhz processor and put it on my 2.6 ghz server processor that only acts as a single small website server.

---

### Post by cybergalvez on 2009-09-07
That depends on how complicated you want to be? The router is designed to be your first line of defence, and even though its only had a 240Mhz procesor in it, your not really asking it to do much.  The DMZ opens all ports to pass through, so by using it you are opening yourself up for trouble especially if you  machine is not rock solid.  I would use the router as my first line of defense and then you can add your computers firewall if you want to leave it off if you want

---

### Post by Cardale on 2009-09-07
The router already has many other features and computer attached.  If I did have a decent firewall setup on the server wouldn't that make it safe especially if only two ports are open and those services are locked down up to known vulnerabilities?

Thanks for any advice.. Using Shorewall.

---

### Post by windependence on 2009-09-07
> **cybergalvez said:**
> That depends on how complicated you want to be? The router is designed to be your first line of defence, and even though its only had a 240Mhz procesor in it, your not really asking it to do much.  The DMZ opens all ports to pass through, so by using it you are opening yourself up for trouble especially if you  machine is not rock solid.  I would use the router as my first line of defense and then you can add your computers firewall if you want to leave it off if you want

This is not actually the way a DMZ is supposed to be set up. Basically, you have two firewalls, and the web server or mail server is in between the two firewalls. Most SOHO routers just open everything to the DMZ, but in real practice it is not supposed to be this way. The setup would be;

INTERNET ==>FIREWALL==>DMZ BOX==>FIREWALL==>PRIVATE LAN

The Private LAN can access the DMZ box, but cannot get out to the internet through the same data path as the DMZ router. The DMZ box can be seen on the Internet (by opening port 80 or whatever ports it needs), but the private LAN cannot be reached from the outside.

Personally, I use pfsense for all my firewall/router boxes. Much more stable, secure, and smaller than Linux solutions.

Having a firewall on the same box with your server is not good practice because the two are sharing resources. An attacker can easily take down your server just by launching a DDOS attack on your server, thereby overloading your firewall software and killing your server even though they never actually get in.

-Tim

---

