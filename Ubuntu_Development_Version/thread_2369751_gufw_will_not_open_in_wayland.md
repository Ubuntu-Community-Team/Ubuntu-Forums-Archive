---
title: "gufw will not open in wayland"
date: 2017-08-26
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-08-26
gufw will not open in wayland.

[https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1713238](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1713238)

---

### Post by dino99 on 2017-08-26
i can open it from gnome-system-settings, and set my prefs as expected (but i always insert the xhost script into a terminal when opening the session)

---

### Post by ventrical on 2017-08-26
> **dino99 said:**
> i can open it from gnome-system-settings, and set my prefs as expected (but i always insert the xhost script into a terminal when opening the session)

Well.. whoever meetooed the bug .. thanks .. because eventually wayland sessions are going to have to have these programs working (lest they have other user_friendly firewalls?)

Regards..

---

### Post by rrnbtter on 2017-08-26
Greetings,
I didn't have it installed. So I first ran the xhost script, then apt install gufw. I opens for me from a terminal "gufw" (no sudo needed).
Running gnome on wayland.

---

### Post by ventrical on 2017-08-26
> **rrnbtter said:**
> Greetings,
I didn't have it installed. So I first ran the xhost script...

That's the fly in the ointment we hope to have fixed or incorporated, so that we don not have to run this script, to open and close each time in terminal, come release day.

Regards..

---

### Post by rrnbtter on 2017-08-26
Greetings, 
They (the applications) will have to be ported to Wayland or an alternative compatible application will have to be used.  To use a xhost script to allow xwayland to call up xorg server to run an x-application kind of defies the change to Wayland. My opinion.

---

### Post by ventrical on 2017-08-26
> **rrnbtter said:**
> Greetings, 
They (the applications) will have to be ported to Wayland or an alternative compatible application will have to be used.  To use a xhost script to allow xwayland to call up xorg server to run an x-application kind of defies the change to Wayland. My opinion.

  The problem is that new users and current end_users will just safely assume that regular favorite ubuntu apps will run on wayland, hence the disapp-oinment;) , but I think end_users will eventually  get the learning curve. So there is gnome-shell for legacy apps. The best of both worlds. I mean I do not think it is that big a job to build  a bridge here. (IMO), otherwise gnome with wayland will appear to be exclusive and that makes it kind of jumpy.


Regards..

---

### Post by Chanath on 2017-08-26
> **ventrical said:**
> The problem is that new users and current end_users will just safely assume that regular favorite ubuntu apps will run on wayland, hence the disappointment;) Regards..

Most users don't care, whether Ubuntu runs on X or Wayland, or even know about that. All they know is Ubuntu works, and they take it for granted that all usual apps work in Ubuntu. If apps won't work, users would leave. Just because Wayland is out there, doesn't mean all app developers would want or have enough time to port them to Wayland.

---

### Post by mc4man on 2017-08-26
Well on a fresh install currently users would get ubuntu-xorg so every thing would work.
(- while the default session (ubuntu) is wayland,  on fresh install it will actually be xorg

---

### Post by ventrical on 2017-08-26
I can run ;

```

  pkexec ufw enable

```
in wayland

---

### Post by Frogs Hair on 2017-08-26
I made a startup applications script that works with synaptic and gufw , but not bleachbit.  It's a temporary workaround, sorry if posted already.


```
#!/bin/bash
sleep 10 && xhost +si:localuser:root

```

---

### Post by dino99 on 2017-08-27
a temp mod proposed:

cat <<EOF | sudo tee /etc/xdg/autostart/xhost.desktop
[Desktop Entry]
Name=xhost
Comment=Fix graphical root applications
Exec="xhost +si:localuser:root"
Terminal=false
Type=Application
EOF

---

### Post by ventrical on 2017-08-27
> **dino99 said:**
> a temp mod proposed:

cat <<EOF | sudo tee /etc/xdg/autostart/xhost.desktop
[Desktop Entry]
Name=xhost
Comment=Fix graphical root applications
Exec="xhost +si:localuser:root"
Terminal=false
Type=Application
EOF

Thanks dino.

They now have the bug marked *CRITICAL*. I hope it gets the required attention before release because I think it is paramount in these times that we have a graphical firewall app working in ubuntu (wayland) during the 18.04 cycle because it's wayland that we will really be testing as it is proposed to be default DE.

Regards..

---

### Post by dino99 on 2017-08-27
i remember some months back, devs were doing the policykit transition to pkexec; now they need do reverse the previous job for wayland   :lolflag:

---

