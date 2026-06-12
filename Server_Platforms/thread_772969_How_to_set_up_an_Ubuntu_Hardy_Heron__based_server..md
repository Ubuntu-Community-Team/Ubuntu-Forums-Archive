---
title: "How to set up an Ubuntu Hardy Heron  based server."
date: 2008-04-28
forum: Server Platforms
---

### Post by Midwest-Linux on 2008-04-28
How to set up an Ubuntu Hardy Heron  based server.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)


This tutorial shows how to set up an Ubuntu Hardy Heron (Ubuntu 8.04 LTS) based server that offers all services needed by ISPs and hosters: Apache web server (SSL-capable), Postfix mail server with SMTP-AUTH and TLS, BIND DNS server, Proftpd FTP server, MySQL server, Courier POP3/IMAP, Quota, Firewall, etc. This tutorial is written for the 32-bit version of Ubuntu 8.04 LTS, but should apply to the 64-bit version with very little modifications as well.

---

### Post by DJiNN on 2008-04-29
I'm looking to set up (asap) a home server to deal with the ever increasing amount of files & stuff on my machines.... as a sort of "Central Repository" kind of thing. Will this tutorial deal with that do you think, or do i need something a bit simpler?

Thanks in advance for any help. :)

DJiNN

---

### Post by Svenstaro on 2008-04-29
DJiNN, while the guide would certainly be good practice indeed, it is quite oversized if you're loooking at setting up a file server only. What you intent to do is actually really easy. Simply install Ubuntu Server, set up some big volume during setup consisting of multiple hard disks (LVM) and put your files on there. Then use nfs to export them to other computers. I suggest using Samba only if you need Windows machines to be able to read the files. Good luck!

---

### Post by DJiNN on 2008-04-29
> **Svenstaro said:**
> DJiNN, while the guide would certainly be good practice indeed, it is quite oversized if you're loooking at setting up a file server only. What you intent to do is actually really easy. Simply install Ubuntu Server, set up some big volume during setup consisting of multiple hard disks (LVM) and put your files on there. Then use nfs to export them to other computers. I suggest using Samba only if you need Windows machines to be able to read the files. Good luck!

HI there, thanks for the reply. 

I basically need a file server (or at least that's what i THINK i need) that will allow me to store all files (Audio, Video, apps, data etc) in one place and be accessible by several machines (Mixed Linux & widows). I'd also like to try (at some time in the near future) setting up a mail server also if that's possible, hopefully from the same unit. 

I'll do what you mentioned first though, as it'll be good to give it a try, see how it works etc. Just got to dig out the relevant hardware & cobble it altogether then i'll get stuck in. :)

---

### Post by K.Mandla on 2008-04-29
Moved to Server Platforms.

---

