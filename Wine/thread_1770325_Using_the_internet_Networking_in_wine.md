---
title: "Using the internet? Networking in wine?"
date: 2011-05-29
forum: Wine
---

### Post by cracker89 on 2011-05-29
for a lot of windows applications while on wine, it would be nice to have them be able to connect to the internet.. is that possible? 

For Eg: i installed counter strike, but for the life of me i cant figure out how to network play..

---

### Post by 3rdalbum on 2011-05-29
Wine does not stop network communication. Maybe it's some other problem at your end?

---

### Post by cracker89 on 2011-05-29
hmmm.. so as in if i try to use the gtalk for windows thru wine on linux it ought to connect to the internet and work?

---

### Post by bobwyajnr on 2011-05-29
> **cracker89 said:**
> for a lot of windows applications while on wine, it would be nice to have them be able to connect to the internet.. is that possible? 

For Eg: i installed counter strike, but for the life of me i cant figure out how to network play..

Wine does pass-through to the Linux networking stack. I presume you are not running a firewall on Ubuntu?

To check your whether you have any active packet filtering going on in Ubuntu:
```
sudo iptables -L
```
The default is, a rather insecure, pass-all (incoming, outgoing and forwarding - on all network interfaces).

I've played a few on-line games through Wine, and use a Windows email client (using a TLS secure port). So it definitely works! You do run into problems with online play and stupid DRM stuff like *Punkbuster* -that will lead to you getting kicked off online servers. Not a problem for Counter Strike! :popcorn:

Bob

---

