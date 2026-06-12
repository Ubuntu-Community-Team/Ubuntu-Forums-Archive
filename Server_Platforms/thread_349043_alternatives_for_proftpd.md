---
title: "alternatives for proftpd?"
date: 2007-01-29
forum: Server Platforms
---

### Post by sjlsam on 2007-01-29
for about 4 days i have been trying to find an ftpd that will work through a router on ubuntu

about two years ago i was using linux and was able to use an ftpd through a firewall by port forwarding the correct ports

i tried the same thing on proftpd (yes i even forwarded the passive ports too) - the FTP works locally but everyone outside the router can't get in

i understand that proftpd randomly chooses ports or something for data transfer - which makes it impossible to forward through a router

what other ftpd alternatives are there? so far i have tried the following without any luck:
glftpd
wu-ftpd
pure-ftpd
proftpd

ubuntu is a great dist of linux and the community provides outstanding support, i do not want to have to give all of this up just because i cant set up an FTP server through a router

please if there are any suggestions you can make i will be eternally grateful

---

### Post by jrock2004 on 2007-01-29
vsftpd

---

### Post by eternalsword on 2007-01-29
I can't imagine all those not working.  One question at least.  Have you set up the ftp server to run on the ip address that your router is forwarding to or is it set up to localhost?  I suppose if all else fails, you could try running filezilla's server through wine, though that would definitely be as a last resort.  I'm not sure about the safety concerns of running a server through wine.

---

