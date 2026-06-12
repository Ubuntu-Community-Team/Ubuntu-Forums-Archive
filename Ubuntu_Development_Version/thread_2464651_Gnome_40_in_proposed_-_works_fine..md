---
title: "Gnome 40 in proposed - works fine."
date: 2021-07-08
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-07-08
Installed Gnome 40 from proposed. Works fine. Same dock on left, same icons on desktop, you see the difference only pressing the super key!
[https://www.omgubuntu.co.uk/2021/07/gnome-40-in-ubuntu-21-10-first-look](https://www.omgubuntu.co.uk/2021/07/gnome-40-in-ubuntu-21-10-first-look)

---

### Post by Hewjr100 on 2021-07-11
If you delete extensions, you will get Gnome 40 dock on bottom.

Henry

---

### Post by xyz-t on 2021-07-11
Not bad at all. Meets the excitement of trying something new. +1

Dock stayed at the bottom intact, without deleting anything. Tweaks won't open, not even with su. Extensions works fine, but hide activities gives the following error: The extension is incompatible with the current GNOME version.

We must get the content of Proposed first, reboot in the new Kernel (5.13) and get gnome 40 after.
```

sudo apt update && sudo apt dist-upgrade
The following packages were automatically installed and are no longer required:
  libasn1-8-heimdal libgssapi3-heimdal libhcrypto4-heimdal
  libheimbase1-heimdal libheimntlm0-heimdal libhx509-5-heimdal
  libkrb5-26-heimdal libldap-2.4-2 libroken18-heimdal libwind0-heimdal
Use 'sudo apt autoremove' to remove them.
...

The following packages will be upgraded:
  evolution-data-server fwupd gir1.2-gweather-3.0 gnome-settings-daemon
  gnome-settings-daemon-common gnome-shell gnome-shell-common
  gnome-shell-extension-prefs gnome-shell-extension-ubuntu-dock
  libcamel-1.2-62 libebackend-1.2-10 libebook-1.2-20 libebook-contacts-1.2-3
  libecal-2.0-1 libedata-book-1.2-26 libedata-cal-2.0-1 libedataserver-1.2-26
  libedataserverui-1.2-3 libgweather-3-16 yaru-theme-gnome-shell
20 upgraded, 5 newly installed, 4 to remove and 0 not upgraded.
...

Setting up gnome-shell (40.2-1ubuntu1) ...
Setting up gnome-shell-extension-prefs (40.2-1ubuntu1) ...
Setting up gnome-shell-extension-ubuntu-dock (70~ubuntu1) ...
reboot
```


```
apt policy gnome-shell
gnome-shell:
  Installed: 40.2-1ubuntu1
  Candidate: 40.2-1ubuntu1
uname -r
5.13.0-11-generic
```

---

### Post by zebra2 on 2021-07-11
I'm using 21.10 and Gnome 40.2 on my three systems. Just upgraded my wife from Focal today.  Everything works ok except some fonts need improvement. Might interest someone to know that the adwaita and libhandy routines for gtk are not yet complete. Hence there should be considerable changes to the appearance of Gnome 40 yet to be implemented. Also, since adwaita and libhandy are supported independent of GTK, the mere presence of GTK4 doesn't imply that those Gnome libraries are mature. 
I have been using Gnome 40 since the PPA turned up and was satisfied with it even in that undeveloped state.  The additions in Proposed fixed a lot of issues. There should be more to come.

---

### Post by VMC on 2021-07-13
Anyone get gnome-tweaks to work on gnome 40?  Mine crashes. There's one bright spot. My doc now works perfectly under Wayland. On gnome 38, it took 30 seconds to populate any icons to the doc.

---

### Post by corradoventu on 2021-07-14
I have Ubuntu 21.04 with Gnome 40 on 2 different PC and gnome-tweaks works fine.
Gnome 40 has been installed from proposed on a fresh installation of Ubuntu 21.10.

---

### Post by VMC on 2021-07-14
doesn't work on my 21.10 proposed:
```
$ gnome-tweaks 
Traceback (most recent call last): 
  File "/usr/lib/python3/dist-packages/gtweak/app.py", line 30, in do_activate 
    self.win = Window(self, model) 
  File "/usr/lib/python3/dist-packages/gtweak/tweakview.py", line 58, in __init__ 
    self._model.load_tweaks(self) 
  File "/usr/lib/python3/dist-packages/gtweak/tweakmodel.py", line 107, in load_tweaks 
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0) 
  File "/usr/lib/python3/dist-packages/gtweak/tweaks/tweak_group_font.py", line 104, in <module> 
    FontXSettingsTweak(), 
  File "/usr/lib/python3/dist-packages/gtweak/tweaks/tweak_group_font.py", line 32, in __init__ 
    self.btn_full.set_active(self.settings["hinting"] == "full") 
  File "/usr/lib/python3/dist-packages/gi/overrides/Gio.py", line 259, in __getitem__ 
    raise KeyError('unknown key: %r' % (key,)) 
KeyError: "unknown key: 'hinting'" 
```
Not sure I want to create a report this being on proposed.

---

### Post by VMC on 2021-07-14
Today, I did clean install:


[LIST=1]
[*]Proposed,
[*]"sudo apt update && sudo apt dist-upgrade",
[*]"sudo apt install gnome-tweaks".
[/LIST]
 
Now gnome-tweaks works.

---

