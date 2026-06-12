---
title: "LAN to WAN multi server environment"
date: 2011-11-20
forum: Server Platforms
---

### Post by dmattox10 on 2011-11-20
It doesnt look like this has already been posted (don't hold me to it...), so I believe I may have a unique home setup? On my LAN I have three (3) separate machines running ubuntu server. One "real server", One older AMD 64 bit machine, and One older still P4 machine. The primary server is DMZ'd from the router, uses dyn-ip tracking to a custom domain, and is world accessible. To emulate a production environment, I have set up a LAMP stack on all three, but am using the "server" for apache, AMD for storage/smb/ftp, and P4 for MySQL. Is it possible to reach all of these servers from the outside world (subdomains I guess?)? And how in my php code for the site, would I access resources on the other machines, would use the internal LAN addresses, or External? Thanks...

---

### Post by volkswagner on 2011-11-20
If you want to have multiple web servers using one WAN ip address you will want to create a reverse proxy on the DMZ machine to route requests to the second and third web servers.

You may want to search "multiple web servers with one public ip".
Also of interest may be "load balancing web servers".

For the reverse proxy some folks favor Nginx over Apache, but either will do.

---

### Post by dmattox10 on 2011-11-20
Okay. I've sat down and opened up ssh connections with all three servers, working on a reverse proxy, however, I still need to know; within the php code for the site I am working on, do I use the external address, or internal address, to save images on the P4, and access MySQL from the AMD?

---

### Post by dmattox10 on 2011-11-20
500 internal server errors... but this isn't exactly what I wanted... To rephrase, I want my php code to be able to make requests to the other two servers, and display content from them, but they don't really need an external address. Should I post on a coding forum?

---

### Post by volkswagner on 2011-11-20
I would say it is safest to use internal addresses or hostnames.  I would not expose the MySql to world accessible.  If you want to use external hostnams (incase you move these servers off the same LAN) you can setup aliases in /etc/hosts for each machine.  Point the external hostnames to the local ip.

---

### Post by dmattox10 on 2011-11-20
Thank you. I won't ever move the servers. Once the site is done, my partners and I will acquire servers to host it on, and I will move on to the next project on my servers... How do I mark this as solved?

---

