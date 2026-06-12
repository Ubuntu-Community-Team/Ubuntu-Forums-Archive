---
title: "where can I log out in unity desktop in 14.04"
date: 2013-11-22
forum: Ubuntu Development Version
---

### Post by leeper69 on 2013-11-22
Hi well if it can be broken I seem to find it.
I booted into 14.4 and where the logout was in the top bar the icon was missing, this has happend to me now a coupel times. ( but not always it seems to be a hit and miss situation )
is there anywhare I can log out, restart, or shutdown the unity desktop other than the top bar?
my only fix for now is to open the terminal and type sudo shutdown now -h which will shutdown the system.
also can anyone tell me the terminal comand to rerstart the system insted of shuting it down?

---

### Post by howefield on 2013-11-22
```
sudo reboot
```

Although...

```
killall unity-panel-service

```
worked for me in resetting the panel.

---

### Post by leeper69 on 2013-11-22
Hi and thanks for your help howefield!!!
sudo reboot works for me too my system dosent like to be shut down. ( sorry my version is 14.04 ubuntu desktop )

---

### Post by howefield on 2013-11-22
Glad you are sorted, just a small point... it is 14.04, not 14.4. 

Only saying as version numbers can be quite important :)

---

### Post by PJs Ronin on 2013-11-22
I believe this also works ```
 sudo restart lightdm
```

---

### Post by jerrylamos on 2013-11-22
> **howefield said:**
> [quote]```
killall unity-panel-service

```worked for me in resetting the panel.
Just didn't work for me.  I'm in the middle of an update to 
linux-image-3.12.0-4-generic from the -2
then I'll do a sudo reboot in a terminal window.

---

### Post by craig10x on 2013-11-22
control/alt/delete keys held down at the same time should bring up the log out window...and if you log out and back in, the icon should return to the panel....we had the same problem on 13.10 testing for a while until it got fixed...

---

### Post by mc4man on 2013-11-22
> **craig10x said:**
> control/alt/delete keys held down at the same time should bring up the log out window...and if you log out and back in, the icon should return to the panel....we had the same problem on 13.10 testing for a while until it got fixed...

Due to someones brilliant idea ctrl+alt+delete is now bound to open the sys monitor in compiz installs. If it still opens a log out screen then either one is on an older install updated or maybe gnome-flashback/compiz isn't behaving nicely in this regard.

(considering the continuing issue with disappearing indicators, mouse cursor, ect. maybe they should have left well enough alone..

---

### Post by zika on 2013-11-23
Ctrl-Alt-Backspace?

---

### Post by howefield on 2013-11-23
Indeed, Ctrl+Alt+Del opens up the system monitor in this fresh 14.04 install, although the keyboard application thinks it should offer a logout :)

Ctrl+Alt+Backspace does nothing.

---

### Post by zika on 2013-11-23
Then in must be that in recent past I've done```
[COLOR=#000000][FONT=arial]dpkg-reconfigure keyboard-configuration[/FONT]
```[FONT=arial]or similar...[/FONT][/COLOR]

---

