---
title: "Home Server Administration via Remote Desktop/VNC"
date: 2008-02-17
forum: Server Platforms
---

### Post by jacrider on 2008-02-17
I am running a small server (Ubuntu 7.10) at home to primarily act as a file server and webserver.

I have been messing around with Remote Desktop and VNC to administer the server pretty successfully.

My issue is that when the server needs booting, like when I am installing a RAID array or something, I need to login locally on the server, then I can use VNC on my client to administer the server.

Is there any way to allow a client to login to a session on the server without having to do it locally?  This will allow me to get rid of the screen/kbd/mouse.

Thanks.

---

### Post by perhhk on 2008-02-17
When you VNC in to the server without logging on don't you get to the login screen?


[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)


I  id this with my Xububntu and after installing an extra package it worked fine and I had to type the ip address of the computer xxx.xxx.xxx.xxx:1 and it worked and let me log on from the logon screen

---

### Post by ramstainer on 2008-02-17
login ssh
start vncserver
login through vncviewer
?

---

### Post by HermanAB on 2008-02-17
As suggested above, the best solution is to use SSH.  SSH is secure and can do everything VNC does, plus many things that VNC cannot do.  As a bonus, SSH is also easier to install and get to work.

---

### Post by jacrider on 2008-02-17
ramstainer:

I can ssh into the server.

I try to start vncserver, it responds and gives me a display number - ie. :2 or :3.

Then on my client, I vncviewer ip_address:2 and I simply get a terminal window.  I want/desire the full gnome desktop.

Am I doing something wrong?  Do I have to start gnome?  

Thanks.

---

