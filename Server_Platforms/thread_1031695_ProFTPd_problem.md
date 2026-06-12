---
title: "ProFTPd problem"
date: 2009-01-05
forum: Server Platforms
---

### Post by GunniH on 2009-01-05
Hey there,

I installed proftpd recently, I can login to stfp with my ubuntu username and password and browse everything but I cant upload/move nor delete anything. I always get permission denied.

Although I am using the same config as I used to use 3months ago and it worked perfectly then.

Any suggestions?

---

### Post by GunniH on 2009-01-06
bump ! =)

---

### Post by nkassi on 2009-01-06
SFTP is done using SSH and not ProFTP. Where are you trying to write to? Your home directory or someplace else like /var/www?

---

### Post by GunniH on 2009-01-06
> **nkassi said:**
> SFTP is done using SSH and not ProFTP. Where are you trying to write to? Your home directory or someplace else like /var/www?

I am trying to write to /var/www

So if I'm using SFTP I should login with the same username and password as I login to SSH and on the computer. It's the only user on the computer and it has sudo priviliges so its kinda strange that I get the permission denied error ;s

~GunniH

---

### Post by GunniH on 2009-01-09
bump!

---

### Post by GunniH on 2009-01-10
bump!

---

