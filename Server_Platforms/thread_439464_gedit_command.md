---
title: "gedit command"
date: 2007-05-10
forum: Server Platforms
---

### Post by twinax on 2007-05-10
Editing smb.conf with the command
sudo gedit /etc/samba/smb.conf  and response is "cannot open display" 
samba is installed and operational
ran sudo  testparm.. and it gave me smb.conf details.
Ideas?

---

### Post by dmizer on 2007-05-10
try nano instead:
```
sudo nano /etc/samba/smb.conf
```

---

### Post by twinax on 2007-05-11
Thanks  for the help. I installed webmin last night  and all ios well.  One thing. Which file do I edit to change to static IP address on the server?

---

### Post by Ken_Lewis81 on 2007-05-11
Setting static IP's? Check your /etc/network/interfaces.  To find out the details of this file, type "man interfaces", but the key thing to change will be the word "dhcp" to "static" in the section about the interface you want.
```
iface eth0 dhcp
``` 

You'll then need:```
iface eth0 static
    address=a.b.c.d
    netmask=a.b.c.d
    gateway=a.b.c.d
```

Take care.
Ken.

---

### Post by twinax on 2007-05-14
Hi Ken,

Thanks for the info.,. I have edited /etc/network/interfaces, but whenever I restart, the boot message is it can't read  /etc/network/interfaces. Is there another txt file I need to edit?
Thanks for your help

---

### Post by twinax on 2007-05-14
Hi ken,

No worries, I got it! Thanks for your reply. I needed also to edit resolv.conf
Regards

---

