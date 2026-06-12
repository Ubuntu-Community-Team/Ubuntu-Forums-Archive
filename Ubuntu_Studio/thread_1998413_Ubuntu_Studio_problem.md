---
title: "Ubuntu Studio problem"
date: 2012-06-06
forum: Ubuntu Studio
---

### Post by Never Give Up on 2012-06-06
I have 2 related issues occurring right now and i dont know where else to turn. My first problem is jack control will not start, im getting a generic message stating that jack failed to start as server client. My next problem is that Zynnaddsubfx will not work if i start it after i start hydrogen drum machine, this works both ways, meaning that if i start zynnaddsubfx first hydrogen drum machine will not work, its like its one or the other what is causing this? i am really excited to use it as i just installed everything and got my desktop all set up winderfully now.... any help is greatly appreciated, thanks guys!

---

### Post by Sylos on 2012-06-07
I suspect the reason why you cant use both at the same time is because you are not running the jack server. Jack is a sound server and allows a number of apps to work together through your soundcard. Without jack running I assume that hydrogen and Zyn are both defaulting to alsa which isnt allowing both to work simultaneously.

In order to get jack running could you post the following info:

PC spec
soundcard
Ubuntu version and release
the output of the Qjackctl messages window after jack fails to start.
the ouput of the following commands:
aplay -l
cat /proc/asound/cards

I dont know that much about this but with the above information hopefully someone can help diagnose the problem. 

Cheers

---

