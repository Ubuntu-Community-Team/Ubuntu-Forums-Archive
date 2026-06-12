---
title: "ubuntu server plus NAS togehter?"
date: 2008-08-23
forum: Server Platforms
---

### Post by bone2006 on 2008-08-23
I have a buffalo LS-STGL/R1 LinkStation pro Duo NAS box that I was told I could mount it on my ubuntu server.

I'm really not familiar with this buffalo NAS system, but I would like to have a permanent mounted area on server so that I can access the NAS through my server.

Any help is greatly appreciated?

---

### Post by windependence on 2008-08-23
Alright, you need to add this line to your /etc/fstab

```
//192.168.0.2/data   /mnt/your_mount_point   cifs   user=YOUR-USERNAME ON-UBUNTU,password=!,uid=YOUR-USERNAME-ON-UBUNTU,gid=users 0 0 
```

Of course replace the IP address with the IP of your NAS, and replace the your_mount_point and the user name stuff with your real user.

-Tim

---

### Post by bone2006 on 2008-08-23
thanks so much
you have:
user=YOUR-USERNAME ON-UBUNTU,password=!,uid=YOUR-USERNAME-ON-UBUNTU

Was that supposed to be the username on the NAS?  I'm just not sure how the server would logon to the NAS by just putting in ubuntu server info on the fstab and no login info for the NAS box?

---

### Post by windependence on 2008-08-23
Is there a password on your NAS?

-Tim

---

### Post by bone2006 on 2008-08-24
Yes, there's a username and password.  I at least don't know any way of getting on it without a username and password.  

There's an admin user and I created a few other users as well.

---

### Post by bone2006 on 2008-08-29
I guess my only option is to go into the NAS setup and allow guest users to get on the box and then mount it.

---

