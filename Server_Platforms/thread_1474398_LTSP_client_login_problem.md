---
title: "LTSP client login problem"
date: 2010-05-06
forum: Server Platforms
---

### Post by pft0 on 2010-05-06
I have fresh installed ubuntu 10.04 and added ltsp-server-standalone for my thin client to login.
When the client login, i hear the ubuntu login theme sound, but before it completely loaded the desktop, then the display would blank and said something about GLib error.

i can completely login and use my desktop if i logged in at the server, but after i logged out, i can't use the think client again.

i had the dhcp server on windows server 2003 and setup the PXE parameters according to the ubuntu community wiki.

Any idea what i may done wrong?

---

### Post by kfleten on 2010-05-26
I have read several posts in the forum about this, but have seen no solutions. 
I would suggest:
sudo ltsp-update-sshkeys
sudo ltsp-update-kernels
sudo ltsp-update-image --arch 1386
sudo service tftpd-hpa restart

And then completely power off your thin client (not just reboot) and then restart. This makes LTSP login possible - but it seems like the error returns on a random thin client for a random user after a random time...

---

