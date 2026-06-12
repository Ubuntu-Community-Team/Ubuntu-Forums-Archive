---
title: "Nvidia drivers and gnome"
date: 2015-02-10
forum: Ubuntu Development Version
---

### Post by brisch on 2015-02-10
There has not been many comments about gnome.
I have a problem that seems to be unique to nvidia drivers and gnome.
I have been using cairo-dock with several releases of Ubuntu.

With 1504  I have this problem.
I installed Cairo-dock and with it gnome.
In the login process I select Cairo-dock/gnome.

The screen comes up with no visible curser.  If I move the
mouse I can trip over a selection in cairo-dock and select it.
No matter what is done the curser is invisible.
This has been going on from the beginning of 1504 so I just revert
back to unity and all is well.
Has anyone else run into this?
If so anyone got a suggestion for a solution?
It could be my nvidia card or something related but
it is so consistant with all upgrades to 1504.

---

### Post by sammiev on 2015-02-10
Have you tried loading gnome and selecting systemd from the advance grub menu? Other wise gnome is doing the same to me and much broken.

---

### Post by brisch on 2015-02-10
Systemd did not work
Same problem
Gnome is a basket case

---

### Post by xc3RnbFO8P on 2015-02-10
This worked for me, in Terminal:
> gsettings set org.gnome.settings-daemon.plugins.cursor active false

---

### Post by brisch on 2015-02-10
gsettings set org.gnome.settings-daemon.plugins.curser active false did not work
something needs to be corrected in this command.
is this closer to what you mean?
org.gnome.settings-daemon.peripherals.input-devices
com.canonical.Unity.Devices

---

### Post by xc3RnbFO8P on 2015-02-10
check this bug:
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1387219]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1387219")

---

### Post by brisch on 2015-02-10
Sorry no fixie,  sudo apt-get install ibus-gtk not the solution for me

---

### Post by xc3RnbFO8P on 2015-02-11
For some this has never been solved.

Here is somthing I found:
> 
I had the same problem. You can fix it manually. Open System Settings > Displays. In the Displays window, you will see an Unknown monitor. Click it and disable it.
> sudo modprobe -r psmouse

sudo modprobe psmouse proto=imps

---

### Post by Cavsfan on 2015-02-11
I had the same problem with FB with compiz. I am included in that bug also.
Mc4man provided a work around: [http://ubuntuforums.org/showthread.php?t=2261278&page=2&p=13211065#post13211065](http://ubuntuforums.org/showthread.php?t=2261278&page=2&p=13211065#post13211065)

It has worked for me ever since.

---

