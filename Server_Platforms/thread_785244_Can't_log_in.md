---
title: "Can't log in"
date: 2008-05-07
forum: Server Platforms
---

### Post by Bjerrum on 2008-05-07
Hi

I have a ubuntu 7.10 server running. It works fin from ssh and also gui programs like eclipse can be opened from ssh. There is installed ubuntu-desktop gui on the server but now it's not possible to log in as desktop user.

I have the following error in .xsession-errors:

```
(process:6508): Gtk-WARNING **: This process is currently running setuid or setgid.
 ...
(process:6512): Gtk-WARNING **: This process is currently running setuid or setgid.
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=da_DK.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied
```

Can someone point me to a solution?

---

### Post by leidola on 2008-05-07
So the X-Server doesn't start?

Did you install the xserver-xorg package? AFAIK it isn't installed on ubuntu-server.
If it is installed, check the permissions of the /tmp directory.

---

### Post by Bjerrum on 2008-05-07
Yes I installed: sudo aptitude install ubuntu-desktop for some monthes ago. Untill now it have bin working fin.

What shuld the premission be: 
sudo chmod 755 /temp 
or ?

---

### Post by Bjerrum on 2008-05-07
By typping "ls -l /" i found out that there is a difference between my laptop and the server.

Server:
[FONT="Courier New"]drwxr-xr-x  10 root root  4096 2008-05-07 13:26 tmp[/FONT]
Laptop
[FONT="Courier New"]drwxrwxrw[COLOR="Red"]t[/COLOR]  14 root root  4096 2008-05-07 13:28 tmp[/FONT]

Therefor I changed the permission: "sudo chmod 777 /tmp"
Now it works. But i wounder what this "t" in the end mean? According to this there is no "t": [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Tanks

---

### Post by leidola on 2008-05-07
This is the sticky-bit, you can add it to /tmp by running

chmod 1777 /tmp

Have a look at: [http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)

---

### Post by Bjerrum on 2008-05-07
Thanks, I learned some to day ;-)

---

