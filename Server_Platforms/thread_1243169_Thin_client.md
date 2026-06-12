---
title: "Thin client"
date: 2009-08-18
forum: Server Platforms
---

### Post by asai on 2009-08-18
Hi,
I have a issue on a 8.04 LTSP server.
When trying to boot from the client, it hangs for a while after IP address is assigned, and then a error message appear:
```
UDP checksum error
```
This message keeps coming every 5 min or so, until i CTRL-C and system halts. Any ideas on this matter?

---

### Post by drave on 2009-08-18
bad client hardware
bad network switch/hub port
bad wiring

---

### Post by asai on 2009-08-18
I have tried it on another server, same client. works perfect.
It's also the same network. That leaves us with the server. This server has up until recently been a fileserver, so I don't think it can be any networking issues. This server is also configured remote with SSH.

---

### Post by drave on 2009-08-18
i dont belive that error could come from the software stack , which is why i was leaning towards a hardware problem. could be the server.

it always worth running memtest. memory errors can manifest in many different ways

---

### Post by asai on 2009-08-23
I have found that the problem is possibly a NFS problem. For some reason the NFS server doesn't work any longer. Is there a way to completely reinstall both ltsp server and the nfs server?

---

### Post by asai on 2009-08-30
A little update on this problem.
The problem was that the tftp server wasn't running...:roll:
So now I'm able to boot from the server. The problem now is that I only get a shell with initramfs, no X. Anyone know why this happens?

---

