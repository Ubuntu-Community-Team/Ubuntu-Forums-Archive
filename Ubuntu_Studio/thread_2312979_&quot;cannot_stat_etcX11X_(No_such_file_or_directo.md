---
title: "&quot;cannot stat /etc/X11/X (No such file or directory)&quot; in Ubuntu Studio 14.04.3 amd 64"
date: 2016-02-08
forum: Ubuntu Studio
---

### Post by ectomonomorphosis on 2016-02-08
My computer screen has been going  black after the "Ubuntu Studio" spinning logo screen, with no assurance  of ever flashing on. 

I ran failsafeX in the recovery menu and received:

```
X: cannot stat /etc/X11/X (No such file or directory), aborting
```

I don't want a server environ, but my old Ubuntustudio desktop back.

---

### Post by matt_symes on 2016-02-08
Hi

You missing the symbolic link from /etc/X11/X -> /usr/bin/Xorg.

Boot to the root console from the recovery menu and type

```
dpkg-reconfigure -phigh xserver-xorg
```

This will recreate the missing symlink for you.

Then type 

```
reboot
```

This time don't select failsafe mode and boot to the desktop normally.

Does X start up for you ?

If so then please mark this thread as SOLVED.

If not then post back any errors.

If your unsure how to get to the root console then also post back.

Kind regards

---

### Post by ectomonomorphosis on 2016-02-08
Solved. Your help and expeditiousness have been greatly appreciated.

---

### Post by SurfaceUnits on 2017-02-07
In my case xorg had been removed during an installation and upgrade and it needed to be installed from the console

---

### Post by mickey6 on 2017-04-28
This solved the problem for me ("cannot stat /etc/X11/X (No such file or directory)"), as well. Thank you!

---

