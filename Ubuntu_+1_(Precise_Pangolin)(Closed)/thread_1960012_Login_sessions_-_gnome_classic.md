---
title: "Login sessions - gnome classic??"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by candtalan on 2012-04-16
I have recently installed Ubuntu 12.04 beta 2 and updated, and also one or two things from Ubuntu software centre, and also medibuntu repo. I notice in the login sessions options that not only are Ubuntu and Ubuntu 2D offered, but also gnome classic.

Is this a result of my own installs somehow, or is it  intended to be a future option in the full Ubuntu 12.04 release? Anyone know?

---

### Post by cariboo on 2012-04-16
You probably installed  gnome-session-fallback in order to get gnome-classic in the session menu

---

### Post by candtalan on 2012-04-17
> **cariboo907 said:**
> You probably installed  gnome-session-fallback in order to get gnome-classic in the session menu
No I did not, at least, not knowingly. This is a new install, for testing on this machine, so I am mystified as to why the extra stuff is installed. Would medibuntu and its multimedia stuff have implications in this direction? libvidcss? w32codecs?

---

### Post by mc4man on 2012-04-17
> **candtalan said:**
> Would medibuntu and its multimedia stuff have implications in this direction? libvidcss? w32codecs?
None of those, there's likely a very short list of packages that would install gnome-session-fallback as a dep.

Software center has a history button, check & maybe see

---

### Post by kansasnoob on 2012-04-17
Post the full output of:

```
cat /var/log/apt/history.log
```

And:

```
ls /var/log/apt
```

Please use code tags by clicking on the # in this reply box before pasting the output.

---

### Post by philinux on 2012-04-17
You used to get it by installing gnome-panel. 

[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

On my system this seems to have been installed as default now. I clean installed on the 11th april.

```
 apt-cache policy gnome-panel
gnome-panel:
  Installed: 1:3.4.1-0ubuntu1
  Candidate: 1:3.4.1-0ubuntu1
```

---

### Post by jbicha on 2012-04-17
gnome-panel or gnome-session-fallback are not installed by default. If you install gnome-tweak-tool you'll currently get the Classic session too. (I think that's a bug though).

---

### Post by mc4man on 2012-04-17
> **jbicha said:**
> gnome-panel or gnome-session-fallback are not installed by default. If you install gnome-tweak-tool you'll currently get the Classic session too. (I think that's a bug though).

Well currently the tweak tool deps on gnome-shell which recommends gnome-session-fallback

So would the bug be the tweak tool shouldn't dep on GS or that installing package A which deps on package B installs the recommends of package B & the recommends of the recommends of package b

---

### Post by philinux on 2012-04-17
> **jbicha said:**
> gnome-panel or gnome-session-fallback are not installed by default. If you install **gnome-tweak-tool** you'll currently get the Classic session too. (I think that's a bug though).

That's where it must have come from then lol.

---

### Post by kansasnoob on 2012-04-17
> **jbicha said:**
> gnome-panel or gnome-session-fallback are not installed by default. If you install gnome-tweak-tool you'll currently get the Classic session too. (I think that's a bug though).

In deed, this is also why I've asked for logs :)

The apt logs will answer the question.

---

### Post by philinux on 2012-04-17
> **kansasnoob said:**
> In deed, this is also why I've asked for logs :)

The apt logs will answer the question.

Looks like tweak tool not the culprit.

```
sudo apt-get purge gnome-tweak-tool
[sudo] password for philcb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-tweak-tool*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 584 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151591 files and directories currently installed.)
Removing gnome-tweak-tool ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
philcb@philcb-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
philcb@philcb-desktop:~$ sudo apt-get purge gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-applets* gnome-panel* gnome-session-fallback*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 2,262 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151507 files and directories currently installed.)
Removing gnome-applets ...
Removing gnome-session-fallback ...
Removing gnome-panel ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
philcb@philcb-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  alacarte gnome-applets-data gnome-panel-data python-gmenu
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 31.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151452 files and directories currently installed.)
Removing alacarte ...
Removing gnome-applets-data ...
Removing gnome-panel-data ...
Removing python-gmenu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
philcb@philcb-desktop:~$ sudo apt-get install gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  gnome-tweak-tool
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/81.0 kB of archives.
After this operation, 584 kB of additional disk space will be used.
Selecting previously unselected package gnome-tweak-tool.
(Reading database ... 148518 files and directories currently installed.)
Unpacking gnome-tweak-tool (from .../gnome-tweak-tool_3.3.4-0ubuntu1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up gnome-tweak-tool (3.3.4-0ubuntu1) ..
```.

---

### Post by candtalan on 2012-04-17
> **kansasnoob said:**
> In deed, this is also why I've asked for logs :)

The apt logs will answer the question.
Thanks, I am soon to get the logs.
But I have just recalled that I also installed AWN because I love the shiny switcher applet, and this is a sort of panel related function, so, still not holding my breath, but that might be the reason. Will get to the logs before long now.

tia

---

### Post by candtalan on 2012-04-17
> **kansasnoob said:**
> Post the full output of:

```
cat /var/log/apt/history.log
```

And:

```
ls /var/log/apt
```

Please use code tags by clicking on the # in this reply box before pasting the output.

ls /var/log/apt
```

user@user-System-Product-Name:~$ ls /var/log/apt
history.log  history.log.1.gz  term.log  term.log.1.gz

```

The history.log  comprises two files, one zipped. I believe I have extracted  the earlier one and then pasted them together. Completed file, compressed, attached.
I note it is big - I started with beta2 and then of course there are many updates. Hopefully  an attached file is ok? the cat  command  is something I am not familiar with and it seemed to give incomplete results.
tia

---

### Post by kansasnoob on 2012-04-17
> **candtalan said:**
> ls /var/log/apt
```

user@user-System-Product-Name:~$ ls /var/log/apt
history.log  history.log.1.gz  term.log  term.log.1.gz

```

The history.log  comprises two files, one zipped. I believe I have extracted  the earlier one and then pasted them together. Completed file, compressed, attached.
I note it is big - I started with beta2 and then of course there are many updates. Hopefully  an attached file is ok? the cat  command  is something I am not familiar with and it seemed to give incomplete results.
tia

There it is (highlighted in red):

```
Start-Date: 2012-04-15  14:04:18
Commandline: aptdaemon role='role-commit-packages' sender=':1.91'
Install: awn-applet-awn-notification-daemon:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-volume-control:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libpanel-applet-4-0:i386 (3.4.0-0ubuntu1, automatic), python-awn-extras:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libdesktop-agnostic-fdo-gnome:i386 (0.3.92+dfsg-1, automatic), awn-applet-cpufreq:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-thinkhdaps:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-cairo-clock:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libdesktop-agnostic0:i386 (0.3.92+dfsg-1, automatic), python-paramiko:i386 (1.7.7.1-2, automatic), fortunes-min:i386 (1.99.1-4, automatic), awn-applet-notification-area:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-garbage:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-animal-farm:i386 (0.4.1~bzr1507-0ubuntu7, automatic), alacarte:i386 (0.13.2-2ubuntu4, automatic), indicator-applet-complete:i386 (0.5.0-0ubuntu1, automatic), awn-applet-awnterm:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libdesktop-agnostic-data:i386 (0.3.92+dfsg-1, automatic), python-awn:i386 (0.4.1~bzr830-2ubuntu1, automatic), awn-applet-dialect:i386 (0.4.1~bzr1507-0ubuntu7, automatic), fortune-mod:i386 (1.99.1-4, automatic), libawn1:i386 (0.4.1~bzr830-2ubuntu1, automatic), awn-applet-quit-applet:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-utidylib:i386 (0.2-8build1, automatic), python-bzrlib:i386 (2.5.0-2ubuntu2, automatic), python-configobj:i386 (4.7.2+ds-3build1, automatic), awn-applet-cairo-main-menu:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-indicator:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-gnomedesktop:i386 (2.32.0+dfsg-1, automatic), librecode0:i386 (3.6-18, automatic), libdesktop-agnostic-vfs-gio:i386 (0.3.92+dfsg-1, automatic), awn-applet-hardware-sensors:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libtidy-0.99-0:i386 (20091223cvs-1ubuntu2, automatic), python-xklavier:i386 (0.4-2build1, automatic), awn-settings:i386 (0.4.1~bzr830-2ubuntu1, automatic), awn-applet-awn-system-monitor:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-todo:i386 (0.4.1~bzr1507-0ubuntu7, automatic), bzr:i386 (2.5.0-2ubuntu2, automatic), python-glade2:i386 (2.24.0-3, automatic), awn-applet-related:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-shinyswitcher:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-bandwidth-monitor:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-desktop-agnostic:i386 (0.3.92+dfsg-1, automatic), **[COLOR="Red"]gnome-session-fallback:i386 (3.2.1-0ubuntu7, automatic)[/COLOR]**, avant-window-navigator:i386 (0.4.1~bzr830-2ubuntu1), awn-applet-showdesktop:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-feedparser:i386 (5.1-0ubuntu3, automatic), avant-window-navigator-data:i386 (0.4.1~bzr830-2ubuntu1, automatic), libglade2-0:i386 (2.6.4-1ubuntu1, automatic), python-rsvg:i386 (2.32.0+dfsg-1, automatic), awn-applet-file-browser-launcher:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-stack:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-comics:i386 (0.4.1~bzr1507-0ubuntu7, automatic), gnome-applets:i386 (3.2.1-0ubuntu1, automatic), python-gmenu:i386 (3.0.1-0ubuntu7, automatic), awn-applet-media-player:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libwebkitgtk-1.0-common:i386 (1.8.0-0ubuntu2, automatic), gnome-panel:i386 (3.4.0-0ubuntu1, automatic), libgnome-desktop-2-17:i386 (2.32.1-0ubuntu9, automatic), libdesktop-agnostic-cfg-keyfile:i386 (0.3.92+dfsg-1, automatic), libwebkitgtk-1.0-0:i386 (1.8.0-0ubuntu2, automatic), libjavascriptcoregtk-1.0-0:i386 (1.8.0-0ubuntu2, automatic), awn-applets-common:i386 (0.4.1~bzr1507-0ubuntu7, automatic), gnome-applets-data:i386 (3.2.1-0ubuntu1, automatic), awn-applet-media-icon-applet:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-battery-applet:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-webapplet:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-mail:i386 (0.4.1~bzr1507-0ubuntu7, automatic), gir1.2-panelapplet-4.0:i386 (3.4.0-0ubuntu1, automatic), gnome-panel-data:i386 (3.4.0-0ubuntu1, automatic), awn-applet-feeds:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-gtop:i386 (2.32.0+dfsg-1, automatic), awn-applet-media-control:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-common-folder:i386 (0.4.1~bzr1507-0ubuntu7, automatic)
End-Date: 2012-04-15  14:05:37

```

Maybe when you installed awn? It's harder to parse using USC than if one uses either apt or synaptic but it was clearly installed intentionally.

---

### Post by mc4man on 2012-04-17
> **kansasnoob said:**
>  It's harder to parse using USC than if one uses either apt or synaptic but it was clearly installed intentionally.
I would differ there - 
The History in Software-Center shows everything installed, whether from Sc, apt-get, synaptic, ect.

The History in synaptic only shows what's been installed via synaptic

---

### Post by kansasnoob on 2012-04-17
> **mc4man said:**
> I would differ there - 
The History in Software-Center shows everything installed, whether from Sc, apt-get, synaptic, ect.

The History in synaptic only shows what's been installed via synaptic

I meant only that it's a bit harder to parse in the apt logs ;)

I'm not cursing USC, just commenting on how apt logs show things, but it's still always there, sometimes just a bit harder to see.

---

### Post by mc4man on 2012-04-17
> **kansasnoob said:**
> I meant only that it's a bit harder to parse in the apt logs ;)

I'm not cursing USC, just commenting on how apt logs show things, but it's still always there, sometimes just a bit harder to see.

Well you don't need to parse the logs, just open Sc & click on History, it's all right there, line by line
The one advantage of synaptic is it breaks it history into individual uses

---

### Post by candtalan on 2012-04-17
> **kansasnoob said:**
> There it is (highlighted in red):

```
Start-Date: 2012-04-15  14:04:18
Commandline: aptdaemon role='role-commit-packages' sender=':1.91'
Install: awn-applet-awn-notification-daemon:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-volume-control:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libpanel-applet-4-0:i386 (3.4.0-0ubuntu1, automatic), python-awn-extras:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libdesktop-agnostic-fdo-gnome:i386 (0.3.92+dfsg-1, automatic), awn-applet-cpufreq:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-thinkhdaps:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-cairo-clock:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libdesktop-agnostic0:i386 (0.3.92+dfsg-1, automatic), python-paramiko:i386 (1.7.7.1-2, automatic), fortunes-min:i386 (1.99.1-4, automatic), awn-applet-notification-area:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-garbage:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-animal-farm:i386 (0.4.1~bzr1507-0ubuntu7, automatic), alacarte:i386 (0.13.2-2ubuntu4, automatic), indicator-applet-complete:i386 (0.5.0-0ubuntu1, automatic), awn-applet-awnterm:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libdesktop-agnostic-data:i386 (0.3.92+dfsg-1, automatic), python-awn:i386 (0.4.1~bzr830-2ubuntu1, automatic), awn-applet-dialect:i386 (0.4.1~bzr1507-0ubuntu7, automatic), fortune-mod:i386 (1.99.1-4, automatic), libawn1:i386 (0.4.1~bzr830-2ubuntu1, automatic), awn-applet-quit-applet:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-utidylib:i386 (0.2-8build1, automatic), python-bzrlib:i386 (2.5.0-2ubuntu2, automatic), python-configobj:i386 (4.7.2+ds-3build1, automatic), awn-applet-cairo-main-menu:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-indicator:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-gnomedesktop:i386 (2.32.0+dfsg-1, automatic), librecode0:i386 (3.6-18, automatic), libdesktop-agnostic-vfs-gio:i386 (0.3.92+dfsg-1, automatic), awn-applet-hardware-sensors:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libtidy-0.99-0:i386 (20091223cvs-1ubuntu2, automatic), python-xklavier:i386 (0.4-2build1, automatic), awn-settings:i386 (0.4.1~bzr830-2ubuntu1, automatic), awn-applet-awn-system-monitor:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-todo:i386 (0.4.1~bzr1507-0ubuntu7, automatic), bzr:i386 (2.5.0-2ubuntu2, automatic), python-glade2:i386 (2.24.0-3, automatic), awn-applet-related:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-shinyswitcher:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-bandwidth-monitor:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-desktop-agnostic:i386 (0.3.92+dfsg-1, automatic), **[COLOR="Red"]gnome-session-fallback:i386 (3.2.1-0ubuntu7, automatic)[/COLOR]**, avant-window-navigator:i386 (0.4.1~bzr830-2ubuntu1), awn-applet-showdesktop:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-feedparser:i386 (5.1-0ubuntu3, automatic), avant-window-navigator-data:i386 (0.4.1~bzr830-2ubuntu1, automatic), libglade2-0:i386 (2.6.4-1ubuntu1, automatic), python-rsvg:i386 (2.32.0+dfsg-1, automatic), awn-applet-file-browser-launcher:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-stack:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-comics:i386 (0.4.1~bzr1507-0ubuntu7, automatic), gnome-applets:i386 (3.2.1-0ubuntu1, automatic), python-gmenu:i386 (3.0.1-0ubuntu7, automatic), awn-applet-media-player:i386 (0.4.1~bzr1507-0ubuntu7, automatic), libwebkitgtk-1.0-common:i386 (1.8.0-0ubuntu2, automatic), gnome-panel:i386 (3.4.0-0ubuntu1, automatic), libgnome-desktop-2-17:i386 (2.32.1-0ubuntu9, automatic), libdesktop-agnostic-cfg-keyfile:i386 (0.3.92+dfsg-1, automatic), libwebkitgtk-1.0-0:i386 (1.8.0-0ubuntu2, automatic), libjavascriptcoregtk-1.0-0:i386 (1.8.0-0ubuntu2, automatic), awn-applets-common:i386 (0.4.1~bzr1507-0ubuntu7, automatic), gnome-applets-data:i386 (3.2.1-0ubuntu1, automatic), awn-applet-media-icon-applet:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-battery-applet:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-webapplet:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-mail:i386 (0.4.1~bzr1507-0ubuntu7, automatic), gir1.2-panelapplet-4.0:i386 (3.4.0-0ubuntu1, automatic), gnome-panel-data:i386 (3.4.0-0ubuntu1, automatic), awn-applet-feeds:i386 (0.4.1~bzr1507-0ubuntu7, automatic), python-gtop:i386 (2.32.0+dfsg-1, automatic), awn-applet-media-control:i386 (0.4.1~bzr1507-0ubuntu7, automatic), awn-applet-common-folder:i386 (0.4.1~bzr1507-0ubuntu7, automatic)
End-Date: 2012-04-15  14:05:37

```

Maybe when you installed awn? It's harder to parse using USC than if one uses either apt or synaptic but it was clearly installed intentionally.

As a novice I guess it was installed as part of AWN which I got from Ubuntu Software Centre, it is in between 
awn-applet-bandwidth-monitor:i386
and
avant-window-navigator:i386

Without doing a lot of trial and error tests - no time just now - it gives me a strong clue  as to the cause. It is not a problem for me, because I like AWN and the shiny switcher is something I also like a lot, so it is good to know a bit of what is going on.

Thanks all
(marking as solved)

---

