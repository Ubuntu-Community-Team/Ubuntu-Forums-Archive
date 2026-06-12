---
title: "Cannot boot without monitor"
date: 2011-05-11
forum: Server Platforms
---

### Post by ComputerJy on 2011-05-11
Hi everyone.

I have an ubuntu server installed on an old computer (Its a Pentium 4) and it was running fine for a while but ever since I installed the JDK (x11-common was a dependency) the system starts fine but I'm unable to connect to it through ssh unless a monitor was plugged into the computer. I also am unable to ping it, meaning its no longer connected.

Also, if I leave it running for a while it the same thing happens (ping returns destination not found). Anyone knows how can I fix this?

I don't know if this is useful but the server is connected to a wireless network that uses a WPA2 key.

Please help ](*,)

---

### Post by arrrghhh on 2011-05-11
Does that mean you installed X on the server...?  Can you remove it?

Might also be able to change the runlevel to see if it makes a difference... odd behavior.

---

### Post by ComputerJy on 2011-05-12
Only x11-common is installed. I removed it and nothing changed. And how do I change the runlevel?

---

