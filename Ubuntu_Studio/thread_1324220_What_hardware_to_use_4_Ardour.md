---
title: "What hardware to use 4 Ardour"
date: 2009-11-12
forum: Ubuntu Studio
---

### Post by milagro on 2009-11-12
Hello I am using Ubuntu Studio 9.10 on a old ADM Athlon 1.04 Ghz with o old SIS SI7012 sound card. When I start Ardour I get the messages  **Ardour could not start Jack** 

1) Your requested audio parameters that are not supported.
2) Jack is running as a other user. 

Do I need other hardware or can I choose a other configuration (if so how to config?)

---

### Post by pepsifx357 on 2009-12-02
I don't know how serious you are about recording or how many channels you need, but I would suggest a better sound card.

As for your hardware problem, I have no clue.  I'm not a genius like some of the people here.  I'm just an audio engineer.

---

### Post by gorgon on 2009-12-02
hi,

get the gui for Jack called qjackctl

```
apt-get install qjackctl
```

if you calibrate the settings there, most importantly Frames/Periods to something big, at least 1024, and then start jack from the qjackctl before starting Ardour, your soundcard will have a lot greater chance of working.

cheers,
g

---

### Post by AutoStatic on 2009-12-02
> **milagro said:**
> SIS SI7012 sound card
Anything will work better than this soundcard. But what are your current JACK settings?

---

