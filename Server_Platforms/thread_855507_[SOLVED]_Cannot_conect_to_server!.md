---
title: "[SOLVED] Cannot conect to server!"
date: 2008-07-10
forum: Server Platforms
---

### Post by batty on 2008-07-10
Hello, I was doing so well!

I can no longer connect to my Ubuntu 8.04 server from my Ubuntu and Kubuntu PCs. I cannot see files or ping from PC to server or server to PC. Worked fine yesterday.

If I boot into windows I can see the server and copy files both ways.

Any advice why my server or K/Ubuntu PCs can no longer see each other?

Cheers Dave

---

### Post by k_grdn on 2008-07-10
Hi,

Try going through thefew OSI layers,

layer 1 - check physical connections, hardware.
layer 2 - arp cache, mac, switching
layer 3 - ipaddress, network layer
layer 5 - telnet
layer 7 - ssh

Regards,

k_grdn

---

### Post by batty on 2008-07-10
Hi, Thanks for reply.

It turns out it was my fault not ubuntu :oops:

I have a squeezebox music player attatched to my network.Although I set it up with a static IP address it suddenly decided to pick it's own address which clashed with that of my PC. Which obviously threw my network into meltdown.
As I don't normally use windows it's not set for a static IP address, unlike my Linux box, and therefore picked an address that didn't clash with the squeezebox!

I can't believe I almost thought Windows was better than Linux. 

Dave

---

### Post by cariboo on 2008-07-11
Pick ip addresses outside of the range that dhcp sets, then the conflicts won't happen.

Jim

---

### Post by kroon78 on 2008-07-11
Good point

---

