---
title: "How do I start Gnome (installed it using aptitude)"
date: 2006-03-16
forum: Server Platforms
---

### Post by wgregori on 2006-03-16
I just installed the Ubuntu server edition. Following a successfull install I used Aptitude to install Gnome.  The installation seemed to go okay but now how do I start Gnome?

Thanks,
Wayne

---

### Post by daniel2501 on 2006-03-16
Hrm... After rebooting, if all the dependencies were installed, gdm should come up after booting. Make sure you have gdm installed and try *sudo gdm*

---

### Post by VinceDee on 2006-03-16
I hope this helps:

```
sudo /etc/init.d/gdm start
```

Vince

(EDITED for a better solution)

---

### Post by wgregori on 2006-03-16
Thanks for the tips but I'm still having problems.  I think my problem is that Gnome may not be installed.  I went to the /etc/init.d directory and could not find "gdm".  Perhaps you could tell me how I need install Gnome.  The way that I tried to do it was to use Aptitude and install "the Gnome Desktop System".  Is there another way to install it?

Thanks,
Wayne

---

### Post by VinceDee on 2006-03-16
To install Gnome from the command line:

```
sudo apt-get install ubuntu-desktop
```

Vince

---

