---
title: "remote gui"
date: 2009-02-18
forum: Server Platforms
---

### Post by Mr.Carramba on 2009-02-18
hi,

this question is posted in a lot of thread, nevertheless I didn't find solution that meets my need. (and works)

I want to allow users to start graphical interfaces of the applications. 
There will be more than one user connect to the server.
On the client side I will force use of x-win32 for windows users.

My installation steps
sudo apt-get install x-window-system-core xserver-xorg gnome-desktop-environment gdm
sudo dpkg-reconfigure xserver-xorg

then 
sudo /etc/init.d/gdm start

which result in error:
*Starting GNOME Desctop mananger [fail]

and it just doesn't work or give more errors :(

Thank you in advance
L

---

