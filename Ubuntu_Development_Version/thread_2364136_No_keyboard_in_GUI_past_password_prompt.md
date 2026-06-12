---
title: "No keyboard in GUI past password prompt"
date: 2017-06-19
forum: Ubuntu Development Version
---

### Post by dbarron on 2017-06-19
I had a working 17.04 installation, and decided to take it to 17.10 by dist-update a few days ago.  I found that after i did, I had no keyboard interaction after the login password prompt.  I tried using both the gnome login and Wayland, both displayed the same symptom.
Can anyone advise on what I might check or try to help solve the problem?

---

### Post by dino99 on 2017-06-19
I also get such a trouble, but it is seen randomly when i want to select a particular line from the grub menu: sometimes the keyboard (usb (1) to usb3 port) is activated (as expected), sometimes not. If it was not activated, then when the selected os boot, the keyboard is always active. Maybe a transitional script issue that randomly disturb the process. (using lightdm and gnome-shell session)

---

### Post by dbarron on 2017-06-19
I poked around in console mode and saw some permission denies related to console-indicator.  But as I understand that is the console terminal devices...not the X console.  However I also saw an error opening xconsole.
Still stumped.

---

### Post by dbarron on 2017-10-17
Okay I just upgraded again and this is still an issue does anybody have any ideas?

---

### Post by dino99 on 2017-10-17
I have not got that issue recently on my system; maybe run gtkorphan & bleachbit (as root) to clean the system; then reboot and glance at journalctl for warning/error

---

### Post by dbarron on 2017-10-17
Thanks for your reply.
But how would I launch gtkorphan without a keyboard?  When I mouse-navigated using the file explorer, it opened as a text file (since it's a script I assume).  Didn't see any way to launch it (but maybe I missed it).
As a note, I will not be able to access logs till I reboot, since ALL input from keyboard (including access to virtual terminals) is now ineffective.  I can access a VT before I login, but I can't switch afterwards.

---

### Post by jimmy-frydkaer on 2017-10-17
I got the same problem as OP and the only workaround I found was to make the system hipernate from a login screen - When you have loged in and you have no keeboard log out of the system, then put the system to sleep and restart the session from sleep/power on and you'll get the login screen up again. Login - problem solved. It is the only way I know will bring back the keyboard.

---

### Post by dbarron on 2017-10-17
Jimmy, you are correct, exactly the same behavior.  Is this a kernel problem perhaps then?
I have an older logitech USB keyboard, what do you have (though I wouldn't think it would be device specific..just trying to provide info/find info)?

---

### Post by jimmy-frydkaer on 2017-10-18
I have a Logitech G15 keyboard but i doubt that it is the reason. On my laptop, Lenovo <ideapad 100> I do not have this problem, strange. If it was a device specific problem I would have a hard time explaining why the keboard works after the workaround. I guess it's a kernel problem but I'm not sure about that either. Maybe the problem lies with the in a keyboard script some how.

---

### Post by dbarron on 2017-10-18
Mine is a G15 also...I think we have something in common.  I have another keyboard, I'll try it and if the issue goes away, I'll file a bug report.

---

### Post by dbarron on 2017-10-18
Switched to a naga keyboard, no issue.  Confirmed.

---

