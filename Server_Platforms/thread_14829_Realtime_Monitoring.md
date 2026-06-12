---
title: "Realtime Monitoring"
date: 2005-02-10
forum: Server Platforms
---

### Post by orion_114 on 2005-02-10
I am looking for a tool that provides realtime graphing of the interfaces on my networks routers. I currently have MRTG installed but the graphs are not realtime enough for me to troubleshoot. Is there a tool out there that could give me near realtime graphing and statistical information about my cisco routers ?

---

### Post by smok on 2005-02-10
[QUOTE=orion_114]I am looking for a tool that provides realtime graphing of the interfaces on my networks routers. I currently have MRTG installed but the graphs are not realtime enough for me to troubleshoot. Is there a tool out there that could give me near realtime graphing and statistical information about my cisco routers ?[/QUOTE]


Another tool like MRTG you could use is Cacti.  It is a wrapper layer around MRTG and RRD.

All these tools allow the interval between measurements to be set so you could get 1 min or 10 sec readings. 

Richard

(Edited to correct spelling)

---

### Post by orion_114 on 2005-02-10
Thanks. I'll give it a look.

---

### Post by raven on 2005-06-24
[QUOTE=orion_114]I am looking for a tool that provides realtime graphing of the interfaces on my networks routers. I currently have MRTG installed but the graphs are not realtime enough for me to troubleshoot. Is there a tool out there that could give me near realtime graphing and statistical information about my cisco routers ?[/QUOTE]

How did you make mrtg works, 
I try to launch it from terminal
I get this message

 "     ERROR: Mrtg will most likely not work propperly when the environment
       variable LANG is set to UTF-8. Please run mrtg in an environment
       where this is not the case:

       env LANG=C /usr/bin/mrtg ...   "

any help is appreciated

---

### Post by eromaled on 2006-02-09
I am also wondering - How do you change the time interval to 10 secs ?

---

### Post by geekman on 2006-07-04
[QUOTE=raven]How did you make mrtg works, 
I try to launch it from terminal
I get this message

 "     ERROR: Mrtg will most likely not work propperly when the environment
       variable LANG is set to UTF-8. Please run mrtg in an environment
       where this is not the case:

       env LANG=C /usr/bin/mrtg ...   "

any help is appreciated[/QUOTE]
 For anyone still needing help with this, simply use the command in the message (like it says :P) or type "LANG=C" without quotes to set it then you can just use mrtg. Changing the LANG setting hasnt effected me so far....

---

### Post by geekman on 2007-01-21
What was stated in my last post doesn´t really work all that well, or not at all :D
but changing LANG in /etc/environment should work. After you do this you must either reboot or do export LANG

Thanks

---

