---
title: "JACK execute scripts after start up"
date: 2010-04-01
forum: Ubuntu Studio
---

### Post by mdrake36 on 2010-04-01
Newbie here hayoooo!
 
I can enter the Command in to the Execute script after start up field and it works. I can Start Hexter along with Jack. 
 
BUT
 
Hexter doesn't let Jack continue ... the Jack transport is frozen until I close Hexter
 
Basically I have no Idea how to create an acceptable "Execute After start up Script"
I want to Execute like three programs after start up.

---

### Post by AutoStatic on 2010-04-01
Hello mdrake36 how does your startup script look like right now? Maybe you should add an ampersand (&) after the hexter command to let it run in the background:
```
#!/bin/bash

# Start Hexter
/usr/bin/hexter &

# Start dweebeleewop
/usr/bin/dweebeleewop &

# Start shibbedeebang
/usr/bin/shibbedeebang
```

---

### Post by mdrake36 on 2010-04-09
[SIZE=3]You got the flava. Seriously thank you .
Where do you reference all your good info. are there any Studio 64/ubuntu
 articles that helped you? I am thinking about coding a step sequencer in the future and jack has impressed me to the point of actually trying.

Oh and to your question.

I literally just typed the terminal command [/SIZE]jack-dssi-host hexter.so

I think I also need to disable the boot intro sound 
cuz Jack is failing to start automatically

---

### Post by AutoStatic on 2010-04-09
> **mdrake36 said:**
> You got the flava. Seriously thank you .
Where do you reference all your good info. are there any Studio 64/ubuntu
 articles that helped you?Not really. I'm just very fortunate to be able to work with Ubuntu/Linux on a professional basis.

> **mdrake36 said:**
> I am thinking about coding a step sequencer in the future and jack has impressed me to the point of actually trying.I won't stop you! :)

> **mdrake36 said:**
> Oh and to your question.

I literally just typed the terminal command jack-dssi-host hexter.soAh, you ran the dssi plug-in, that should be no problem, just try it with the ampersands.

> **mdrake36 said:**
> I think I also need to disable the boot intro sound 
cuz Jack is failing to start automaticallyYup, that's probably libcanberra blocking JACK.

---

### Post by mdrake36 on 2010-04-09
:guitar:

---

