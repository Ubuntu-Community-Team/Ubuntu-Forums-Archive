---
title: "SFTP server: how to tune speed?"
date: 2006-07-24
forum: Server Platforms
---

### Post by bricedebrignaisplage on 2006-07-24
Hi,

I've set up a SFTP server on Dapper Drake using openSSH. The download (DL from my computer) speed never goes above 40kB/s while the upload is 15kB/s. I was wondering if that was a limitation of my network (set by my ISP) or a configuration problem.
Then, can I set a different transfer rate for different users/groups?

thanks

---

### Post by paul.maddox on 2006-07-24
There will always be overhead when transferring over SSH due to the encryption. Try changing SSH's encryption method to something like blowfish which is faster.

---

