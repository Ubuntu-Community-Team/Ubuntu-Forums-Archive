---
title: "is there a known problem with conky manager in trusty?"
date: 2014-03-16
forum: Ubuntu Development Version
---

### Post by ortermagic on 2014-03-16
i have been unable to install conky manager using tee jees ppa in trusty, has anyone had this problem?

---

### Post by ortermagic on 2014-03-16
I had to revert to the saucy ppa, now it works I suppose the package is'nt ready for trusty yet

---

### Post by Cavsfan on 2014-03-16
No problems here. Any 1.9 version will work. Conky version 1.8.1 no bueno.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy conky-all
conky-all:
  Installed: 1.9.0-4
  Candidate: 1.9.0-4
  Version table:
 *** 1.9.0-4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by ortermagic on 2014-03-16
Hi cavsfan, I'm not really very expert at this but I ran the commands you did and got the same, so we both have the same conky install
As in...```
ortermagic@ortermagic:~$ apt-cache policy conky-all
conky-all:
  Installed: 1.9.0-4
  Candidate: 1.9.0-4
  Version table:
 *** 1.9.0-4 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```

But I like Tony Georges LSD conky, which meant that I needed his fantastic ppa script, found here [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) trusty main(Source Code)
which did'nt work for me, so I assumed that tony had not yet upped to trusty yet. Have you tried this?


Infact I just discovered that teejee is working on it!     > Conky Manager v2 will be released soon for 14.04

---

### Post by grahammechanical on 2014-03-17
When I go here and click "Choose your Ubuntu version" I see that there is a PPA for Trusty (14.04). So, if it is not working then there must be something wrong.

[https://launchpad.net/~teejee2008/+archive/ppa](https://launchpad.net/~teejee2008/+archive/ppa)

What exactly is the problem? apart that is from "unable to install?" What error messages did the terminal throw out?

Regards.

---

### Post by ortermagic on 2014-03-18
Sorry Graham, I have been very busy lately, I tried to get teejees script to work and it didn't, so I went to his site  [http://www.teejeetech.in/p/conky-manager.html](http://www.teejeetech.in/p/conky-manager.html)  and had a look at the comments made by posters there, which is where I got the quote from (and the script).
I always get one or two problems when taking on transitional distros, mainly due to my ignorance and my reckless nature. Generally I tend to create conflicts within my system by the use of, or misuse of terminal commands (usually found by trawling), that I don't fully understand.
I have just reinstalled a fresh copy of trusty and I have dumped the troublesome one (last night) and it seems that I have stability in skype at last (one of my bugbears),as for conky I am working on it again later today.
Sorry I can't provide any tech detail cos I can't remember what I did, and I've wiped to reinstall.

---

### Post by ortermagic on 2014-03-18
Hi there, anyone interested, I have just completed a clean install of Trusty and found that the only way I could install conky-manager was to revert to the Saucy ppa provided by teejee.
Does anyone know where can I find the terminal log record? there must be a command for retrospective retrieval. I would like to find the evidence for the benefit of grahammechanical if possible.

---

### Post by grumblebum2 on 2014-03-20
> **ortermagic said:**
> Hi there, anyone interested, I have just completed a clean install of Trusty and found that the only way I could install conky-manager was to revert to the Saucy ppa provided by teejee.
Does anyone know where can I find the terminal log record? there must be a command for retrospective retrieval. I would like to find the evidence for the benefit of grahammechanical if possible.
 Doesn't appear to be a build for Trusty yet.
Without messing around with ppas I just downloaded the Saucy deb for my architecture and installed using gdebi.
Seems to work fine.
[https://launchpad.net/~teejee2008/+archive/ppa/+packages](https://launchpad.net/~teejee2008/+archive/ppa/+packages)

---

### Post by ortermagic on 2014-03-20
Interesting, I am using the saucy ppa which works, tho not perfectly, I am not able to get rid of the shadow frame around the app.I have tried changing the script frpm normal to override, which seems to generate garbled clock numerals and text overlay as well as eliminating the shadow.

---

### Post by grumblebum2 on 2014-03-20
> **ortermagic said:**
> Interesting, I am using the saucy ppa which works, tho not perfectly, I am not able to get rid of the shadow frame around the app.I have tried changing the script frpm normal to override, which seems to generate garbled clock numerals and text overlay as well as eliminating the shadow.
Install compizconfig-settings-manager (ccsm)...
```
sudo apt-get install compizconfig-settings-manager
```

 ccsm > effects > window decoration 
and insert in the **shadow windows **box...
```
(any) & !(class=Conky)
```

---

### Post by ortermagic on 2014-03-20
Oh dear, I just tried that and now I have lost unity altogether, anyone got a terminal command to rcover compiz? I have no dash hud

---

### Post by ortermagic on 2014-03-20
I have recovered unity using terminal but i'ts reset unity to defaults now ```
ortermagic@ortermagic:~$ dconf reset -f /org/compiz/ 
ortermagic@ortermagic:~$ unity --reset-icons &disown
[1] 3784
ortermagic@ortermagic:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2014-03-20 12:02:20 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2014-03-20 12:02:20 unity.debug.interface DebugDBusInterface.cpp:196 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
WARN  2014-03-20 12:02:20 xim.controller XIMController.cpp:103 IBus natively supported.
WARN  2014-03-20 12:02:20 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2014-03-20 12:02:20 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2014-03-20 12:02:20 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2014-03-20 12:02:20 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
ERROR 2014-03-20 12:02:21 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2014-03-20 12:02:21 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'


```
Where am i going wrong?
Oh not too bad, I still have my apps in the hud dash, just have to reload the unity panel and change icon size. Thanks for your help I guess I will have to be a bit more careful with compiz.

---

### Post by grumblebum2 on 2014-03-20
Yeah sorry about that.
I didn't test in Trusty first and it seems the window decoration plugin is no longer used
and decoration and shadows are provided by the unity plugin.
Enabling the window decoration plugin buggered up unity.

Couldn't set back to defaults.
Had to reboot and enable the unity plugin and a couple of others like move windows.

The good news is I got rid of the conky shadow  using **ccsm > unity plugin > decorations > inactive windows shadow color**
and changed the opacity to zero.
You need to also tick the **Override Theme Settings** box.

---

### Post by ortermagic on 2014-03-20
Great, grumblebum,that worked.Nice to see another uk user (judging by the time of your post) thank you!
[ATTACH=CONFIG]251317[/ATTACH]

---

