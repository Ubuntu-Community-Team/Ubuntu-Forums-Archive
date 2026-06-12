---
title: "Server Situation"
date: 2009-05-14
forum: Server Platforms
---

### Post by number65 on 2009-05-14
I'm setting up a Intel Xeon 2.0ghz Quad Core server with 4 SATA II 500gb (in a RAID 5 setup) hard drives. I'd like to install ubuntu server edition 8.04 LTS.

I have about 35 workstations in the office, and need the server to act as a DHCP server (maybe DNS-- I don't know) and Samba server for file sharing. That is it. No mail, no php, no apache. Will it be able to handle the workload of all 35 workstations access the same Microsoft Access database file on the server and using it as a shared drive for constant reading and writing?

---

### Post by TwiceOver on 2009-05-14
Should be fine for all of that.

---

### Post by Iowan on 2009-05-14
Check into DNSMasq for DNS/DHCP server. I haven't tried it yet, but it's supposed to integrate the two services.

---

### Post by wirelessmonkey on 2009-05-14
dhcpd and samba will do all you need...

---

### Post by number65 on 2009-05-15
Thanks for your help! :)

---

