---
title: "access xp share from command line"
date: 2008-06-06
forum: Server Platforms
---

### Post by smacintyre569 on 2008-06-06
Ok I am new to Ubuntu Server, but I have successfully set it up as a basic file server. 

I can browse to the file shares on the server from my xp box with no problem. What I would like to have some help on is browsing the shared folders on my xp box from the server command line within Ubuntu. (e.g. ls //station1/shares)

"Staion1" being the xp box and "shares" being the shared folder on the xp box.

The Ubuntu server is static and the xp box(es)are dchp.

tia

---

### Post by quelx on 2008-06-06
Install **smbclient** and **smbfs** on the server. You may need to replace **station1** with the actual IP for the machine.

```
sudo smbmount //station1/shares /mnt -o user=*username* password=*password*
```

---

### Post by smacintyre569 on 2008-06-06
Thank you for the solution :)

---

