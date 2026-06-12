---
title: "server needs an X. how do I start xfce on boot?"
date: 2010-01-19
forum: Server Platforms
---

### Post by ant2ne on 2010-01-19
I installed the server 9.10. Then I realised i needed X for an application. So Installed xfce4. how do i get xfce to launch automatically on startup?

---

### Post by kiranmurari on 2010-01-20
Hi,
You can add the following to your .bashrc/.bash_profile in the home directory to start XFCE automatically when you login on tty1:
```
if [ "$(tty)" = "/dev/tty1" ] ; then
  startxfce4
fi
```After reboot, enter your login credentials at the command prompt and XFCE will automatically launch.

Hope this helps.

---

### Post by ant2ne on 2010-01-20
I'm not sure if that will work as I may need X regardless of being logged in. I will give it a try though.

---

### Post by jfmanamtr on 2010-01-20
Are you using a login manger?If you are using one, you can always use: 
 
```
 
sudo update-rc.d gdm defaults

```
 
that will start gdm as the login manager at boot. You can replace gdm with the boot manager you use. 
 
~John

---

