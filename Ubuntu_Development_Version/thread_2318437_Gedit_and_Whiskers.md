---
title: "Gedit and Whiskers"
date: 2016-03-26
forum: Ubuntu Development Version
---

### Post by makitso on 2016-03-26
Xubuntu 16.04 and have installed gedit.  However, it does not appear in the Whiskers menu?

---

### Post by ajgreeny on 2016-03-26
I presume you are aware that 16.04 is still only in beta form, and that minor bugs are still possible, or even likely to be seen.

Have you logged out and in again or perhaps rebooted; did that help?

If not, you could try copying the gedit-desktop file from /usr/share/applications to ~/.local/share/applications to see if that helps, or just use menu-libre to add gedit manually to the whisker menu.

---

### Post by Dennis N on 2016-03-26
Here is one likely cause:

Look at the gedit desktop file in /usr/share/applications - it is probably named gedit.desktop. Look for a line beginning with "OnlyShowIn=". It may contain reference to specific desktop environment(s) like Unity. If so, comment it out (place # at the start of the line), and save.

Less likely is a line beginning "NotShowIn=", but if present, that too can cause a failure to display.

---

### Post by makitso on 2016-03-26
>  I presume you are aware that 16.04 is still only in beta form...

Yes, I understand that. 

> Look at the gedit desktop file in /usr/share/applications....

There are no issues with the desktop file

---

### Post by vasa1 on 2016-03-26
Why don't you post the contents of the .desktop file?

---

### Post by ajgreeny on 2016-03-26
The default gedit.desktop file in 16.04 is
```
[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.18.3
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit/gedit-bugreport
Actions=new-window;new-document;
Keywords=Text;Editor;Plaintext;Write;
X-Ubuntu-Gettext-Domain=gedit

X-AppStream-Ignore=true

[Desktop Action new-window]
Name=Open a New Window
Exec=gedit --new-window

[Desktop Action new-document]
Name=Open a New Document
Exec=gedit --new-document
```
so if that is what makitso sees I can not see why it should not be in the whisker menu.

I do seem to remember, however, that I have had to manually copy some desktop files to ~/.local/share/applications for them to appear in the whisker menu of 14.04, but that will have been a long time ago now, so my memory may be playing tricks.
I still think it worth copying the desktop file to ~/.local/share/applications to see if that works.

---

### Post by Dennis N on 2016-03-26
I cannot duplicate this problem. I installed gedit in Xubuntu 16.04 beta 1 (with all updates applied) and it appears in the Whisker menu under "Accessories". No rebooting, logout/in, or other additional steps were necessary.

---

### Post by makitso on 2016-03-26
Well, I have 4 systems on xubuntu 16.04 and only one has the problem.  On that system the whiskers menu shows run gedit.  I have reinstalled gedit on that system and nothing changes.  Oh well, it must be operator error.

---

