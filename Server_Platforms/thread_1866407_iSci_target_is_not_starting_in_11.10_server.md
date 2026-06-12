---
title: "iSci target is not starting in 11.10 server"
date: 2011-10-21
forum: Server Platforms
---

### Post by svizi on 2011-10-21
Hi guys,

i have upgraded a server to 11.10. I just figured out that the iscsitarget is not working.
I get a FATAL: Module iscsi_trgt not found when i try to start it manually.
I suppose that there is no support at the new kernel? Is there a way to start it?

Thanks

---

### Post by miggl on 2011-10-21
I am running into the same issue, both on 32-bit and 64-bit installations.

---

### Post by svizi on 2011-10-22
I am running a 64bit dist. The problem is that i cannot even get the module build.

When i give m-a a-i iscsitarget i get this:

debian/rules:145: *** commands commence before first target.  Stop.

---

### Post by xherbert on 2011-10-22
Try to run: 
```
apt-get install iscsitarget-dkms
```
This built the required module for me and after this the iscsitarget service started :-)

---

### Post by svizi on 2011-10-24
Thanks. That worked!

---

### Post by ShawnKemp on 2012-08-27
I realize this is an old thread, but I just upgraded from 10.04.4 LTS to 12.04.1 LTS and ran into the same problem, so I wanted to add my thanks to xherbert (and this forum in general) for making the solution so easy to find. It's worth noting that you will have to start iscsitarget (sudo /etc/init.d/iscsitarget start) after the install completes.

---

