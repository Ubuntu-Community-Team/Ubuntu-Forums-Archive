---
title: "autofs under ldap empties directories"
date: 2012-05-30
forum: Server Platforms
---

### Post by multikaos on 2012-05-30
I'm having problems with autofs. I've been using this guide: [https://help.ubuntu.com/community/AutofsLDAP]("https://help.ubuntu.com/community/AutofsLDAP"). So i'm using autofs to mount nfs shares listed in ldap.

It's working well, but my problem is that i'd like to use autofs for /home/$USER. If there allready is a $USER folder under there it should mount "on top" of that. It does that but it also "empties" /home.
There's directories in /home that i still would like to access while using autofs.

Is there any way to make autofs not "mount over" /home but only /home/$USER ?

---

### Post by kelt65 on 2012-05-30
No. If /home is in an automount map, it will take over the entire directory. When you're using the automounter, you leave the directories you give it alone ...):P

---

### Post by multikaos on 2012-06-04
Ok, thanks for your reply!
I ended upp just mounting the autofs stuff to a different folder (/home_nfs) and changed the users home dirs there.

---

