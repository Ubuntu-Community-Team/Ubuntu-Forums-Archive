---
title: "Problem with  JACK  srart"
date: 2010-08-19
forum: Ubuntu Studio
---

### Post by V-music on 2010-08-19
Hello.
I can't start JACK in a mode of real time. More precisely it is sometimes started, but is very rare. More often it shows these messages and hangs up.

> 
15:56:45.565 Patchbay deactivated.
15:56:45.565 &#1055;&#1077;&#1088;&#1077;&#1079;&#1072;&#1087;&#1091;&#1089;&#1082; &#1089;&#1090;&#1072;&#1090;&#1080;&#1089;&#1090;&#1080;&#1082;&#1080;
15:56:45.608 ALSA connection graph change.
15:56:45.803 ALSA connection change.
15:56:48.189 &#1057;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081;, &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1103;&#1077;&#1084;&#1099;&#1081; &#1087;&#1088;&#1080; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1077;...
15:56:48.191 artsshell -q terminate
sh: artsshell: not found
15:56:48.596 &#1042;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1080;&#1077; &#1089;&#1090;&#1072;&#1088;&#1090;&#1086;&#1074;&#1086;&#1075;&#1086; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1103; &#1087;&#1088;&#1077;&#1082;&#1088;&#1072;&#1097;&#1077;&#1085;&#1086; with exit status=32512.
15:56:48.596 JACK &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072;&#1077;&#1090;&#1089;&#1103; ...
15:56:48.596 /usr/bin/jackd -dalsa -dhw:CA0106 -r44100 -p1024 -n2
15:56:48.603 JACK was started with PID=2318.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
@audio - memlock unlimited
in your /etc/limits.conf to read:
@audio - memlock 960330
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:CA0106|hw:CA0106|1024|2|44100|0|0|nomon|swmeter|-|32bit
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
15:56:50.626 Server configuration saved to "/home/vmusic/.jackdrc".
15:56:50.628 &#1055;&#1077;&#1088;&#1077;&#1079;&#1072;&#1087;&#1091;&#1089;&#1082; &#1089;&#1090;&#1072;&#1090;&#1080;&#1089;&#1090;&#1080;&#1082;&#1080;
15:56:50.658 &#1050;&#1083;&#1080;&#1077;&#1085;&#1090; &#1072;&#1082;&#1090;&#1080;&#1074;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;
15:56:50.659 JACK connection change.
15:56:50.665 JACK connection graph change.
Enhanced3DNow! detected
SSE2 detected
15:56:50.677 XRUN callback (1).
15:56:52.662 XRUN callback (47 skipped).
15:56:53.864 &#1050;&#1083;&#1080;&#1077;&#1085;&#1090; &#1076;&#1077;&#1072;&#1082;&#1090;&#1080;&#1074;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085; ("client is deactivated" from Russian)
15:56:53.865 JACK &#1086;&#1089;&#1090;&#1072;&#1085;&#1072;&#1074;&#1083;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; ...  ("Jack is stopping..." from Russian)
jack main caught signal 15
15:56:53.896 JACK-&#1089;&#1077;&#1088;&#1074;&#1077;&#1088; &#1086;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086;. ("JACK-server is stopped successfully" from Russian)
15:56:53.897 Post-shutdown script...
15:56:53.897 killall jackd
jackd: &#208;&#191;&#209;&#128;&#208;&#190;&#209;&#134;&#208;µ&#209;&#129;&#209;&#129; &#208;&#189;&#208;µ &#208;&#189;&#208;°&#208;&#185;&#208;&#180;&#208;µ&#208;&#189;
15:56:54.362 Post-shutdown script terminated with exit status=256.


I have noticed that before hangup &#1072;lways failes synchronization (I see on the Jack display). If there are no periods without synchronization, it works normally.

I have Ubuntu Studio 10.04, sound card - Creative Audigy SE. In attachment are Jack parameters. I have tried to change them, but It doesn't give result.

Tell, please, what the reason ?
Thanks.

---

### Post by Pablo_F on 2010-08-19
I think that lots of xruns kill jack. 

What is the output of 

cat /proc/interrupts 

?

Have you tried increasing the frames per period value and what is the result?

Have you tried setting the cpu freq scaling to performance?

CPU and amount of RAM you have?

---

### Post by V-music on 2010-08-19
Thank you Pablo. I have Athlon II X2 240 (2,8 GHz); 1,3 Gb memory + 256 Mb for integrated video card.
I tried increasing the frames per period value and result was the same. For example (2048 frames) in attachment. I have not tried setting the cpu freq scaling to performance ( I don't know about this setting:) ).

---

### Post by V-music on 2010-08-19
Output of cat /proc/interrupts in attachment.

---

### Post by Pablo_F on 2010-08-19
Hi, 

There is a gnome applet (add to panel...) to set the cpu frequency to performance. cat /proc/interrupts seems sane to me. Sometimes wireless is awful. An rt kernel and a well configured rtirq-init script can help a lot. Maybe try 48000 HZ... Check your system with the realtime configuration scan script you can find in the linuxmusicians' wiki... Follow this thread... [http://ubuntuforums.org/showthread.php?t=1543109](http://ubuntuforums.org/showthread.php?t=1543109)... ask in the IRC channels, maybe #jack or #ubuntustudio...

---

### Post by V-music on 2010-08-20
Thanks. 48000 HZ doesn't give result. I will continue to search.

---

