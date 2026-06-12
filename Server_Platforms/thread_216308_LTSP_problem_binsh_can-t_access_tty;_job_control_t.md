---
title: "LTSP problem: /bin/sh can-t access tty; job control turned off"
date: 2006-07-15
forum: Server Platforms
---

### Post by mlmarloth on 2006-07-15
Hi,

I have come accross this problem when booting clients, some work others don't, though not client specific, totally random.
The client boots and all seems well untill this message appears: "/bin/sh can-t access tty; job control turned off ".
Some times the clients work, other times not?!

Our server worked fine a few days ago, I have only installed a few programmes and updated the system. Something might have gone wrong. Anyoneone who can help me with this? School is starting on tuesday, so it would be nice to have this system up and running by then.

Thanks :)

---

### Post by kihai on 2006-07-17
This is most probably a problem with your router. I have the same problem, once I try and boot several clients at once. It's because the communication between the clients and the server works via udp-packets. Some routers just delete some udp packets, when there are obviously too many of them. This usually prevents attackers from flooding the network with udp packets. In our  case, it's too much security, but except for changing the router you can't do anything about it. I just set the clients (in BIOS) to boot one every 5 minutes, starting at 07:30 a.m.. If you have an option like this in your clients' BIOSses, you could do this as well. Only other option would be booting manually with a pause of 1 minute or so between two boots.

---

