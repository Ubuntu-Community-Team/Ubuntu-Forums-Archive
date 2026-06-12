---
title: "Spectacle opening Dolphin as root"
date: 2024-01-13
forum: Ubuntu/Debian BASED
---

### Post by tuxedo24 on 2024-01-13
[COLOR=#000000][FONT=Verdana]   Hi I am new here, but not new to Linux, been using various distros for 15 years. Now I am using Tuxedo OS, with the KDE plasma desktop.

When I hit Print Screen it brings up Spectacle for a screen shot. When I go to look at the image from the dialog, it opens Dolphin as root. I only installed this system a couple of days ago. Not sure why its happening? It should open Dolphin as non root.

When I use to cli to check who has sudo privilege I get:
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]```
[COLOR=#000000]bob@bob-tobefilledbyoem:~$ getent group sudo
[/COLOR]sudo:x:27:bob
```

[COLOR=#000000][FONT=Verdana]I just tried to open the Spectacle Icon in the KDE folder, and it opens Dolphin as non root, but opening it from print screen is root. What gives?

I am thinking the keyboard has some sort of root privilege? This never happened in KDE Neon, Kubuntu, Open Suse, Linux Mint Plasma?[/FONT][/COLOR]

---

### Post by tuxedo24 on 2024-01-13
[COLOR=#000000][FONT=Verdana]Here is some inputs in my bash history. Not all of them went through, but could they cause this?[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Verdana]
[COLOR=#0000BB]setfacl [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]m u[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]libvirt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]qemu[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]x
vim [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]scripts[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]virt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]manager[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]sh
export DISPLAY[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#DD0000]':0.0'
[/COLOR][COLOR=#0000BB]cp [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]v [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]home[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]bob[/COLOR][COLOR=#007700]/.[/COLOR][COLOR=#0000BB]Xauthority [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]root[/COLOR][COLOR=#007700]/.[/COLOR][COLOR=#0000BB]Xauthority
virt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]manager
su [/COLOR][COLOR=#007700]- [/COLOR][COLOR=#0000BB]root
[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]scripts[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]virt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]manager[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]sh
sudo chown [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]hR bob [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]media[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]bob[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]VBox[/COLOR][COLOR=#007700]*/
[/COLOR][COLOR=#0000BB]sudo vi [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]etc[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]libvirt[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]qemu[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]conf
sudo systemctl restart libvirtd
chown root[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]kvm [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]dev[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]kvm
sudo chown root[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]kvm [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]dev[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]kvm
sudo systemctl restart libvirtd [/COLOR]
[/FONT][/COLOR]
```

---

### Post by ajgreeny on 2024-01-13
*Thread moved to **Ubuntu/Debian BASED**.* which is more appropriate and a better fit as this is not about Ubuntu.

---

### Post by tuxedo24 on 2024-01-13
Now I find Krunner Baloo is opening Dolphin as root too?

---

### Post by tuxedo24 on 2024-01-13
Looking at this, I got a plug in to open as root. I should have got root actions instead. Now how do I undo this?

 [https://www.reddit.com/r/kde/comments/5l35db/how_can_you_enable_root_access_in_dolphin/](https://www.reddit.com/r/kde/comments/5l35db/how_can_you_enable_root_access_in_dolphin/)

---

### Post by tuxedo24 on 2024-01-13
[COLOR=#000000][FONT=Verdana]I unistalled dolphin, reboot, reinstall, now all apps open in the non root dolphin.[/FONT][/COLOR]

---

