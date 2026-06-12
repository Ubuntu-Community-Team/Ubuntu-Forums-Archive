---
title: "Firewall in Ubuntu"
date: 2008-11-11
forum: Security
---

### Post by Mclinux on 2008-11-11
Hello,

Could anyone tell me where I can access my firewall settings with ubuntu?  I'm trying to modify it to allow access to certain websites using different ports and I can't find an interface to change anything.

---

### Post by tuxxy on 2008-11-11
Your best using [ufw]("https://wiki.ubuntu.com/UbuntuFirewall") open terminal and type ufw for a list of available commands.

```
ufw
```

If you would prefer a graphical frontend to ufw rthan CLI you could install [gufw]("http://gufw.tuxfamily.org/index.html")

```
sudo apt-get install gufw
```

---

### Post by Mclinux on 2008-11-11
Thanks

---

### Post by hyper_ch on 2008-11-12
by default the firewall does not prevent you from accessing anything.

---

