---
title: "Preventing Ubuntu 10.04 server image"
date: 2011-12-28
forum: Server Platforms
---

### Post by deepakdeshp on 2011-12-28
I want to protect my Ubuntu server and want that nobody should be able to clone and restore the server using cloning tools like Clonezilla , Ghost etc. It should be usable only after using a password or any other method.

Is it possible to achieve this?

---

### Post by rubylaser on 2011-12-28
Preventing cloning a drive is really impossible if someone has physical access to the machine.  The best way to secure the data would be to encrypt the hard drive.  That way, even if a person had a clone of the drive, it wouldn't be worth anything without the key to decrypt it or the MASSIVE amount of time to brute force crack the key, if you used a strong password.

---

### Post by deepakdeshp on 2011-12-28
This is what I found on disk encryption. 
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

Any other useful links? It will have an effect on performance of the system. Was wondering how much it may affect in general.

---

### Post by rubylaser on 2011-12-28
That's a good place to start.  The performance impact should be negligible.  The main problem I've seen on the forums are when user's run into a problem, data recovery is not an easy task.

---

### Post by deepakdeshp on 2011-12-28
But at the same time I should be able to clone the system I presume I will be able to clone it after setting up the encryption.

---

### Post by rubylaser on 2011-12-28
Yes, you can still clone the disk, and that would be a good solution for a full machine image.  Or, once, it's decrypted, you can use traditional backup tools as well.  My main point was to make sure you have a backup, which is a good practice in all cases :)

---

### Post by deepakdeshp on 2011-12-28
Thank you Rubylaser. I will take take the restore difficulty into consideration and test the backup and restore.

---

### Post by deepakdeshp on 2012-03-21
I need to create a black box web server .Once built, nobody should be able to login to it, it will just act as the web server and if something goes bad, its disk will be replaced.

Only the web pages in /var/www may be served without encryption, otherwise all the remaining disk has to be encrypted.

---

