---
title: "BIND setup"
date: 2011-04-14
forum: Server Platforms
---

### Post by coyoteboy on 2011-04-14
I've got my server system set up as a webserver within my LAN and to the outside world, and I'm using a few dynamic addresses as name servers so that I can act as my own DNS and host my domain name happily, however I'd like to set up the server as a caching DNS - i.e. I want the other LAN computers to use the server as the DNS and for my machine to get the IPs from another server if it doesn't already know it, but if it does already know it it should just return the correct IP. I've scooted around a dozen examples online but can't find what I'm looking for and can't seem to get it running on my own, it never seems to contact the outside world when it doesn't know an address, it just returns unknown. Any tips?

---

