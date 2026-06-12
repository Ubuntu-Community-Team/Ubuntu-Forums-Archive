---
title: "Where is Samba config?"
date: 2016-02-11
forum: Server Platforms
---

### Post by vincent-andre on 2016-02-11
Hello,

I have installed Samba to share some folder with my Windows machines. I did the install through CLI, but I shared the folders using the right-click in Nautilus.

Now, I want to check through CLI the config on those shared folders. Where can I find that as it is not in /etc/samba/smb.conf

Thanks

---

### Post by Doug S on 2016-02-11
Hi and welcome to Ubuntu forums,

As far as I know, smb.conf is, and always has been, in the /etc/samba directory. I have Ubuntu servers running 12.04, 14.04, and 16.04 (although samba on 16.04 isn't working for me yet).
Note: I am a server person, and if things are different on a desktop or wherever "Nautilus" runs, I wouldn't know.

---

### Post by bab1 on 2016-02-11
> **vincent-andre said:**
> Hello,

I have installed Samba to share some folder with my Windows machines. I did the install through CLI, but I shared the folders using the right-click in Nautilus.

Now, I want to check through CLI the config on those shared folders. Where can I find that as it is not in /etc/samba/smb.conf

Thanks

The shares you created are Samba  usershares.  They are located at /var/lib/samba/usershares.

---

### Post by vincent-andre on 2016-02-11
Thanks a lot

---

