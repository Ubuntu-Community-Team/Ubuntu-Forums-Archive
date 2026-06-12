---
title: "Firestarter not working correctly?"
date: 2012-05-28
forum: Security
---

### Post by bbno3 on 2012-05-28
[ATTACH]218842[/ATTACH]

My firestarter gets the error in the box from the picture i have uploaded to the attachments.

I have tried other firewalls and nothing else worked. Any ideas?

---

### Post by claracc on 2012-05-28
I would not use firestarter as it is an old project and I think it is not actively mantained.

Insted you use ufw firewall, the default one in ubuntu and its gui gufw to set the rules

---

### Post by bbno3 on 2012-05-28
How do i access UFW? I dont seem to have it.

---

### Post by ajgreeny on 2012-05-28
Unless you are running a very old and no longer supported version of ubuntu, ufw is included in the default installation but it is a command-line application.

In a terminal run ```
man ufw
``` which will show the manual for ufw; if that shows OK then ufw is installed.  I think you may need to install gufw for the simple GUI, as I don't think that is installed by default.

---

### Post by Ms. Daisy on 2012-05-28
> **ajgreeny said:**
> Unless you are running a very old and no longer supported version of ubuntu, ufw is included in the default installation but it is a command-line application.

In a terminal run ```
man ufw
``` which will show the manual for ufw; if that shows OK then ufw is installed.  I think you may need to install gufw for the simple GUI, as I don't think that is installed by default.
+1

Also, make sure you completely remove firestarter, IIRC it will conflict with ufw.

---

### Post by claracc on 2012-05-29
ufw is installed in ubuntu by default.

To install its gui, you write in a xterm:

sudo apt-get install gufw

you enter your root password and it is all.

Then you can set the rules to allow or not allow programs or TCP addreses with the gui app. gufw

---

