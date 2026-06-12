---
title: "DHCP with MAC Addresses"
date: 2009-03-27
forum: Server Platforms
---

### Post by deadowl on 2009-03-27
Essentially, what I'm doing right now with DHCP is:

```
host hostname {
  hardware ethernet XX:XX:XX:XX:XX:XX;
  fixed-address X.X.X.X;
}
```

I want to centralize IP addresses while maintaining static IPs for 30+ boxes, and while I can write a script to do all of this for me, I'm seeking as low of maintenance as possible and the syntax is quite verbose in comparison to say: hostname MAC static-address (like RARP but with hostname :D)

I've been doing some reading on classes, and while I've seen compact solutions for mac-address filtering, etc; I haven't seen it for MAC->fixed IP addresses.

I have the hostname, mac, and desired IP of each computer in a list, and eventually I want to get a DDNS setup on the same machine (which I'm also trying to get setup right now, but for some reason it's not getting me anything back).

---

