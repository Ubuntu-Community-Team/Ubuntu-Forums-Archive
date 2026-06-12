---
title: "Jack start problem"
date: 2010-07-22
forum: Ubuntu Studio
---

### Post by V-music on 2010-07-22
Hello. I have a problem with  starting JACK. When I turn on my computer, then I can to start/stop JACK. Bat very often, after some time of work with computer I can not already start JACK.

OS                Ubuntu studio 10.04
Souns card   Creative Audigy  SE

> 
19:01:24.877 Patchbay deactivated.
19:01:24.878 &#1055;&#1077;&#1088;&#1077;&#1079;&#1072;&#1087;&#1091;&#1089;&#1082; &#1089;&#1090;&#1072;&#1090;&#1080;&#1089;&#1090;&#1080;&#1082;&#1080;
19:01:24.915 ALSA connection graph change.
19:01:25.111 ALSA connection change.
19:01:26.408 &#1057;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081;, &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1103;&#1077;&#1084;&#1099;&#1081; &#1087;&#1088;&#1080; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1077;...
19:01:26.410 artsshell -q terminate
sh: artsshell: not found
19:01:26.814 &#1042;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1080;&#1077; &#1089;&#1090;&#1072;&#1088;&#1090;&#1086;&#1074;&#1086;&#1075;&#1086; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1103; &#1087;&#1088;&#1077;&#1082;&#1088;&#1072;&#1097;&#1077;&#1085;&#1086; with exit status=32512.
19:01:26.814 JACK &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072;&#1077;&#1090;&#1089;&#1103; ...
19:01:26.814 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -P
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
19:01:26.821 JACK was started with PID=4120.
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    960330
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|-|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
19:01:27.105 JACK-&#1089;&#1077;&#1088;&#1074;&#1077;&#1088; &#1086;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1091;&#1089;&#1087;&#1077;&#1096;&#1085;&#1086;. ("The server is stopped successfully"  from Russian)
19:01:27.106 Post-shutdown script...
19:01:27.107 killall jackd
19:01:27.108 JACK has crashed.
jackd: Ð¿Ñ&#8364;Ð¾Ñ&#8224;ÐµÑÑ Ð½Ðµ Ð½Ð°Ð¹Ð´ÐµÐ½
19:01:27.575 Post-shutdown script terminated with exit status=256.
19:01:29.195 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by Pablo_F on 2010-07-22
You marked it as solved, but you don't tell us how you solved it ;) Please.

---

### Post by V-music on 2010-07-23
I am sorry. I was mistaken. It is not solved. Please help.

---

### Post by cchhrriiss121212 on 2010-07-23
Check you do not have any other programs open that are using audio when you start jack. If it only happens after you have been using things then it may be some background service causing trouble.

---

