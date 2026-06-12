---
title: "Virtualbox 5.1 systemd startup"
date: 2017-07-13
forum: Virtualisation
---

### Post by Tim_Stephens on 2017-07-13
Hi, I have a problem starting a VM on boot using systemd, I searched the forums and followed this thread - [https://ubuntuforums.org/showthread.php?t=2326419](https://ubuntuforums.org/showthread.php?t=2326419).

This is my service file.
```

# vbox.service[Unit]
Description=VBox Headless Virtual Machine Service
## Optional, but note this:
# Requires=systemd-modules-load.service
# After=systemd-modules-load.service






[Service]
## This was the original setting, which only worked for the OP on CLI:
#Type=simple
## The following chaange let it start at boot:
Type=idle
User=tim
Group=vboxusers
ExecStart=/usr/bin/VBoxHeadless --startvm "3cxpbx"
## next could also be turned off as savestate
ExecStop=/usr/bin/VBoxManage controlvm "3cxpbx" poweroff




[Install]
WantedBy=multi-user.target

```

This is the output of sudo systemctl status vbox3cx

```

&#9679; vbox3cx.service - VBox Headless Virtual Machine Service
   Loaded: loaded (/etc/systemd/system/vbox3cx.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2017-07-13 09:40:24 BST; 8min ago
 Main PID: 919 (VBoxHeadless)
   CGroup: /system.slice/vbox3cx.service
           &#9500;&#9472; 919 /usr/lib/virtualbox/VBoxHeadless --startvm 3cxpbx
           &#9500;&#9472;1144 /usr/lib/virtualbox/VBoxXPCOMIPCD
           &#9500;&#9472;1166 /usr/lib/virtualbox/VBoxSVC --auto-shutdown
           &#9492;&#9472;1736 /usr/bin/pulseaudio --start --log-target=syslog


Jul 13 09:40:24 tim-Ubuntu-Server systemd[1]: Started VBox Headless Virtual Machine Service.
Jul 13 09:41:06 tim-Ubuntu-Server pulseaudio[1736]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-da
Jul 13 09:41:06 tim-Ubuntu-Server pulseaudio[1736]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon with
Jul 13 09:41:30 tim-Ubuntu-Server pulseaudio[1736]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible 
~
~
~
~
~
~
~
~
~
lines 1-14/14 




```

It says active but it hasn't launched! If I restart the service then it launches correctly.

```

&#9679; vbox3cx.service - VBox Headless Virtual Machine Service
   Loaded: loaded (/etc/systemd/system/vbox3cx.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2017-07-13 10:09:14 BST; 2min 13s ago
  Process: 5863 ExecStop=/usr/bin/VBoxManage controlvm 3cxpbx poweroff (code=exited, status=0/SUCCESS)
 Main PID: 5884 (VBoxHeadless)
   CGroup: /system.slice/vbox3cx.service
           &#9500;&#9472;5884 /usr/lib/virtualbox/VBoxHeadless --startvm 3cxpbx
           &#9500;&#9472;5898 /usr/lib/virtualbox/VBoxXPCOMIPCD
           &#9500;&#9472;5903 /usr/lib/virtualbox/VBoxSVC --auto-shutdown
           &#9492;&#9472;5940 /usr/bin/pulseaudio --start --log-target=syslog


Jul 13 10:09:14 tim-Ubuntu-Server systemd[1]: Started VBox Headless Virtual Machine Service.
Jul 13 10:09:15 tim-Ubuntu-Server pulseaudio[5940]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-da
Jul 13 10:09:15 tim-Ubuntu-Server pulseaudio[5940]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon with
Jul 13 10:09:40 tim-Ubuntu-Server pulseaudio[5940]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible 
~
~
~



```

I don't understand why it works when I restart as using same service file, any help would be much appreciated.

Thanks in advance,
Cheers,
Tim

---

