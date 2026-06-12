---
title: "Using encryption option"
date: 2008-06-05
forum: Security
---

### Post by sn0m on 2008-06-05
Hi guys
Im a doctor and have got some medico-legal stuff that is confidential. I've noted that if i right click on any folder theres an option for encryption there, which i seemed to fail to make use of. Could any of you help me with that or point to any good thread where i can be enlighted about it.
Kind regards
Sokol

---

### Post by Biochem on 2008-06-05
The encryption option in nautilus uses GPG. it will create an encrypted COPY of your file and uses a public key algorithm. This is very good if you intend to transfer the file to a college. But you will be left with an unsecured file on your HDD and every time you need to access it you will have to decrypt it manually. which will again leave an unencrypted copy.

However, if you want to protect your data in case your computer is stolen, it would be more adequate to use volume encryption either through encfs, dmCrypt or Truecrypt. Ideally you encrypt the hole system so that way, you are sure no to leave unsecured document in cache, /tmp, swap.

Encfs has the particularity to only encrypt one folder wich is a good idea if other people use your computer and could be easyly used on a remote filesystem like cifs on nfs, though a trucrypt volume would probably be as easy.

---

