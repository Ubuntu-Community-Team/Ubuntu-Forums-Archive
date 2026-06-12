---
title: "cant' get samba to work"
date: 2010-05-02
forum: Server Platforms
---

### Post by alambre on 2010-05-02
i recently installed ubuntu server 10.4 and i can't seem to find the samba service, when i tried running /etc/init.d/samba restart,
command not found and when i typed samba it says "The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4" but i have my smb.conf on /etc/samba/smb.conf, tanx

---

### Post by Ryan Dwyer on 2010-05-03
Yes, smb.conf exists on a fresh install even when Samba isn't installed. I think it's used to connect to other Samba servers, but if you want to run your own Samba server then you need to install the package.

---

### Post by alambre on 2010-05-03
tanx, i'm prompted to install samba4, is the samba4 config file still the smb.conf at /etc/samba/???

---

### Post by Ryan Dwyer on 2010-05-03
I haven't played around with Samba4 yet, but I imagine it's the same file. It is for Samba3.

---

