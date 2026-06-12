---
title: "Lubuntu proposed technical preview (called LX-Ultra)"
date: 2009-12-08
forum: The Cafe
---

### Post by llelectronics on 2009-12-08
Here a technical preview of a LXDE based Ubuntu (Lubuntu proposed) Desktop based on Karmic Koala. 

Software included :
Kernel 2.6.32-7 (lucid) 
PCManFM 0.5.2 (bugfixed release) 
gnome-mplayer (+ codecs) 
aqualung
xfburn (burning app)
claws-mail (mail client)
chromium-browser (build 4.0.226) (webbrowser)
people 0.2 (manage vcards)
orage (manage vcal) 
gnome-alsamixer (audiomixer app) 
OpenOffice 3.1 (fitts on cd but maybe too memory intensive, especially for 128 MB RAM users) 
WICD to manage networks
gigolo (as networkmanager and computer icon on the desktop to launch and mount drives [convenience for windows switcher] ) 


I changed some config files of openbox to support FN-Keys for some netbooks (so Volume up and down should work). Included is also a custom theme and a LXDE Menu button. 

Some new hotkeys:
CTRL+ALT+T will now launch a new Terminal window
CTRL+ALT+D will now launch a new filemanager window (SUPER + D will hide all windows and show the desktop) 

Some apps like network-manager , gnome-power-manager, xfce4-volumed that use the new notify-osd system are fine but seem to eat to much memory so I removed them for now and put in some replacements, like wicd and a volume.sh script. 
I also added those apps from the app proposel page that seem to do best in my opinion. 
See : [https://wiki.ubuntu.com/Lubuntu/Applications](https://wiki.ubuntu.com/Lubuntu/Applications)
The CDRigBy from the other features would be nice to include, but the website seems to be down. 
More on Lubuntu : [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
How to get involved: [http://blog.lxde.org/?p=562](http://blog.lxde.org/?p=562)

The obligatory screenshots:
xsplash:[[img]http://ubuntu-pics.de/thumb/33545/2009_12_08_201127_1280x800_scrot_iYt3XS.png[/img]](http://ubuntu-pics.de/bild/33545/2009_12_08_201127_1280x800_scrot_iYt3XS.png) 
desktop:[[img]http://ubuntu-pics.de/thumb/33546/2009_12_08_201146_1280x800_scrot_utIQ4J.png[/img]](http://ubuntu-pics.de/bild/33546/2009_12_08_201146_1280x800_scrot_utIQ4J.png)

Download: [http://dl.dropbox.com/u/2351433/lx-ultra-remix.iso](http://dl.dropbox.com/u/2351433/lx-ultra-remix.iso)
MD5: 29811ba871d3a4088de8f71ac1a7948b  lx-ultra-remix.iso

Note: This is only a testing version and is not intent to run on a productive machine. Virtualbox seems to have problems loading the vboxvideo driver thats not avaiable. Simply edit the xorg.conf and try to load it with the vesa driver. 

Comments and feedback are appreciated ;)

---

### Post by gilir on 2009-12-08
Some comments :
- Please propose you artwork on [https://wiki.ubuntu.com/Lubuntu/Artwork/Incoming/Lucid](https://wiki.ubuntu.com/Lubuntu/Artwork/Incoming/Lucid) . We don't have a current artwork, so if yours is complete and good, it could be include directly :)
- Please propose your configuration change for openbox as a patch, so other people can also enjoy the new hotkeys.
- Please also discuss this on the mailing, I sure not all people monitor the IRC chan and the ubuntu forums. Discussion on applications will begin shortly on the mailing list.

---

### Post by NormanFLinux on 2009-12-08
Make changes to the LXlauncher to make it more configurable with small screen devices. This is a considration as LXDE is a good match for netbooks.

---

### Post by llelectronics on 2009-12-13
New Version is online, with a new Theme (see [https://wiki.ubuntu.com/Lubuntu/Artwork/Incoming/Lucid/NewWave](https://wiki.ubuntu.com/Lubuntu/Artwork/Incoming/Lucid/NewWave) )

Some tools I added, 2 scripts to change time and date, jockey-gtk, synaptic, metacity, compiz-fusion, fusion-icon (added same Hotkey behavior in every 3 window managers).
Xfce4-Power-Manager is now used for powermanagement and xfce4-volumed for audio volume.

Notice: Some tools are included that seem not to be packaged or maintained in ubuntu repositories. So it might be not good for a official lubuntu iso. 
This ISO is just a work in progress I made for myself to improve or help the lubuntu team (and have a fast booting usb stick with nice tools that also is good for presentations and demos). Its just a tech preview not meant to be used as everyday desktop.

---

