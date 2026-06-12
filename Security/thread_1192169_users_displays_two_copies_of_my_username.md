---
title: "users displays two copies of my username"
date: 2009-06-19
forum: Security
---

### Post by Rangua on 2009-06-19
well, the title explains it all.. i type in a terminal (within gnome) users, and i get: doe doe
if i logout from gnome and login in tty1, i just get: doe.
i've also been experimenting an intermittent connection when i try to install (download) something with synaptic, now i'm trying to install it from tty1 with apt-get, let's see how that goes.
anyways, weird things are happening. here are some lines from my auth.log:
```
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.110" (uid=1000 pid=15916 comm="/usr/lib/gvfs/gvfs-hal-volume-monitor "))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.121" (uid=1000 pid=15978 comm="/usr/lib/gnome-applets/gweather-applet-2 --oaf-act"))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 2 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.11" (uid=0 pid=2989 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant"))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.109" (uid=0 pid=15918 comm="/usr/lib/libgconf2-4/gconfd-2 "))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.108" (uid=1000 pid=15659 comm="x-session-manager "))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.119" (uid=1000 pid=15896 comm="nautilus "))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.107" (uid=1000 pid=15777 comm="/usr/bin/pulseaudio --start "))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.7" (uid=0 pid=2859 comm="/usr/lib/hal/hald-addon-cpufreq "))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.106" (uid=1000 pid=15794 comm="/usr/lib/libgconf2-4/gconfd-2 "))
Jun 19 20:39:47 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.124" (uid=1000 pid=15895 comm="gnome-panel "))
Jun 19 20:40:00 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.125" (uid=1000 pid=16084 comm="/usr/lib/firefox-3.0.11/firefox "))
Jun 19 20:40:01 nirvana CRON[16091]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 19 20:40:01 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.126" (uid=0 pid=16091 comm="/USR/SBIN/CRON "))
Jun 19 20:40:01 nirvana CRON[16091]: pam_unix(cron:session): session closed for user root
Jun 19 20:40:14 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.127" (uid=1000 pid=16284 comm="gnome-screensaver "))
Jun 19 20:40:42 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.129" (uid=0 pid=16303 comm="/usr/lib/NetworkManager/nm-dhcp-client.action "))
Jun 19 20:40:44 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.130" (uid=0 pid=16305 comm="/usr/lib/NetworkManager/nm-dhcp-client.action "))
Jun 19 20:40:45 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.131" (uid=0 pid=16311 comm="/usr/lib/NetworkManager/nm-dispatcher.action "))
Jun 19 20:40:46 nirvana dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.123" (uid=1000 pid=15966 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.132" (uid=104 pid=16604 comm="/usr/lib/policykit/polkitd "))
Jun 19 20:43:47 nirvana sudo:      doe : TTY=unknown ; PWD=/home/doe ; USER=root ; COMMAND=/usr/sbin/synaptic 
```
what do you think this might be?
I've also blocked ICMP connections with firestarter, just in case (there were "serious" events, all of them using ICMP)
PD: the tty1 apt-get is experimenting the same connection issues.
Edit: using root account to install solved the problem. i've deleted my user from sudoers just in case. awaiting instructions.

---

### Post by bodhi.zazen on 2009-06-20
I think you will get your answer with the who, or simply w command.

When you log into gnome, that is tty7
when you open a teminal, that is pts/0

Open a third terminal, that is pts/1

This is what I get on my system , loged into gnome with 2 terminals open :

```
bodhi@karmic:~$ users
bodhi bodhi bodhi

bodhi@karmic:~$ w
bodhi tty7 :0 
bodhi pts/0
bodhi pts/1
```

This is all normal and I see nothing concerning in your logs either.

The first step in security is to know what is normal and what is not.

---

### Post by Bachstelze on 2009-06-20
By the way, notice the [font="monospace"]:0[/font] in the [font="monospace"]w[/font] output, which indicates that there is a X display attached to that session (0 being the display number).

---

### Post by Rangua on 2009-06-21
thanks for the advice.. i think i solved the problem, by disabling ipv6 (i'm behind a router).. so..  ](*,) 
but thanks for the w command, i had no idea it existed :D

---

