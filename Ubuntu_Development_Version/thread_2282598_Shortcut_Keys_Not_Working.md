---
title: "Shortcut Keys Not Working"
date: 2015-06-15
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-06-15
Got Gnome 15.10 up and all seems fine except the Shortcut keys no longer work.  Specifically the CTL-ALT-T does not bring up a new terminal session.  Went to All Settings > Keyboard > Shortcuts and ensured that new terminal was set to CTL-ALT-T but still doesn't work.

---

### Post by steveo314 on 2015-06-26
Give this a try:

> Gnome-Shell uses not Metacity Window Manager, but new Window Manager - Mutter, which uses new configuration system - dconf, while old GNOME and Ubuntu Unity interface uses old configuration system - gconf. Because of this "System Settings" -> Keyboard -> Shortcuts doesn't work on Ubuntu with GNOME3 shell :(

One Workaround

Install dconf-tools Install dconf-tools

Run dconf-editor

Look in org.gnome.desktop.wm.keybindings or org.gnome.mutter.keybindings

[found here in the 1st reply]("http://askubuntu.com/questions/135425/keyboard-shortcuts-dont-work-in-gnome-shell")

---

### Post by crcarson on 2015-07-01
> **steveo314 said:**
> Give this a try:



[found here in the 1st reply]("http://askubuntu.com/questions/135425/keyboard-shortcuts-dont-work-in-gnome-shell")

Thanks for the reply.  Don't see any "launch terminal" in dconf after installing dconf-tools.  Do I need to add something?

---

### Post by mc4man on 2015-07-04
Seems to be par for the course during dev that shortcuts break in a gnome session (gnome-shell
There are quite  number of non-functioning ones plus custom shortcuts seem to not work either
Sooner or later will likely be fixed..

---

### Post by ventrical on 2015-07-04
> **mc4man said:**
> Seems to be par for the course during dev that shortcuts break in a gnome session (gnome-shell
There are quite  number of non-functioning ones plus custom shortcuts seem to not work either
Sooner or later will likely be fixed..

It works on some installs and not on others. More or less random atm.

---

### Post by mc4man on 2015-07-04
> **ventrical said:**
> It works on some installs and not on others. More or less random atm.
How does one log out of a gnome-shell session if ctrl+alt+delete doesn't work?

Edit - I see, thru name....

---

### Post by vq1 on 2015-07-04
not a fix, but I use xbindkeys to make keyboard shortcuts. I used it for screen brightness

---

### Post by ventrical on 2015-07-04
> **mc4man said:**
> How does one log out of a gnome-shell session if ctrl+alt+delete doesn't work?

I have three different hdds on three different machines with  gnome-shell (ubuntu-gnome) wily installed. On one machine I upgraded from 15.04 to 15.10 and had added the gnome ppa. This is the one that will not give me a terminal with Ctrl+Alt+T. The other two are installs from wiley ubuntu-gnome.isos. (ctrl+alt+T work on these).

 I am just happen chance doing a regular update/upgrade on one OCed system and I will try ctrl+alt+del after it is done updating and get back.

edit:after updates.

Ctrl+alt+T busted.

Ctrl+alt+Del busted too.

---

### Post by ventrical on 2015-07-04
If you hit the ctrl+alt+del keys real fast in succession (like playing a piano) and you have a firefox screen open you will notice the page jump up and down now and again.

---

### Post by Daliolores on 2015-07-20
You could easily install the staging-ppa, update and dist-upgrade. I faced the same bug and that workaround solved it. I guess it's because 15.10 is still an Alpha Version...


Following packages are getting a change or getting installed:

Paketaktualisierung (Upgrade) wird berechnet... Fertig
Die folgenden NEUEN Pakete werden installiert:
  libmirclient8 libmircommon4
Die folgenden Pakete werden aktualisiert (Upgrade):
  aisleriot gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-goa-1.0 gir1.2-gtk-3.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-webkit-3.0 gnome-control-center
  gnome-control-center-data gnome-control-center-shared-data
  gnome-online-accounts gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-shell gnome-shell-common libgail-3-0 libgirepository-1.0-1
  libgnome-control-center1 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-1 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk-3-dev
  libjavascriptcoregtk-3.0-0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
28 aktualisiert, 2 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0 B von 51,5 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 56,8 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] j



... and for the lost shortcut to quit your session, if the settings had been overwritten, you could have a look into "sudo dpkg-reconfigure keyboard-configuration". There's an option to be set, to let you log out in the way you described. But be sure to check your keyboard settings first and just don't miss to set the function for the two keys you'll be asked  for. You can check your current settings with "setxkbmap -query".

---

### Post by fthx on 2015-07-20
latest gnome-shell update solved this bug :

> gnome-shell (3.16.3-1ubuntu2) wily; urgency=medium

  * debian/patches/revert-AcceleratorActivated-signature-1.patch,
    debian/patches/revert-AcceleratorActivated-signature-2.patch: Revert
    backwards-incompatible changes to the signature of the
    AcceleratorActivated signal that require gnome-settings-daemon 3.15.4.
    **Fixes media, brightness, volume, and shortcut keys.**  (LP: #1427877)
  * Conflicts gnome-settings-daemon (>= 3.15.4~) so that this doesn't happen
    again when gnome-settings-daemon 3.16 is uploaded.

---

