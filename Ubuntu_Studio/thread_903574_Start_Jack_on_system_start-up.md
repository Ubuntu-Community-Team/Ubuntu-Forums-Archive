---
title: "Start Jack on system start-up"
date: 2008-08-28
forum: Ubuntu Studio
---

### Post by alecz20 on 2008-08-28
I just installed Ubuntustudio, I installed the firmware for Echoaudio GINA3G, and I can only have sound from multiple sources if I use Jack.

The problem is that only a few applications start the Jack server on their launch (Ardour), but other applications just complain Jack isn started (Audacious).

What I want is for the jack server to start automatically when I boot up the machine.

This system will be for my brother, and he wants to create music easily, not fiddle with settings.

How can I have jack start up on system boot?


Thanks

---

### Post by markbuntu on 2008-08-28
You can use System/Preferences/Session/Startup Programs/Add to add a jack startup. 

 In the Applications/Sound and Video menu right click on the jack control icon and click properties. Just copy the Name and Command from the jack control launcher to the Add boxes.

Then use the jack control/setup to start jack automatically. 

In jack Control/setup/Misc check the box "Start Jack server on application startup"

It took longer to write this than it will take you to do it.

---

### Post by Stochastic on 2008-08-28
If you would like jack to start behind the scenes, it's entirely possible to merely run jackd (with the appropriate device flags & options) rather than starting qjackctl.  The upside to this is that there's less clutter on your workspace; the downside to this is that you can't readily monitor any jack errors.
If you go with that setup, I'd recommend patchage as your patchbay - it can save its settings and has midi and audio all on the same screen.  You can even start it right away too.

---

### Post by alecz20 on 2008-08-29
> **markbuntu said:**
> You can use System/Preferences/Session/Startup Programs/Add to add a jack startup. 

 In the Applications/Sound and Video menu right click on the jack control icon and click properties. Just copy the Name and Command from the jack control launcher to the Add boxes.


This is what I was looking for. Simple, but I am still learning. I will try this tomorrow.

> **Stochastic said:**
> If you would like jack to start behind the scenes, it's entirely possible to merely run jackd (with the appropriate device flags & options) rather than starting qjackctl.


How do I find out the flags and options?

> **Stochastic said:**
> 
If you go with that setup, I'd recommend patchage as your patchbay - it can save its settings and has midi and audio all on the same screen.  You can even start it right away too.

This sounds interesing... I have to see what "patchage is all about. I am not that interested in music production, so I haven't heard of all these things before.

Thanks for the help guys!

---

### Post by Stochastic on 2008-08-30
> **alecz20 said:**
> How do I find out the flags and options?

Best method is to get things working with qjackctl, then copy those settings to your startup jackd command.  You can get the listing of flags for jackd by doing ```
jackd --help
or
jackd -dalsa --help
```
I'm going to assume that you have another soundcard on your computer, so one of the most important flags will be the hardware designation flag for the alsa driver.  This will go after '-dalsa' and will be something like '-dhw:1' (without the quotes).  It may just be easier for you to use qjackctl if you're a beginner.

---

