---
title: "VirtualBox will not run in Karmic"
date: 2009-11-02
forum: Virtualisation
---

### Post by lostkrs on 2009-11-02
[SIZE=4]I just upgraded to Karmic 9.10 today. when my virtualbox would not run, I uninstalled it , went to suns site and downloaded "virtualbox 3.0.10 for Linux host, not sure if that was a mistake for me to do. When I go to open vitrualbox a box pops up with the heading "VirtualBox - Error In SUPR3HardenedMa" with the body of the box displaying "Effective UID is not root (euid=1000 egid=1000 uid=1000) (rc=-10) . Under that in smaller text is says "It may help to reinstall VirtualBox."  I am clueless to what is meant here. I can fire up the terminal box and enter commands but I do not have an understanding of the language used by those of you that progr**am. Your help is appreciated much**[/SIZE]

---

### Post by skatinjj on 2009-11-02
Did you add yourself to the vboxusers group?

---

### Post by lostkrs on 2009-11-02
is that on this site?

---

### Post by rliegh on 2009-11-02
> **lostkrs said:**
> is that on this site?

open a command prompt and type the following:
> sudo gedit /etc/group
enter your user password when asked.
look for an entry that looks like:
> vboxusers:x:122:
and change it to > vboxusers:x:122:USERNAMEreplace USERNAME with whatever user name you use on your computer.
log out
log back in, and you should have the permissions that you need.

---

### Post by lostkrs on 2009-11-03
[SIZE=4]I opened it up and what I found already there was this 
quote:
vboxusers:x:125:kent,root,chris

I'm guessing I should leave this alone? 
[/SIZE]

---

### Post by Suiname on 2009-11-03
I have a user running VirtualBox on 9.10 64-bit, I actually did an upgrade using the package you downloaded from the VirtualBox website, so it does work.  Perhaps you should follow their advice and try reinstalling VirtualBox (you can reinstall the package with the .deb file).  When I initially installed VirtualBox, I also had to compile the kernel before it would run the first time, but that doesn't look like it will address the error code you are getting.

---

