---
title: "name this command..."
date: 2006-11-22
forum: Server Platforms
---

### Post by at0mic on 2006-11-22
hi guys,

whats the command to show all network adapters , their ip and their model? ifconfig doesnt show the models.


also has anyone installed ubuntu LAMP server at work? how do you like it? currently using an XP box /w apache. thinking of switching it over.

---

### Post by adwait on 2006-11-22
How about 
```
lspci
```

This will list all the PCI devices, so you'll have to look for the network devices in the list.

---

### Post by at0mic on 2006-11-22
hi... that one didnt give out any usable information. it is a stripped version of linux [firewall]

---

### Post by Akita on 2006-11-22
Lshw will get you the static info you want (vendor, name, etc). Ifconfig gets you the dynamic info like IP address.

---

