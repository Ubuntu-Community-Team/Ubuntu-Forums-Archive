---
title: "jack control, alsa- cannot set channel 1 for capture"
date: 2011-07-05
forum: Ubuntu Studio
---

### Post by berg3rakger4k on 2011-07-05
p, li { white-space: pre-wrap; } [COLOR=Black][COLOR=#999999]hey guys, [/COLOR][/COLOR]
i am having problem with jack and alsa
heres the message that i got when i start jack


[COLOR=#999999]23:26:06.193 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]23:26:06.713 Statistics reset.[/COLOR]
 [COLOR=#66cc99]23:26:06.876 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]23:26:08.570 ALSA connection change.[/COLOR]
 ** (<unknown>:2023): WARNING **: Invalid borders specified for theme pixmap:
         /home/satellite/.themes/Cillop-Midnite/gtk-2.0/null.png,
 borders don't fit within the image
 [COLOR=#999999]23:26:11.674 Startup script...[/COLOR]
 [COLOR=#990099]23:26:11.675 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]23:26:12.171 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]23:26:12.173 JACK is starting...[/COLOR]
 [COLOR=#990099]23:26:12.174 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n3 -i1 -o1[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]23:26:12.211 JACK was started with PID=2032.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|3|44100|1|1|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: cannot set channel count to 1 for capture
 ALSA: cannot configure capture channel
 cannot load driver module alsa
 [COLOR=#999999]23:26:12.647 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]23:26:12.649 Post-shutdown script...[/COLOR]
 [COLOR=#990099]23:26:12.656 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]23:26:13.090 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]23:26:14.256 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


[COLOR=#ff0000][COLOR=Black]i read from previous post where i should set the channels to default, i dont know how to edit ... im still new to ubuntu... any help is greatly appreciated

this is the post by the way... 
[http://ubuntuforums.org/showthread.php?t=1414204&highlight=alsa+set+channel+count](http://ubuntuforums.org/showthread.php?t=1414204&highlight=alsa+set+channel+count)
[/COLOR] [/COLOR]

---

### Post by berg3rakger4k on 2011-07-05
got it actually... :))) 
just go into setup and set the input and output to default

---

