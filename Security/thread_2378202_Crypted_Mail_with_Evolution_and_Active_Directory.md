---
title: "Crypted Mail with Evolution and Active Directory"
date: 2017-11-21
forum: Security
---

### Post by kyphala on 2017-11-21
My company using Microsoft O365 with windows clients and local outlook installtions (not via web browser)
For email encryption the public user certificates are stored in microsoft active directory.

Now we try to get also linux clients running in our enviroment.

Evolution Mail with EWS working fine.
Access to global adressbook works 
Also signing and decrypting mails works.

But we got problems with encrypting mails.

When entering the email address of a user the auto complete funktion fetch the matching emails from the server but it doesn't find the public key.

Currently I have to add the public key manually to evolution key ring which works but is not very user friendly

---

