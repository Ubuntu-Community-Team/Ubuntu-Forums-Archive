---
title: "PGP Key Retrieval"
date: 2008-09-14
forum: Security
---

### Post by cj100570 on 2008-09-14
About a month ago I finally started using PGP to sign my email in Evolution. Recently my hard drive died and I need to know how to retrieve my private key.

---

### Post by tribaal on 2008-09-14
Whow. 

Not having a backup of your private key is bad: the system was designed exactly to prevent people from regenerating the same gpg key twice :(

Hopefully you created a revocation certificate and burned it to a CDROM when you created your key - you can now revoke this key and create a new one.

Otherwise, well... you public key will remain in the internet limbos for ever.

- Trib'

---

### Post by cj100570 on 2008-09-14
> **tribaal said:**
> Whow. 

Not having a backup of your private key is bad: the system was designed exactly to prevent people from regenerating the same gpg key twice :(

Hopefully you created a revocation certificate and burned it to a CDROM when you created your key - you can now revoke this key and create a new one.

Otherwise, well... you public key will remain in the internet limbos for ever.

- Trib'

Thanks. When I made the key there was an option to export it and I did. But when I import the backup it doesn't work. Unfortunately I was unaware of the revocation certificate. I guess I'll have to start all over.

---

### Post by tribaal on 2008-09-14
How exactly do you import your backup certificate? What file format is it stored in?

---

### Post by cj100570 on 2008-09-14
> **tribaal said:**
> How exactly do you import your backup certificate? What file format is it stored in?

When I clicked export after making the public & private keys it created a .asc file. Apparently it's just my public key though. And at this point scouring the net hasn't gotten me any closer to figuring out how to store my private key.

To import it I'm using the Password and Encryption Keys program.

---

### Post by Oldsoldier2003 on 2008-09-14
> **cj100570 said:**
> When I clicked export after making the public & private keys it created a .asc file. Apparently it's just my public key though. And at this point scouring the net hasn't gotten me any closer to figuring out how to store my private key.

To import it I'm using the Password and Encryption Keys program.

If you didn't backup your private key then you are out of luck. The public and private keys are different and you cannot restore or retrieve the private key using the public key.

---

