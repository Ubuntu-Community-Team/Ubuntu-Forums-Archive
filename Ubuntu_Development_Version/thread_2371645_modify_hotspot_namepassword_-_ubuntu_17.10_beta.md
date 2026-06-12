---
title: "modify hotspot name/password - ubuntu 17.10 beta"
date: 2017-09-17
forum: Ubuntu Development Version
---

### Post by durk22 on 2017-09-17
When I create a wifi hotspot I cant set the name and password.
I tried to modify the file /etc/NetworkManager/system-connect/Hotspot but it gets overridden by the hotspot creation dialog.
Which file or procedure do I need to modify?

---

### Post by howefield on 2017-09-17
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by jbicha on 2017-09-17
After editing that file, try:

```

sudo systemctl restart NetworkManager

```

(That command will temporarily disconnect you from the network and the Internet.)

---

### Post by jbicha on 2017-09-17
The hotspot name is set to your computer's name which can be set from Settings>Sharing or Settings>Details>About.

---

