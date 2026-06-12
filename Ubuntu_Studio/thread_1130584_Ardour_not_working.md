---
title: "Ardour not working"
date: 2009-04-19
forum: Ubuntu Studio
---

### Post by chkneater on 2009-04-19
I've got Jack running and am able to use jack eq and get sound, however Ardour will never load.  I used synaptic to install it and have uninstalled/reinstalled it and still not working.

---

### Post by kayosiii on 2009-04-20
That is most odd... Could you try starting it from a terminal (in the assesories menu in GNOME)...
type in ardour then TAB then Enter... copy anything that happens in the terminal an post it here...

---

### Post by chkneater on 2009-04-21
I've tried opening ardour from the term b4 but it didn't work.  This time, hitting the tab button after ardour, it loaded for the first time.  Here is the script I got.  I've had the GTKspinbutton problem trying to get my webcam to work.  Thanks for the help.

bobby@HellKiller:~$ ardour2
WARNING: Your system has a limit for maximum amount of locked memory!
This might cause Ardour to run out of memory before your system runs out of memory. You can view the memory limit with 'ulimit -l', and it is normally controlled by /etc/security/limits.conf
Ardour/GTK 2.5
   (built using 3525 and GCC version 4.3.2)
Copyright (C) 1999-2008 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
theme_init() called from internal clearlooks engine
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
ardour: [INFO]: Ardour will be limited to 1024 open files
loading system configuration file /etc/ardour2/ardour_system.rc
ardour: [INFO]: No H/W specific optimizations in use
ardour: [INFO]: looking for control protocols in /home/bobby/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control surface protocol discovered: "Mackie"

(ardour-2.5:6175): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(ardour-2.5:6175): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(ardour-2.5:6175): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(ardour-2.5:6175): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

---

### Post by Stochastic on 2009-04-21
Try unplugging your mackie control surface and see if things start (post the terminal output if it doesn't start).

---

### Post by chkneater on 2009-04-22
Sorry, I don't know anything about Mackie Control surface.  I see it in the output but have no idea about it.  The only thing physical besides the ethernet and printer is the guitar amp so it must be software of some sort, right?

---

### Post by Stochastic on 2009-04-22
After thinking about your output for a bit, and looking some stuff up on google, I don't think the mackie line is the trouble spot (maybe it is, but I don't think so).

It looks like the GTK warning is in a loop.  If you let that run for half an hour does it eventually spit out an error or does it just keep repeating?  does it stop itself after a certain number of warnings?

I'd also mention that you may find more internal Ardour code knowledge from the ardour tech support forums. [http://www.ardour.org/forum](http://www.ardour.org/forum) If we can't help you, they're the people to talk to.

---

### Post by chkneater on 2009-05-02
That's interesting, I never let it run for that long.  I'll leave it running for a while and let you know.

---

### Post by chkneater on 2009-05-02
I let it run for an hour and it gave no new error outputs.  It seems to stop at the repeating after 4 times.  I've had that GTK spin button error with a logitech webcam a while ago also.

---

