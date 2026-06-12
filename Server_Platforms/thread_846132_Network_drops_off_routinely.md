---
title: "Network drops off routinely"
date: 2008-07-01
forum: Server Platforms
---

### Post by tiggyboo on 2008-07-01
I'm running an Ubuntu server and find that about every two weeks I'm unable to ping the machine - actually this happens at very close to the same time every other tuesday.  If I restart networking everything goes back to normal right away.  I guess my initial question is what log extracts or other info should I capture and potentially present to the forum in order to get to the bottom of the problem.  Our networking guy saw nothing unusual going on at the times my server drops off the network.

An initial suspicion of mine is that maybe I messed things up when I changed the machine from DHCP to a static IP... possibly a DHCP server still getting in there and mucking things up?

At any rate, any hints on where to start poking around initially would be greatly appreciated.

Thanks in advance,
Al

---

### Post by artesvida on 2008-07-01
So, this wasn't happening when the server was getting its IP address via DHCP?  Are you sure that you gave it an IP address that has been excluded from distribution (either outside the range or reserved)?

If it works when it uses DHCP, you could create a reservation in DHCP for the server (so the IP address never changes) and set it up to still use DHCP to get its address...  This doesn't really get to the root of the problem, I know, but if it works this way then you have more information.

---

