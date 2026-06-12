---
title: "can i share files with my friend's comp?"
date: 2008-03-15
forum: Server Platforms
---

### Post by brohitv on 2008-03-15
i and my friend are usinf linuxmint but both of us have a different inter net connection .
can we both share files between us ?
if yes please tell me how to do it.

---

### Post by volkswagner on 2008-03-15
You can use FTP service.  You can create users, folder permissions, use SSH. Both options will require keeping track of your external ip if it changes (dynamic ip).

---

### Post by HermanAB on 2008-03-15
FTP, NFS, SSH, Samba.

---

### Post by netlogic on 2008-03-16
> **brohitv said:**
> i and my friend are usinf linuxmint but both of us have a different inter net connection .
can we both share files between us ?
if yes please tell me how to do it.

SSHFS if they are both linux. It works right away and very secure. 
PPTP or Openvpn if windows is involved.
FTPs if he is strictly downloading and uploading files. Make sure you configure your PAM for FTP, so only certain local accounts are allowed to FTP.

---

