---
title: "Lubuntu Software Center does not start after update"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mjhatten on 2012-03-20
Did update of Lubuntu 12.04.  Lubuntu Software Center no longer starts.  Opening in Terminal gets:

michael@michael-AOD255:~$ sudo lubuntu-software-center
Opening config file
Opening config file
Traceback (most recent call last):
  File "/usr/bin/lubuntu-software-center", line 35, in <module>
    mainfunc()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 679, in lscmain
    app = LscControl()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 49, in __init__
    self.ui = UI.Gui(self.on_selected_category, threadingops.get_categories())
  File "/usr/lib/python2.7/dist-packages/LSC/UI.py", line 71, in __init__
    self.pages = pages.Pages(categories_func)
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/pages.py", line 44, in __init__
    self.appsinfo = appsinfo.InfoBox()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 39, in __init__
    self.screendesc = ScreenDesc()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 97, in __init__
    self.details = Details()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 148, in __init__
    self.arrow = Gtk.Arrow()
TypeError: __init__() takes exactly 3 arguments (1 given)

Tried to deinstall and reinstall.  Got this during reinstall:

michael@michael-AOD255:~$ sudo apt-get install lubuntu-software-center+
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  lubuntu-software-center
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/70.3 kB of archives.
After this operation, 618 kB of additional disk space will be used.
Selecting previously unselected package lubuntu-software-center.
(Reading database ... 137425 files and directories currently installed.)
Unpacking lubuntu-software-center (from .../lubuntu-software-center_0.0.4-0ubuntu3_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up lubuntu-software-center (0.0.4-0ubuntu3) ...
Creating package database in /var/cache/lsc_packages.db
Reading package lists... Done
Building dependency tree        
Reading state information... Done
treb: package not found
teamspeak-client: package not found
koffice: package not found
zsnes: package not found
pptview: package not found
lekhonee-kde: package not found
eagle: package not found
dia-gnome-gnome-gnome-gnome-gnome-gnome-gnome-gnome-gnome-gnome-gnome: package not found
syncropated: package not found
gatos: package not found
ggcov: package not found
lekhonee-gnome: package not found
ardour-i686: package not found
gatos: package not found
facturlinex2: package not found
freemix: package not found
startupmanager: package not found
Creating table utils
Creating table universalaccess
Creating table audiovideo
Creating table games
Creating table graphic
Creating table network
Creating table education
Creating table scienze
Creating table system
Creating table devel
Creating table tweaks
Creating table fonts
Creating table office
Creating table packages
libgstfarsight0.10-0: not found
Done

I don't know what it should look like.  What next?

---

### Post by raja.genupula on 2012-03-20
what you are getting after doing this
```
sudo apt-get install -f
```

---

### Post by mjhatten on 2012-03-20
michael@michael-AOD255:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael-AOD255:~$

---

### Post by raja.genupula on 2012-03-20
looking like --

```
sudo apt-get install --reinstall lubuntu-software-center
```

---

### Post by mjhatten on 2012-03-20
no joy:

michael@michael-AOD255:~$ sudo apt-get install --reinstall lubuntu-software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/70.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 137504 files and directories currently installed.)
Preparing to replace lubuntu-software-center 0.0.4-0ubuntu3 (using .../lubuntu-software-center_0.0.4-0ubuntu3_all.deb) ...
Unpacking replacement lubuntu-software-center ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up lubuntu-software-center (0.0.4-0ubuntu3) ...
Creating package database in /var/cache/lsc_packages.db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
treb: package not found
teamspeak-client: package not found
koffice: package not found
zsnes: package not found
pptview: package not found
lekhonee-kde: package not found
eagle: package not found
dia-gnome-gnome-gnome-gnome-gnome-gnome-gnome-gnome-gnome-gnome-gnome: package not found
syncropated: package not found
gatos: package not found
ggcov: package not found
lekhonee-gnome: package not found
ardour-i686: package not found
gatos: package not found
facturlinex2: package not found
freemix: package not found
startupmanager: package not found
Creating table utils
Creating table universalaccess
Creating table audiovideo
Creating table games
Creating table graphic
Creating table network
Creating table education
Creating table scienze
Creating table system
Creating table devel
Creating table tweaks
Creating table fonts
Creating table office
Creating table packages
libgstfarsight0.10-0: not found
Done
michael@michael-AOD255:~$ lubuntu-software-center
Opening config file
Opening config file
Traceback (most recent call last):
  File "/usr/bin/lubuntu-software-center", line 35, in <module>
    mainfunc()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 679, in lscmain
    app = LscControl()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 49, in __init__
    self.ui = UI.Gui(self.on_selected_category, threadingops.get_categories())
  File "/usr/lib/python2.7/dist-packages/LSC/UI.py", line 71, in __init__
    self.pages = pages.Pages(categories_func)
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/pages.py", line 44, in __init__
    self.appsinfo = appsinfo.InfoBox()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 39, in __init__
    self.screendesc = ScreenDesc()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 97, in __init__
    self.details = Details()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 148, in __init__
    self.arrow = Gtk.Arrow()
TypeError: __init__() takes exactly 3 arguments (1 given)
michael@michael-AOD255:~$

---

### Post by MG&amp;TL on 2012-03-20
Hi, I just fixed (I hope) this particular bug-LSC is still under heavy development, but thanks for testing! :)

You can see the fix (if you're interested) at [https://code.launchpad.net/~lubuntu-software-center-team/lubuntu-software-center/lubuntu-software-center-trunk]("https://code.launchpad.net/%7Elubuntu-software-center-team/lubuntu-software-center/lubuntu-software-center-trunk")

The PPA should build within the next 24 hours or so (it's a daily build).

Thanks for your patience.

---

