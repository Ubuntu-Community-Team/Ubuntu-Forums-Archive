---
title: "Likewise, domain and home folder"
date: 2012-01-02
forum: Server Platforms
---

### Post by Andysc on 2012-01-02
Hi! I have connected my Ubuntu to Windows 2008 Domain (likewise, it was so simple :D) and I can  log in, but how to set home folder for domain users in Ubuntu? I mean,  now I can login to domain but it saves home files locally, but I want to  save and load them from server. 
I want to install Ubuntu at school, but without domain connection it could be only curiosity :(

btw. good sectiion?

---

### Post by rsvancara on 2012-01-02
You need to have a network file share, which you can mounted using the autofs.  Also, in likewise, there must be a way to provide home directory information for users just like you do in LDAP.

---

### Post by rsvancara on 2012-01-02
Forgot to mention that the network fileshare can be a samba/cifs mount, but you will need to be careful of permissions and how you mount the directory.  This can be automated using autofs as well.

---

