---
title: "Crazy Windows behavior under Samba, why is that?"
date: 2009-03-02
forum: Server Platforms
---

### Post by PryGuy on 2009-03-02
Good day to all of you! I'm setting up my Samba server and I got the following problem. I have 'security = user' and I've got both restricted and public shares on my Samba server. Everything's fine under Linux, but in WindowsXP everything's fine only if I first login as a user (login/password combination) accessing a first share, I can access guest shares hands down after that, but weird thing happens if I first access a guest share (WindowsXP logins as nobody), then try to access a password protected share, Windows says that I do not have access rights, blah, blah... Is that normal?

Thank you in advance,
Peter.

---

### Post by Yashiro on 2009-03-03
Try map to guest = Bad Password instead of Bad User in /etc/samba/smb.conf perhaps?

---

