---
title: "jackd2 with alsa support"
date: 2011-02-26
forum: Ubuntu Studio
---

### Post by alikthename on 2011-02-26
Hi everybody! I understand that this is not the Debian forum, but since I can't get support from it I post to debian/ubuntu audio distribution forums. Ma be somebody will be able to help me.

The system I use is Debian Squeeze. Can't get what's wrong but jackd2 from debian official repositories does not work with alsa (I have alsa-base, alsa-tools, libaudio-dev, libaudiofile-dev and libasound2-dev installed). Now I downloaded fresh jackd2 source from sourceforge and when I try to "./waf -configure" it it says that there is no alsa package or it's too old in the system and configures itself without alsa support. What do I miss?

Thanks in advance.

---

### Post by cchhrriiss121212 on 2011-02-26
First I would recommend you switch back to the jackd2 that is in the official repos.
> Can't get what's wrong but jackd2 from debian official repositories does not work with alsaCould you be more specific about what doesn't work? Any error messages for example?

---

### Post by alikthename on 2011-02-26
Here is what qjackctl gives me

15:15:37.141 /usr/bin/jackd -r -dALSA -r44100 -p1024
Cannot connect to server socket err = ÐÐµÑ&#130; Ñ&#130;Ð°ÐºÐ¾Ð³Ð¾ Ñ&#132;Ð°Ð¹Ð»Ð° Ð¸Ð»Ð¸ ÐºÐ°Ñ&#130;Ð°Ð»Ð¾Ð³Ð°
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = ÐÐµÑ&#130; Ñ&#130;Ð°ÐºÐ¾Ð³Ð¾ Ñ&#132;Ð°Ð¹Ð»Ð° Ð¸Ð»Ð¸ ÐºÐ°Ñ&#130;Ð°Ð»Ð¾Ð³Ð°
Cannot connect to server socket
jack server is not running or cannot be started
15:15:37.268 &#1057;&#1084;&#1077;&#1085;&#1072; &#1075;&#1088;&#1072;&#1092;&#1072; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081; ALSA.
15:15:37.269 JACK &#1073;&#1099;&#1083; &#1079;&#1072;&#1087;&#1091;&#1097;&#1077;&#1085; &#1089; PID=21660.
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
Unknown driver "ALSA"
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
15:15:37.279 C&#1077;&#1088;&#1074;&#1077;&#1088; JACK &#1086;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1089;&#1086; &#1089;&#1090;&#1072;&#1090;&#1091;&#1089;&#1086;&#1084; &#1074;&#1099;&#1093;&#1086;&#1076;&#1072; 255.
15:15:37.279 Post-shutdown script...
15:15:37.280 killall jackd
15:15:37.343 &#1057;&#1084;&#1077;&#1085;&#1072; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1081; ALSA.
jackd: Ð¿Ñ&#128;Ð¾Ñ&#134;ÐµÑÑ Ð½Ðµ Ð½Ð°Ð¹Ð´ÐµÐ½
15:15:37.685 Post-shutdown script terminated &#1089;&#1086; &#1089;&#1090;&#1072;&#1090;&#1091;&#1089;&#1086;&#1084; &#1074;&#1099;&#1093;&#1086;&#1076;&#1072; 256.
15:15:39.357 &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1080;&#1090;&#1100;&#1089;&#1103; &#1089; &#1089;&#1077;&#1088;&#1074;&#1077;&#1088;&#1086;&#1084; JACK. - &#1042;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1080;&#1077; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080; &#1074; &#1094;&#1077;&#1083;&#1086;&#1084; &#1085;&#1077;&#1091;&#1076;&#1072;&#1095;&#1085;&#1086;. - &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1080;&#1090;&#1100;&#1089;&#1103; &#1089; &#1089;&#1077;&#1088;&#1074;&#1077;&#1088;&#1086;&#1084;. &#1055;&#1088;&#1086;&#1089;&#1084;&#1086;&#1090;&#1088;&#1080;&#1090;&#1077; &#1074;&#1099;&#1074;&#1086;&#1076; &#1074; &#1086;&#1082;&#1085;&#1077; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1081;.
Cannot connect to server socket err = ÐÐµÑ&#130; Ñ&#130;Ð°ÐºÐ¾Ð³Ð¾ Ñ&#132;Ð°Ð¹Ð»Ð° Ð¸Ð»Ð¸ ÐºÐ°Ñ&#130;Ð°Ð»Ð¾Ð³Ð°
Cannot connect to server socket
jack server is not running or cannot be started
15:15:43.834 &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1080;&#1090;&#1100;&#1089;&#1103; &#1089; &#1089;&#1077;&#1088;&#1074;&#1077;&#1088;&#1086;&#1084; JACK. - &#1042;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1080;&#1077; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080; &#1074; &#1094;&#1077;&#1083;&#1086;&#1084; &#1085;&#1077;&#1091;&#1076;&#1072;&#1095;&#1085;&#1086;. - &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1080;&#1090;&#1100;&#1089;&#1103; &#1089; &#1089;&#1077;&#1088;&#1074;&#1077;&#1088;&#1086;&#1084;. &#1055;&#1088;&#1086;&#1089;&#1084;&#1086;&#1090;&#1088;&#1080;&#1090;&#1077; &#1074;&#1099;&#1074;&#1086;&#1076; &#1074; &#1086;&#1082;&#1085;&#1077; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1081;.
Cannot connect to server socket err = ÐÐµÑ&#130; Ñ&#130;Ð°ÐºÐ¾Ð³Ð¾ Ñ&#132;Ð°Ð¹Ð»Ð° Ð¸Ð»Ð¸ ÐºÐ°Ñ&#130;Ð°Ð»Ð¾Ð³Ð°
Cannot connect to server socket
jack server is not running or cannot be started

And here is what I found, it works if I type in cli 
/usr/bin/jackd -r -dalsa -r44100 -p1024
instead of 
/usr/bin/jackd -r -dALSA -r44100 -p1024

---

### Post by Pablo_F on 2011-02-26
The fact that you can't compile jackd has nothing to do with the problem. To compile a program you need the development package of the library.

Anyway, neither do I think that your diagnosis is correct and I agree with Cchhrriiss: Stick to your distro packages by the time being and show the error messages (show the whole content of the message window of Jack Control).

Also, show the output of:

cat /proc/asound/cards 

cat /proc/asound/modules

aplay -l

Cheers, Pablo

---

### Post by alikthename on 2011-02-26
Changed 
Driver=ALSA
to
Driver=alsa
 in ~/.config/rncbc.org/QjackCtl.conf

Seems to work now.

---

### Post by Pablo_F on 2011-02-26
You have it. The driver should be alsa, not ALSA

There is something wrong in ~/.config/rncbc.org/QjackCtl.conf and/or in your qjackctl's setup window.

Cheers, Pablo

---

### Post by Pablo_F on 2011-02-26
You type faster than me. Cool.

---

### Post by alikthename on 2011-02-26
Thanks a lot guys!
Marking as solved.

---

