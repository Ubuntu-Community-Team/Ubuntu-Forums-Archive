---
title: "How to access Samba from outside of my network"
date: 2014-08-30
forum: Server Platforms
---

### Post by the-paul-84 on 2014-08-30
Hi!
I set up a SAMBA server a few months ago and it is working great. However, I set something in the smb.conf that only allow me to log in from my local network.

I can't seem to remember where that is set in the file. Can anyone help? Thanks in advance.

---

### Post by volkswagner on 2014-08-30
Don't!

SAMBA is not meant to be exposed to the internet. You will be opening yourself up for attack.

To access SAMBA shares from outside your network, you'll likely want to setup VPN access.

You can also setup SFTP to the SAMBA share, but depending on users and share info, maintaining file permissions
may require additional configuration if you will be writing to the share remotely.

---

