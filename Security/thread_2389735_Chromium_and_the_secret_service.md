---
title: "Chromium and the secret service"
date: 2018-04-20
forum: Security
---

### Post by graham70 on 2018-04-20
Gday 
I just returned to ubuntu after about 5 years installed 16.04 lts all went very well made up a user account then installed chomium. When using the user account tried to run chromium from the launcher the first time after log in takes sometime but after that all good, now it will not launch . launch in terminal and this is what i get back 
####@#####:~$ chromium
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option force_s3tc_enable overridden by environment.
Gkr-Message: secret service operation failed: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.158" (uid=1001 pid=7415 comm="/snap/chromium/274/usr/lib/chromium-browser/chromi") interface="org.freedesktop.DBus.Peer" member="Ping" error name="(unset)" requested_reply="0" destination="org.freedesktop.secrets" (uid=1001 pid=31560 comm="/usr/bin/gnome-keyring-daemon --daemonize --login ")

The stuff that worried me is "secret service operation" and "canberra-gtk-module" canberra is the capital city of Australia (if you didn't know) 
Just want to see people thoughts about this 
ps I live in Australia


Just launched as root in terminal the same error massage came up but still ran except it didn't auto log me into google .launch by program bar all good.

---

### Post by Dennis N on 2018-04-21
Check your installed software for 
libcanberra-gtk-module
libcanberra-gtk3-module
and install them if missing. That may help.

---

### Post by thenailedone on 2018-04-21
“Just because you're paranoid doesn't mean they aren't after you.” 
&#8213; Joseph Heller

---

### Post by graham70 on 2018-04-22
thanks for your advice i have checked this and have all those modules all ready and up to date. I have installed chrome from the chrome website and all is well. I will leave chromium on the computer to see what happens in a update. thanks again

---

### Post by graham70 on 2018-04-22
thenailedone thanks for messing with my fragile mind they are coming to get me :D

---

### Post by deadflowr on 2018-04-22
Most likely the issues stem from the fact it's the snap version of chromium.
Was this installed through the Ubuntu Software program?

---

