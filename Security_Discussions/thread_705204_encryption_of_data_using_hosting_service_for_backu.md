---
title: "encryption of data using hosting service for backup"
date: 2008-02-23
forum: Security Discussions
---

### Post by brickbat on 2008-02-23
Hi, I am signing up to one of those big hosting plans with 1.7 tb storage for $5 a month.  I want to use it for backups but I dont want to give them access to my music or movies or family pictures or documents.  

Does anyone know how I can have my backup data encrypted at the hosting end but clear at my end.  If I could set up a file container there where the encrypted data would go and then some sort of encrypted fuse connection that is decrypted locally?

Preferably it should be something that lets me use tools like rsync to provide the actual backup functionality.

---

### Post by brickbat on 2008-02-23
I have been doing some research and it looks like I should be able to use truecrypt.  When I figure it out I will post some instructions.

---

### Post by euler_fan on 2008-02-23
I would think at the least you could create a set of TrueCrypt containers, lock your files in them, and then upload them to your website. So long as the passwords are sufficiently secure (GPG Certificates as key files perhaps?) even if you can't work with them live you could always download them, manipulate them, and re-upload.

Good Luck.

EF

---

