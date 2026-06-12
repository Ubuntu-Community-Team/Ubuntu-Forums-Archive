---
title: "How to configure polkit-gnome or PolKit"
date: 2010-08-11
forum: Security
---

### Post by deimusmeister on 2010-08-11
Hello, 

I want to configure the polkit-gnome or polkit so that it does not require root password every time. I want to set it somewhere in configuration files and read from there if execution of application requires root's permissions.
How to configure ? 

Regards,
Levon

---

### Post by bjorgein on 2010-08-11
I too would like to know, I am having problems getting polkit to authenticate me for some reason.

---

### Post by deimusmeister on 2010-08-11
Huh, going to answer to my own question !
polkit's policy toward different applications can be found in /usr/share/ polkit-1/actions/"DBUS interface of app"

Marking the question as closed !

---

### Post by deimusmeister on 2010-08-13
more info can be found in my blog 
[http://levonp.blogspot.com/](http://levonp.blogspot.com/)

---

