---
title: "LTSP Arch help"
date: 2008-10-07
forum: Server Platforms
---

### Post by jv13613 on 2008-10-07
Hi,
I am new with LTSP. I was wondering is it possible to have one LTSP sever with thin clients that use different archs. Like have and i386, sun, and mac as thin clients on one server. If you can could you tell me how. :confused:

---

### Post by lykwydchykyn on 2008-10-07
Well, theoretically I think you'd edit your dhcp config to send different boot files to the thin client depending on the MAC address of the adapter, though there might be a better way to do it.

What I'm not sure about is if you can make a client image that supports anything but i386.  In LTSP5 the client image is generated using the ubuntu repositories (or whatever distro you're using), so I would imagine you're limited to whatever the distro supports.

---

### Post by jv13613 on 2008-10-07
I was confused I saw something on ltsp k12. I saw that u can have a defualt boot file for etherboot on rom-o-matic. But i don't know what to do. If a expert could do it I think it would be possible. I would like if you could look into it

---

