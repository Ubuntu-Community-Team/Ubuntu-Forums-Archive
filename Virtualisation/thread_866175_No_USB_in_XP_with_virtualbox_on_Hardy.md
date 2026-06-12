---
title: "No USB in XP with virtualbox on Hardy"
date: 2008-07-21
forum: Virtualisation
---

### Post by L.B. on 2008-07-21
I followed tutorial and got virtualbox installed on Hardy.I did set up for usb. I can see usb's in the VM menu and add by name or description,but when I start xp the usb's are grey in drop box. I found that someone said to add line to etc/fstab, but don't know how to find etc/fstab, or add this line, # USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 sorry for being the dumb one but I just switched from windows and don't have much clue.plz. help.           vb 1.5.6

---

### Post by HotShotDJ on 2008-07-21
Before going any further... exactly WHICH tutorial did you follow?  In other words, how did you install VirtualBox -- are you using the OSE or the PUEL version?

---

### Post by L.B. on 2008-07-21
I used  How To: Install VirtualBox on Ubuntu 8.04LTS (Hardy Heron) [Tutorial] from ubuntu forums.

---

### Post by L.B. on 2008-07-21
It's not OSE, I think it is PUEL

---

### Post by flytripper on 2008-07-21
have you relogged yet?

---

### Post by L.B. on 2008-07-21
yes I did reboot

---

### Post by HotShotDJ on 2008-07-21
> **L.B. said:**
> It's not OSE, I think it is PUELYes... if you followed that thread, then you have the PUEL. That thread uses an out-of-date version of VirtualBox.  The latest version (which I have installed) is 1.6.2.  But lets not worry about that right now.

In order to edit your fstab file.... open a terminal (Applications --> Accessories --> Terminal) and type:```
gksudo gedit /etc/fstab
```

---

### Post by cszikszoy on 2008-07-21
Did you add your user account to the 'usbfs' group?  After you do that you have to logout and log back in again.

If you don't know how to do this, go to system > administration > users and groups.

unlock and click on manage groups.  Scroll down to usbfs and double click.  It will bring up a box where you can click on your user name to add yourself to that group.

Try that and see what happens.

**edit**

Sorry, I didn't see that you don't know how to edit fstab.  Luckily, while I was posting, someone else told you how to.  Read what he said above, do that and then do what I said and everything will be fine.

---

### Post by L.B. on 2008-07-21
THANK YOU HOTSHOTDJ!!!!!!!!!!  I owe you a cup of joe!!!!!!!!!

---

