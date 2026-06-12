---
title: "automatic login"
date: 2021-03-16
forum: Ubuntu Development Version
---

### Post by VMC on 2021-03-16
Xubuntu won't auto login.

I've had this issue for several updates.

It worked initially, but sometimes it auto logins, but mostly I have to enter password.
Referende this fix: [https://askubuntu.com/questions/530072/how-to-auto-login-in-xubuntu-or-ubuntu-server-with-xfce](https://askubuntu.com/questions/530072/how-to-auto-login-in-xubuntu-or-ubuntu-server-with-xfce)

Which basicaslly  is this:
"/etc/lightdm/lightdm.conf"
```
[Seat:*]
autologin-session=xubuntu
autologin-user=YourDesiredAutoLoginUserName
autologin-user-timeout=0
```

Still no auto login.

I also followed this Arch document:
[https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin](https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin)
I didn't touch the "pam" reference.

---

