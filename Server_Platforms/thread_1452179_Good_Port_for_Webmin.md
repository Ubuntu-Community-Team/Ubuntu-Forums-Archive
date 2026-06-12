---
title: "Good Port for Webmin"
date: 2010-04-11
forum: Server Platforms
---

### Post by Vegan on 2010-04-11
I was wondering if I can use a different port for WebMin down below 1024 where I forward ports to my Linux box, rather than the current 10,000.

The reason is I forward higher ports to the Windows machine at present.

The goal is to keep Linux services down in the low port range. Suggestions?

---

### Post by NullHead on 2010-04-11
Honestly I really wouldn't change the webmin port just for organizational sake.

---

### Post by CharlesA on 2010-04-11
Are you forwarding them via SSH or the router? You can always change which port you use locally and still have it forward it to the machine using port 10000.

---

### Post by bab1 on 2010-04-11
> **NullHead said:**
> Honestly I really wouldn't change the webmin port just for organizational sake.
+1

There are 2^16 (0 - 65,535) ports available on each computer. The first 1024 ports are defined by common convention.  

The OS (in particular the TCP/IP stack) doesn't care what the decimal number is.  It's just the number of *'flipped bits"* in the packet header.  All TCP ports are 16 bits long, so what is the difference between  and 0000000000110101 (53) and 00000**[COLOR="Red"]1[/COLOR]**0000110101 (1077).  The difference is only one flipped bit (1024).

The point being the OS reads the bitstream not the decimal equivalents.

---

