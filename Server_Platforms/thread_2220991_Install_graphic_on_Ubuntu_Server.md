---
title: "Install graphic on Ubuntu Server"
date: 2014-04-30
forum: Server Platforms
---

### Post by TiTiCaMaRa on 2014-04-30
Dear all,

I'm very new on Ubuntu Server edition. And I want to have a graphic on this like in the desktop edition. How can i do this ?

Please help me out!!!

Thanks,

TiTiCaMaRa

---

### Post by ian-weisser on 2014-04-30
```
sudo apt-get install ubuntu-desktop
```

Don't get too impressed by the labels "Desktop" and "Server" in Ubuntu. They have a few differences, but servers run quite well under Desktop, and GUIs run quite well under Server.

---

### Post by steeldriver on 2014-04-30
If you don't need the *full* Ubuntu desktop with all its dependencies (including office apps and so on), then imho a nice lightweight alternative is lxde-core

```
sudo apt-get install lxde-core
```

---

### Post by nerdtron on 2014-04-30
I think the first question here "Why would you like to install a graphical desktop?" What would you need it to do?

---

### Post by TiTiCaMaRa on 2014-04-30
Hi everybody,

Thank you for replies !!

I need to know how to do it. That's the only reason (nerdtron). Thank you for the helps. I'm going to test them.

---

