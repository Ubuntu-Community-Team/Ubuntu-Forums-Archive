---
title: "internet media server"
date: 2009-08-09
forum: Server Platforms
---

### Post by sorwrith on 2009-08-09
Hi, i just finished buying the parts for a home media server for my house and im looking for some help on setting it up so that i can access it from the internet at my job since i have permission to watch movies there. i was thinking of using windows server with the media services but it seemed to require too much tinkering to set it up plus i like ubuntu better. how would i go about setting it up and what programs should i use

---

### Post by garfonzo on 2009-08-09
> **sorwrith said:**
> ... i have permission to watch movies there

uh, sweet job!?

Sorry I can't be any real help I just thought I'd point out that you can watch movies at work. Nice.

(plus bump the thread)

---

### Post by lmlypfan on 2009-08-10
there are quite a few steps to take. Here is what i have done.

Installed ubuntu server edition 9.04.

configured 4 hot swapable 1TB drives in a raid 5 config using mdadm. 

use apache2 to serve these file to the internets. I added the music index module for apache2 to stream FLAC's, MP3's, and OGGS to the web.

I flashed my linksys router with 3rd party firmware from DDWRT.
I used the services from no-ip.org to redirect my "domanin name" to my current IP address. You need this service if you don't have a static IP from your ISP. 

I think i have bookmarks with how to's on a couple of these subjects if needed.

---

### Post by lmlypfan on 2009-08-10
also, i use mediatomb to stream media via UPNP on my LAN. 
NFS and SAMBA for mounting remote drives on my ubuntu and windows desktops.

---

