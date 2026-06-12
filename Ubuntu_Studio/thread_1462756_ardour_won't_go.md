---
title: "ardour won't go"
date: 2010-04-26
forum: Ubuntu Studio
---

### Post by shanehaua on 2010-04-26
Ok, what goes this mean?

Ardour/GTK 2.3
   (built using 3029 and GCC version 4.2.3 (Ubuntu 4.2.3-1ubuntu2))
Copyright (C) 1999-2007 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
loading user ui configuration file /home/shane/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/shane/.ardour2/ardour.rc
ardour: [INFO]: No H/W specific optimizations in use
ardour: [INFO]: looking for control protocols in /home/shane/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control surface protocol discovered: "Mackie"


I don't understand it. What does it mean?

---

### Post by sgx on 2010-04-27
Hi, its just the drunken ramblings of a wannabee guitar hero rummaging
in the dumpster bin behind Guitar Center, he muttered this to himself, last time I saw him:

ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
loading user ui configuration file /home/user/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
ardour: [INFO]: Ardour will be limited to 1024 open files
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/user/.ardour2/ardour.rc
ardour: [INFO]: No H/W specific optimizations in use
ardour: [INFO]: looking for control protocols in /home/user/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control surface protocol discovered: "Mackie"
ardour: [INFO]: Control protocol Tranzport not usable
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
system template path = /usr/share/ardour2//templates

Its a bit like a mechanic, opening the hood of his next car repair,
talking out loud to himself about what he sees under the hood.

There are lots of good youtubes showing ardour usage and setup.
Quite interesting and useful to see what others are up to in their studios.
Cheers :)

---

