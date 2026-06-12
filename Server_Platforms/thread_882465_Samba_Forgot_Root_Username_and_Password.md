---
title: "Samba: Forgot Root Username and Password"
date: 2008-08-07
forum: Server Platforms
---

### Post by Mauler5858 on 2008-08-07
I have forgotten my samba root username and password on my home server.  Any way to recover this?

---

### Post by windependence on 2008-08-07
Try:

```
sudo smbpasswd -a root <newpassword>
```

Replace <newpassword> with the password of your choice.


-Tim

---

### Post by Mauler5858 on 2008-08-07
That added the new user, but my problem is still is im trying to add a winxp computer to the samba domain and when i get prompted for username and password it comes back bad username/password

---

### Post by windependence on 2008-08-07
How are you trying to add the new computer?

-Tim

---

### Post by Mauler5858 on 2008-08-07
I added the machine trust account, and changed the items in the xp registry to allow it.

Now i go in xp to: right click my computer>Properties>Computer Name>Change>and type in the domain name in the box and hit ok.  Im then prompted for username and password.

---

