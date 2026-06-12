---
title: "Help Needed with VirtualBox and Ubuntu 7.10"
date: 2007-11-29
forum: Virtualisation
---

### Post by spynappels on 2007-11-29
Hi Guys,

   I am running VirtualBox on a WinXP Host with an Ubuntu 7.10 Guest. The screen resolution problems are well documented, but I have installed the Guest Additions. Now, I need to edit the /etc/X11/xorg.conf to allow me to up the resolution. However, when I try to use Gedit to edit this file, it allows me to make changes but when I try to save them, it gives me the following error message:

You do not have the permissions necessary to save the file. Check that you typed the location correctly and try again.

How do I edit the file? Do I have to use the terminal? Any help would be very much appreciated, especially as I am fairly new to Linux.

Thanks.
Stefan.

---

### Post by nike984 on 2007-11-29
> **spynappels said:**
> Hi Guys,

   I am running VirtualBox on a WinXP Host with an Ubuntu 7.10 Guest. The screen resolution problems are well documented, but I have installed the Guest Additions. Now, I need to edit the /etc/X11/xorg.conf to allow me to up the resolution. However, when I try to use Gedit to edit this file, it allows me to make changes but when I try to save them, it gives me the following error message:

You do not have the permissions necessary to save the file. Check that you typed the location correctly and try again.

How do I edit the file? Do I have to use the terminal? Any help would be very much appreciated, especially as I am fairly new to Linux.

Thanks.
Stefan.


in terminal, wrote

```
sudo gedit /etc/X11/xorg.conf
```then , it will work

or you can press, alt+f2 and wrote
gksudo gedit

then, you can do what ever you want

---

### Post by spynappels on 2007-11-29
That is exactly what I was looking for. Got it sorted, thanks.

Stefan

---

