---
title: "Server cannot be accessed"
date: 2011-02-01
forum: Server Platforms
---

### Post by brucelok on 2011-02-01
My server is Ubuntu 10.04 which is used to test an Open ERP system.
However, once I setup everything and trying to be access from other workstations, it doesn't work!
Also, the server cannot found any Windows PCs in the network.

***Does anyone know how to resolve this problem???***
***Can anyone help me?***

---

### Post by brucelok on 2011-02-07
can anyone help?

---

### Post by arrrghhh on 2011-02-07
Can you give some more details?

Are you trying to access via samba or SMB from the Windows clients?  Are you attempting to authenticate with ssh?

There's a slew of other questions, but they all really depend on how you're trying to access your server, and what you want it to do.

---

### Post by brucelok on 2011-02-08
I just simply tried to access "Network", but the server couldn't grant access to Windows Network.  Also, all windows PC cannot see the server too.
They are all in the same network range~

---

### Post by arrrghhh on 2011-02-08
Can you ping the server from all the Windows clients?  That would be test #1.

If you can, test #2 would be to try to navigate to the share from a Run dialog on the Windows clients - \\192.168.0.3 for example, put in the correct IP.

Test #3 (assuming that you can ping, and the above failed) check your samba configuration.  If you want, put the output of ```
testparm
``` ^^ in those [code] [ /code] braces.

---

### Post by brucelok on 2011-02-14
Thanks~ let me try!

---

### Post by TechSupportx86 on 2011-02-15
Might also want to make sure your /etc/network/interfaces file is setup correctly. I recently had some trouble getting my samba share to show up because one of the comment lines somehow became un-commented, which made the rest of the file useless.

---

