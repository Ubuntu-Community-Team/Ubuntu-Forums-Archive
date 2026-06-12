---
title: "Ardour help..."
date: 2006-04-06
forum: The Cafe
---

### Post by the_exception on 2006-04-06
I couldn't seem to find help in any other threads on here, so forgive me if this is a repeat.  Anyways, I'm on Kubuntu, and went ahead and installed Ardour for music production, however I can't seem to get the program to run.  At first, when I installed it there was a problem with the jack server, and I couldn't get the program running until I installed qjackctl, then the program would boot and seemed to run fine.  However, today I found that the program wouldn't start.  Apparently, it's looking for midi devices that just aren't there.  After botting jack here's the output I get for when attempting to boot Ardour

Loading UI configuration file /etc/ardour/ardour_ui.rc
Loading system configuration file /etc/ardour/ardour_system.rc
Loading user configuration file /home/michael.ardour/ardour.rc
ardour: [ERROR]: MIDI: no such port device
ardour: [ERROR]: MIDI: no such port device
ardour: [ERROR]: MIDI: no such port device

I've found that when I remove the first three MIDI lines from the /home/michael/.ardour/ardour.rc file, the three errors dissappear, one for each line.  However, this doesn't solve the problem, as the booting process just hangs there.  The window that pops up just ends at Loading user configuration file...

So I'm very curious about what the problem could be, and Google has been no help so far.  Any and all replies are greatly appreciated

Thanks!

---

### Post by the_exception on 2006-04-10
Bump?

---

### Post by GarethMB on 2006-04-10
try using timidity to open some of these midi ports.
might do better in one of the support forums too.

---

