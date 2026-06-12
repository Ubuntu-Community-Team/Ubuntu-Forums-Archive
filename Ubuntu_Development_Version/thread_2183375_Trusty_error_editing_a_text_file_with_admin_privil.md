---
title: "Trusty error editing a text file with admin privileges"
date: 2013-10-24
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-10-24
Is there a fix for this?

```
cavsfan@cavsfan-MS-7529:~$ gksudo gedit /etc/default/grub

(gedit:14285): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
cavsfan@cavsfan-MS-7529:~$ 

```

---

### Post by QDR06VV9 on 2013-10-24
> **Cavsfan said:**
> Is there a fix for this?

```
cavsfan@cavsfan-MS-7529:~$ gksudo gedit /etc/default/grub

(gedit:14285): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
cavsfan@cavsfan-MS-7529:~$ 

```
Have you tried
 ```
gksudo nautilus
```
And then just navigate to etc/default/grub, 1st back it up, then make your changes save and close.
Regards

---

### Post by ventrical on 2013-10-25
It  worked fine here but then I most always use the code you have  stated.  It is easier to navigate between  folders and the text editor that way.

Regards..

---

### Post by Cavsfan on 2013-10-25
Thanks! I'll do that. :)

---

### Post by Cavsfan on 2013-10-25
That worked without giving me any errors!

Cheers! :)

---

