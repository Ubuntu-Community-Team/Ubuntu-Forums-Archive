---
title: "GUI on Ubuntu server"
date: 2009-10-07
forum: Server Platforms
---

### Post by dujlinvik on 2009-10-07
Hi All!

I have installed Ubuntu Server 8.04.3 on a local machine in my company. Unfortunately I'm not a Linux server administrator so I thought it's a good idea to install GUI as well, just to configure some stuff I'm not able to configure from the command prompt (like MySql databases and tables, printer setup, etc.).
So I installed ubuntu desktop and started
```

startx

```

First problem with that is that the desktop is loading too slow and the server responds too slow in the GUI. Now when I boot to Ubuntu, the GUI is loaded automatically, but I want now the command prompt environment.... How can I bring it back? Uninstall ubuntu desktop GUI or what?

Thank you for your help!

---

### Post by kevin11951 on 2009-10-07
you can move to cli using ctrl+alt+f1 (or 2,3,4,5,6) then from there kill gdm using "sudo /etc/init.d/gdm stop"

For future reference use webmin, it is a web based gui for most if not all server functions.  Just make sure you use it behind the router only, because there are some issues with security.

---

### Post by Waappu on 2009-10-07
Hi,

This guide may help you disable GDM on boot
[http://cviorel.easyblog.ro/2008/07/02/enabledisable-gdm-in-ubuntu/](http://cviorel.easyblog.ro/2008/07/02/enabledisable-gdm-in-ubuntu/)

Then you can use startx command, when you need GUI

---

### Post by dujlinvik on 2009-10-07
> **kevin11951 said:**
> 
For future reference use webmin, it is a web based gui for most if not all server functions.  Just make sure you use it behind the router only, because there are some issues with security.

Thank you kevin,

I've installed the latest webmin now. You are talking about security. Please have a look at the attached topology tree and let me know if it IS secure to access the server through the browser (webmin) from terminal 1 or 2?

I really appreciate your help!
Regards

---

### Post by dragos2 on 2009-10-07
> **dujlinvik said:**
> Thank you kevin,

I've installed the latest webmin now. You are talking about security. Please have a look at the attached topology tree and let me know if it IS secure to access the server through the browser (webmin) from terminal 1 or 2?

I really appreciate your help!
Regards

What did you used to draw that ?

---

### Post by dujlinvik on 2009-10-07
> **dragos2 said:**
> What did you used to draw that ?

Adobe Photoshop CS2

I know it's not a masterpiece but I was in rush!
:P

---

