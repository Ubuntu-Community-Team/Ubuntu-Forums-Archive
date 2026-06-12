---
title: "Useful commands for the &quot;Run Application&quot; dialog (Alt+F2, shortcuts, GNOME)"
date: 2010-12-30
forum: Tutorials
---

### Post by plari on 2010-12-30
We can open the "Run Application" dialog of GNOME pressing the F2 key while holding the Alt key.

In this dialog we can type the name of an application and then press the Enter or  Return key (or click on the Run button) so the desired application  opens. For example, if we type totem and press Enter the Totem movie player opens.

We can also type the address of a folder so Nautilus opens in that  place. For example if we enter /etc Nautilus opens in this directory.

This dialog helps us entering the data. For example if we type ged automatically gedit is offered.

This dialog can run any of the many applications inside /usr/bin .

====================================================

Here is a list of the ones I use more often:

gedit : gedit (text editor)

gnome-control-center : GNOME Control Center (control panel)

gnome-terminal : GNOME Terminal (terminal emulator)

xset dpms force off : turns the screen off (useful for laptops)

====================================================

Other ones:

eog : Eye of GNOME (image viewer) (not necessary because it opens when  we click on an image showing that image -if it's the default application  for the image format-)

file-roller : File Roller (archive manager) (not necessary because it  opens when we click on a compressed file we want to decompress; and  there is a Compress... entry on the menu when we right click after  having selected one or more files we want to compress)

gcalctool : gcalctool (calculator)

gconf-editor : Configuration Editor (user preferences and system  configuration data editor for the GNOME Desktop and many applications)

gnome-search-tool : Search for Files (file searcher)

gnome-session-save --logout-dialog : "Log Out of the Session" dialog (to  finish or close the session; or to switch or change the user)

gnome-session-save --shutdown-dialog : "Shut Down the Computer" dialog  (to turn the computer off, reboot it, suspend it or hibernate it)

totem : Totem (movie player; also plays audios) (not necessary because it opens when we click on a film or song)

xcalc : xcalc (calculator)

xterm : xterm (terminal emulator) (gnome-terminal has an useful scrollbar)

---

### Post by RobOrr on 2011-01-01
If you're looking for a more powerful version of this dialog, I recommend using Gnome-Do. It has various useful plugins, such as a Rhythmbox plugin which lets me start typing an artist, such as the Newton in newton faulkner, and it'll start playing songs by that artist.

It's in the repositories, more information can be found at:
[http://do.davebsd.com/](http://do.davebsd.com/)

---

### Post by plari on 2011-01-03
Thanks, RobOrr.

Another advantage of gnome-terminal vs xterm is that the first one allows to copy and paste.

---

### Post by itcotbtoemik on 2011-01-08
Dave Simmons' hack for the selection isn't necessary,
since xterm's provided (menu-selectable) "Select to
Clipboard" since early 2006.

(Copying to both primary and clipboard might be useful,
but I've seen no evidence of it).

---

### Post by itcotbtoemik on 2011-01-15
x-terminal-emulator is a preference (actually points to the /etc/alternatives directory).

---

### Post by vezolmi on 2011-05-05
2 more:
gucharmap or gnome-character-map : GNOME Character Map
setxkbmap **xx** : change the keyboard layout (xx can be **it** or **gb** or **es** or **fr** ...)

---

### Post by vezolmi on 2011-12-27
2 more:
onboard : onscreen keyboard
onboard-settings : configure Onboard

---

### Post by vezolmi on 2012-04-22
gnome-calculator opens also gcalctool

---

### Post by vezolmi on 2012-04-23
Some more commands:

ooffice or openoffice.org : OpenOffice.org
ooffice -draw or openoffice.org -draw : OpenOffice.org Draw
ooffice -calc or openoffice.org -calc : OpenOffice.org Calc
ooffice -impress or openoffice.org -impress : OpenOffice.org Impress
ooffice -writer or openoffice.org -writer : OpenOffice.org Writer
ooffice -math or openoffice.org -math : OpenOffice.org Math

---

### Post by vezolmi on 2012-06-23
The GNOME Character Map can also be opened just with this short command:
charmap

---

### Post by vezolmi on 2012-09-18
Another one: 
simple-scan : Simple Scan

---

### Post by contributor on 2012-09-20
> **vezolmi said:**
> Another one: 
simple-scan : Simple Scan

Nice work Vezolmi. I was not aware about this one.

---

### Post by vezolmi on 2012-11-21
Another one:
alacarte : Main Menu (select which applications we want to appear in the main menu)

This one doesn't work in Ubuntu 12.04 Precise Pangolin. Anyone knows any alternative command for this in this 12 version?

Thanks

---

### Post by vezolmi on 2012-11-21
Another 2, related to the keyboard:
gnome-keyboard-properties : Keyboard Preferences
gnome-keybinding-properties : Keyboard Shortcuts

These 2 ones don't work in Ubuntu 12.04 Precise Pangolin. In this  version, from the control panel you have a Keyboard option where you can  both change keyboard settings (layouts, ...) and keybindings  (shortcuts). Anyone knows which terminal command can open this Keyboard  dialog directly?

Thanks

---

### Post by vezolmi on 2012-11-21
Another command:
gnome-system-monitor : System Monitor (System -info about the system: installed version of Ubuntu, hardware, ...-, Processes -we can view and end them from here-, Resources -monitor of CPU, memory, ...- and File Systems)

---

### Post by Elfy on 2012-11-21
If you want to create a list of commands that can be run from the Run dialogue, then an alpahabetical list on a wiki is a better idea.

Closed thread.

---

