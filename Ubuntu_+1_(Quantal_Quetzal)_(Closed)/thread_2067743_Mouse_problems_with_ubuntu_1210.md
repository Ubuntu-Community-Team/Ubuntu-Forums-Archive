---
title: "Mouse problems with ubuntu 1210"
date: 2012-10-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Billxyzzy on 2012-10-07
I have a problem with 1210 ubuntu.  I have been updating on a regular basis with no problems.  However about 2 days ago after the update I lost all control of the mouse.  It is not a hardware problem as when I switch to Precise or to xubuntu 1210 there is no problem with the mouse (both at the latest update).   Anyone seen this and/have a workaround?   I can't even file bug reports as I can't log into launchpad.

---

### Post by pqwoerituytrueiwoq on 2012-10-07
try unpluging the mouse and plugging it back in (trigger hotplug detect)
you can control the mouse with xdotool
you may be able to enable mouse keys

---

### Post by Billxyzzy on 2012-10-07
Unfortunitly xdotool does no good.
I can't open a terminal with a window open.
I will try the hotplug idea next.

---

### Post by funicorn on 2012-10-07
```
xinput list
```See if your mouse is in the list. If not the kernel doesn't recognize your mouse. Then try modprobe it with
```
modprobe psmouse
```However were the mouse not recognized it would be complicated . If it's there
```
 xinput list <id>
```See its basic info. Then
```
 xinput get-button-map <id>
```See its button map
```
 xev
```Click mouse buttons and roll mouse wheels, see the outputs in the terminal and remember the button sequence. Then use for example
```
xinput set-button-map N1 N2 N3 N4 N5
```to set the button map.

Finally if you are using nvidia driver, use
```
sudo cp /etc/X11/xorg.conf{,.backup} && sudo nvidia-xconfig
```to generate a new X configuration, then restart Xserver.

---

### Post by Billxyzzy on 2012-10-07
Thanks for the suggestions.  Got it resolved.
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
in that order seemed to shake something loose.
Somehow the latest kernel update did not take.
Now all seems to be well.

---

