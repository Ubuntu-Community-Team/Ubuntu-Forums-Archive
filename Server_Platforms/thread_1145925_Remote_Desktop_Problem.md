---
title: "Remote Desktop Problem"
date: 2009-05-02
forum: Server Platforms
---

### Post by Face_Man on 2009-05-02
Hello All,

I'm new to Linux OS's and this is my first week. i install ubuntu 9.04 server and install ubuntu-desktop. So far so good, I was able to remote desktop the box from Windows OS using VNC. However, each time i reboot the box i have to go to box and login and after that i can remote desktop the box. is there anyway i could remote desktop the but without having to login manually.

Any help would be much appreciated.

---

### Post by praveenmarkandu on 2009-05-02
> **Face_Man said:**
> Hello All,

I'm new to Linux OS's and this is my first week. i install ubuntu 9.04 server and install ubuntu-desktop. So far so good, I was able to remote desktop the box from Windows OS using VNC. However, each time i reboot the box i have to go to box and login and after that i can remote desktop the box. is there anyway i could remote desktop the but without having to login manually.

Any help would be much appreciated.

you can try this
[http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/](http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/)

---

### Post by Face_Man on 2009-05-02
well, since i did what is in article  i cannot remote desktop the box at all.

---

### Post by cariboo on 2009-05-02
If your server isn't outward facing, why not just set autologin? Go to System-->Administration-->Login Window-->Security-->Enable Automatic Login.

---

### Post by Face_Man on 2009-05-02
I was able some how to connect to the login screen x11vnc. However, after i enter my username and password i get this error

caught XIO error:
02/05/2009 19:37:49 deleted 36 tile_row polling images.
 
any idea

---

### Post by HermanAB on 2009-05-02
Howdy,

VNC is not a good choice for managing a server. You should install ssh-server from synaptic, then connect to it from Windows using Xming (run it first!) and PuTTY.

SSH can do everything VNC does and much more and it is secure too.  It is the 'standard' tool for managing Unix machines remotely.  Once you start using it, you'll quickly learn why.

---

### Post by Face_Man on 2009-05-02
> **HermanAB said:**
> Howdy,

VNC is not a good choice for managing a server. You should install ssh-server from synaptic, then connect to it from Windows using Xming (run it first!) and PuTTY.

SSH can do everything VNC does and much more and it is secure too.  It is the 'standard' tool for managing Unix machines remotely.  Once you start using it, you'll quickly learn why.
well, i am using PuTTY to connect to the server first and after that i try to use VNC 
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by krunge on 2009-05-03
> **Face_Man said:**
> I was able some how to connect to the login screen x11vnc. However, after i enter my username and password i get this error

caught XIO error:
02/05/2009 19:37:49 deleted 36 tile_row polling images.

Your login greeter program, GDM, by default kills all X clients just after the user logs in (x11vnc is an X client) and then starts the user's session.

Simply repeat the steps and the 2nd time you'll have your session.

To disable this annoying aspect of GDM set the KillInitClients=false option as described here:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

---

### Post by Face_Man on 2009-05-03
i am not sure where was the problem however now every thing is working grate!

well, thanks all for the help.

---

