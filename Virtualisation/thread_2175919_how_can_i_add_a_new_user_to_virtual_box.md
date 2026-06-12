---
title: "how can i add a new user to virtual box"
date: 2013-09-21
forum: Virtualisation
---

### Post by david98 on 2013-09-21
Hi am using the virtual box and trying to boot from usb iv'e installed the extension pact for usb but keep getting this message

Failed to access usb subsystem

virtualbox is not currently allowed to access usb devices. you can change this by adding your user to vboxuser' groups.
please see the user manual for more detailed information.

I cant seem to find the manual or where you add the user groups, by the way am using ubuntu 12.04 any help would be gratefully appreciated.

---

### Post by TheFu on 2013-09-22
```
$ sudo adduser [options] user group
```

**man adduser** to learn more.

---

### Post by david98 on 2013-09-22
Thank's a lot problem solved.

---

### Post by JKyleOKC on 2013-09-23
> **david98 said:**
> I cant seem to find the manual.On the VirtualBox screen where you create a new machine or adjust the settings of an existing one, pull down the "Help" item on the menu bar and select "User Manual." It's installed automagically when you install vbox itself!

---

