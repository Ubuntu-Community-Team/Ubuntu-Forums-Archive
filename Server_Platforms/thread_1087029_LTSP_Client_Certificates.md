---
title: "LTSP Client Certificates"
date: 2009-03-04
forum: Server Platforms
---

### Post by wirelessben on 2009-03-04
How can I get the LTSP kiosk clients to have the same Firefox certificate authorities as a regular user on the server? When I log into the server and use Firefox, I see the certificates authorities I need. When a kiosk boots up with Firefox, it does not have them, and users have to add exceptions just to go to my default web site.

Here's my setup:
Edubuntu 8.04
ltsp-server openssh-server
ltsp-build-client --kiosk

I've tried, to no avail:
ltsp-update-sshkeys and ltsp-update-image
dpkg-reconfigure ca-certificates, ltsp-update-sshkeys and ltsp-update-image

I'm using the recommended NBD to serve the image, not NFS.

---

### Post by wirelessben on 2009-03-20
The filesystem shows that normally firefox stores certificates in 

/home/<username>/.mozilla/firefox/somerandomkey.default/cert8.db

where somerandomkey looks like "ijz0df3h".

Yet the kiosk version of Ubuntu LTSP has nothing in 

/opt/ltsp/i386/home/kiosk

Yet the kiosk does have default certificate authorities. So where are they stored? How would I add one?

---

