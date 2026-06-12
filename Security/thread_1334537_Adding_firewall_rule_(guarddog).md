---
title: "Adding firewall rule (guarddog)"
date: 2009-11-22
forum: Security
---

### Post by Engromada on 2009-11-22
Firstly, sorry if i posted in wring place wasn't sure if this should be here or under networking.

My issue is that I'm trying to play runescape, an on-line Java browser game, but Guarddog is blocking it. i can access the website, and the Java applet loads fine but during the game loading, the game fails to connect to it's update server and world list server.  When i disable the firewall it loads up fine.

The game, after a while tells me i need TCP ports 43594 and 43595 open.
I defined a new protocol in the advanced tab for TCP between those ports, but i don't want to open them up to the whole internet.

I've read the Guarddog manual fully and tried to set up a DMZ with only runescape.com in the DMZ's zone addresses list, and i enabled my new protocol, http and https communtication between local and DMZ.

There is no difference after i apply the new rules, but as soon as i disable the firewall it works. i tried the same with the IP of runescape.com but after looking through my logs, it seems that the requests come from various different IP addresses.

is anyone able to see what i'm doing wrong or able to describe the proper way of enabling certain ports to a certain server only? as i say i did read the entire manual for Guard dog, but i must be missing something vital.

---

