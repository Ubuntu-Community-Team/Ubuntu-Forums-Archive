---
title: "Pin apps in vmware vm to unity launcher"
date: 2013-10-29
forum: Virtualisation
---

### Post by JaySeeJC on 2013-10-29
Just wondering if it's possible. I know vmware has a command line interface to make apps run in a vm. I'm wondering if it's possible to get said app to correspond with a launcher in unity. That way i could just leave the vm in vmware's unity mode. Is this possible? How would i go about setting this up for different apps in the vm?

---

### Post by warp99 on 2013-10-31
You could make a *.desktop file with the command, then place the icon in the Unity launcher. Desktop files are located in /usr/share/applications. Here's one I made to launch XP in VMPlayer.

```
:/$ cat /usr/share/applications/vmware-player-xp.desktop 

[Desktop Entry]
Encoding=UTF-8
Name=Windows XP
Comment=Run a virtual machine
Exec=/usr/bin/vmplayer /share/vmware/Windows\\ XP\\ Professional/Windows\\ XP\\ Professional.vmx
Terminal=false
Type=Application
Icon=vmware-player
StartupNotify=true
Categories=System;
MimeType=application/x-vmware-vm;

```

Use this or one of the other *.desktop files in /usr/share/applications as a template for your *.desktop file. If you want the launcher available only to you save the file in ~./local/share/applications. If you want the launcher available for all users save the file to /usr/share/applications. Here's some more information on the command string needed:

[http://everydaylht.com/howtos/desktop/launch-virtual-apps-directly-from-your-linux-desktop/](http://everydaylht.com/howtos/desktop/launch-virtual-apps-directly-from-your-linux-desktop/)

---

