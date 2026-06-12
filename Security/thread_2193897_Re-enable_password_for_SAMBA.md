---
title: "Re-enable password for SAMBA"
date: 2013-12-15
forum: Security
---

### Post by SuperFreak on 2013-12-15
I have two Ubuntu PCs connected through Samba to each other. The client computer had settings that meant whenever I tried to open a shared Samba directory I was asked for login and password. Foolishly one day I entered my login info and checked never check for passwords again. I now want to put it back the way it was. I have tried editing the smb.conf file but I can't get the settings back (I backed up the  file before I changed it). I don't want to create another SAMBA user unless it is necessary because I think my shares will have to be scanned all over by the client computer.

---

### Post by bab1 on 2013-12-15
I believe the password is saved in the Ubuntu keyring.  You should be able to delete the share password using Seahorse,  See here for an example: [http://askubuntu.com/questions/77127/how-to-discard-saved-password-for-samba-share-in-unity]("http://askubuntu.com/questions/77127/how-to-discard-saved-password-for-samba-share-in-unity")

---

### Post by SuperFreak on 2013-12-15
Thanks...That was easy

---

