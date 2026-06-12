---
title: "Samba + PAM (local users not able to login)"
date: 2010-03-12
forum: Server Platforms
---

### Post by android6011 on 2010-03-12
I just did a fresh reinstall of ubuntu-server for a few reasons. Before when I did adduser test , I could later login to the appropriate samba shares using that username and pass. But now that is not the case. I am finding myself having to manually add users with smbpasswd. Then, the passwords dont even have to match up. I checked and libpam-smbpass is installed and I have security=user set in smb.conf. 

So how can I get a user to automatically be a samba user when I create them? And be sure that the login pass is the same as if logging in locally

---

### Post by capscrew on 2010-03-12
> **android6011 said:**
> I just did a fresh reinstall of ubuntu-server for a few reasons. Before when I did adduser test , I could later login to the appropriate samba shares using that username and pass. But now that is not the case. I am finding myself having to manually add users with smbpasswd. Then, the passwords dont even have to match up. I checked and libpam-smbpass is installed and I have security=user set in smb.conf. 

So how can I get a user to automatically be a samba user when I create them? And be sure that the login pass is the same as if logging in locally

As you say you have the security set for:[FONT="Courier New"]security=user[/FONT].  This means that samba checks the smbpasswd database before users are allowed access.  If you set up the **guest** directives you will not need users to be in the database.

---

