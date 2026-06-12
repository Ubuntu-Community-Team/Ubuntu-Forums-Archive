---
title: "Samba ... ?"
date: 2006-08-23
forum: Server Platforms
---

### Post by Zook on 2006-08-23
Well i think i set this up right but obviously i didn't. 

I need help with my Samba share... i put up a folder for windows users on my network to view and they cant see the folder in the "My Network Places" folder... I can already connect to their machines and copy things just fine but they cant connect to the folder that i have specified :/

Any Help?

-Zook

---

### Post by VirtuAlex on 2006-08-23
make sure you have installed samba package and added samba users with smbpasswd

---

### Post by harrysales on 2006-08-24
Is the samba user allowed permissions on the folder that has been shared?

---

### Post by VirtuAlex on 2006-08-24
If it has no permissions it will be unable to access the folder. You have to take care of permissions on shared folders yourself.

---

