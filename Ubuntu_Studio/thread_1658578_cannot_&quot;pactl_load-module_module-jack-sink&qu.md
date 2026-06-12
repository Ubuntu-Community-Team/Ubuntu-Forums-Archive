---
title: "cannot &quot;pactl load-module module-jack-sink&quot; or &quot;module-jack-source&quot;"
date: 2011-01-02
forum: Ubuntu Studio
---

### Post by asuastrophysics on 2011-01-02
Hey guys,

I'm really having a difficult time understanding how the jack system works. All I want to do is run jack and be able to hear my tracks playing from rhythmbox and firefox at the same time. To do so, the following must be entered into a terminal: 
```
pactl load-module module-jack-sink module-jack-source
```

This, quite illogically, works sometimes, and then doesn't work other times. Sometimes I will get the following output from terminal:
```
17
18
``` Which indicates that the modules loaded successfully.

Other times, I just get the following: 
```
Module initalization failed
``` For no reason at all. The thing is so dumb that it can't even spell "initialization" correctly. 

Every time I launch jack, I always quit every single application I have running, so that jack doesn't give me errors. With nothing running, I launch jack, hit "start", then type the above into terminal, and it doesn't work. Then I have to yang the computer's power plug out of the wall, and completely restart my machine, which causes the module to finally load.

What is causing this? I just want to make some tracks, not spend all day diagnosing my faulty computer. Does anyone know why this message sporadically appears?

Thanks a ton!!! A solution to this would make recording tracks so much easier!!! :guitar:  (yes I do play the bass!)

---

### Post by Terrier on 2011-01-22
Hi, I can not help very much, but in my case it only works while jack is not running. So, either assign sink and source before you start jack, or stop jack to assign it. You can restart jack by 
> jackd -d alsa
if JackControl (qjackctl) can not start it. Hope this helps!
T.

> **asuastrophysics said:**
> Hey guys,

I'm really having a difficult time understanding how the jack system works. All I want to do is run jack and be able to hear my tracks playing from rhythmbox and firefox at the same time. To do so, the following must be entered into a terminal: 
```
pactl load-module module-jack-sink module-jack-source
```This, quite illogically, works sometimes, and then doesn't work other times. Sometimes I will get the following output from terminal:
```
17
18
``` Which indicates that the modules loaded successfully.

Other times, I just get the following: 
```
Module initalization failed
``` For no reason at all. The thing is so dumb that it can't even spell "initialization" correctly. 

Every time I launch jack, I always quit every single application I have running, so that jack doesn't give me errors. With nothing running, I launch jack, hit "start", then type the above into terminal, and it doesn't work. Then I have to yang the computer's power plug out of the wall, and completely restart my machine, which causes the module to finally load.

What is causing this? I just want to make some tracks, not spend all day diagnosing my faulty computer. Does anyone know why this message sporadically appears?

Thanks a ton!!! A solution to this would make recording tracks so much easier!!! :guitar:  (yes I do play the bass!)

---

### Post by asuastrophysics on 2011-01-23
Thanks, I'll try that.

---

