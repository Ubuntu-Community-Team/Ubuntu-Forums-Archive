---
title: "Samba Help, Quick and Dirty"
date: 2009-07-23
forum: Server Platforms
---

### Post by spynappels on 2009-07-23
Can someone help me to set up a smb.conf that will allow any member of the network to access a shared folder, /home/user/shared 

This is a quick and dirty setup but is exactly what I need now.

Can anyone help me please?

---

### Post by dragos2 on 2009-07-23
> **spynappels said:**
> Can someone help me to set up a smb.conf that will allow any member of the network to access a shared folder, /home/user/shared 

This is a quick and dirty setup but is exactly what I need now.

Can anyone help me please?

Yes.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by swerdna on 2009-07-23
> **spynappels said:**
> Can someone help me to set up a smb.conf that will allow any member of the network to access a shared folder, /home/billybob/shared 

This is a quick and dirty setup but is exactly what I need now.

Can anyone help me please?
put this code in the bottom of smb.conf
```

[SHARED]
path = /home/billybob/shared
guest ok = yes
read only = no
force user = billybob
```

FFI: [Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by spynappels on 2009-07-23
That was great, thank you very much.

Stefan.

---

