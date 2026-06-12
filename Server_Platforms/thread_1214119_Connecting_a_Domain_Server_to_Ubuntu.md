---
title: "Connecting a Domain Server to Ubuntu"
date: 2009-07-15
forum: Server Platforms
---

### Post by grizzyfizzy on 2009-07-15
Hello. I have Windows Server 2000 installed at work and have it connected to other computers in the office. I recently got a computer and installed Ubuntu 9.04 onto it and am thinking of converting if I could only solve one problem. How do I connect my Domain to a Linux machine?

---

### Post by Tux.Ice on 2009-07-15
Samba. If you mean to have a linux box as your PDC (Prmary domain controller) samba needs to be setup as it. There are many guides available. And, its not really for novice linux users.

If you mean how to connect your linux box to a domain, install Samba (its in the repos) and edit /etc/samba/smb.conf setting the WORKGROUP variable to your domain name and the SECURITY variable to DOMAIN.

If you've got any other issues, PM me.

---

