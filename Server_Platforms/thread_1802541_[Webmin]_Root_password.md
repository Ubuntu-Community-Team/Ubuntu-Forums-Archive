---
title: "[Webmin] Root password"
date: 2011-07-12
forum: Server Platforms
---

### Post by ki4jgt on 2011-07-12
So, after reading a few reviews and looking at a thread I had started a while back on here. I've decided to go with Webmin for site hosting. The documentation online says, I need my root password to login. I went to another site, which says I could do this:
> /usr/libexec/we /etc/webmin admin foo
to change the admin account to foo for a password. I tried it, invalid command file/folder not found. Anyone have any experience with it?

---

### Post by Perfect Storm on 2011-07-12
Moved to Server Platform forum.

---

### Post by MacTuxLin on 2011-10-12
cd /usr/share/webmin
./changepass.pl /etc/webmin foo newpassword

---

### Post by elico on 2011-10-13
just get into su mode using
sudo su
and change the password using
passwd

---

### Post by CharlesA on 2011-10-13
Last I checked, you can just use any account with sudo access with webmin.

---

