---
title: "Monitor Switcher Key not working on gazp6 running 11.04"
date: 2011-10-17
forum: System76 Support
---

### Post by dspurloc on 2011-10-17
[COLOR=black][FONT=Verdana]Has anyone ever gotten the Monitor Switcher key (FN+F7) to work on a Gazelle Professional ( gazp6 )? For the life of me I can't figure why it's not working and I've searched everywhere for an answer. Any help provided would be greatly appreciated.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I need to give a presentation and would hate to have to borrow someone else's machine.[/FONT][/COLOR]

---

### Post by chriscross93 on 2011-10-17
> **dspurloc said:**
> [COLOR=black][FONT=Verdana]Has anyone ever gotten the Monitor Switcher key (FN+F7) to work on a Gazelle Professional ( gazp6 )? For the life of me I can't figure why it's not working and I've searched everywhere for an answer. Any help provided would be greatly appreciated.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I need to give a presentation and would hate to have to borrow someone else's machine.[/FONT][/COLOR]

There are a lot of us having dual monitor / GDM issues in general.  You are by no means alone, but unfortunately nobody seems to have a answer either.  Keep an eye on the other threads, hopefully we will have a solution soon.

EDIT: I have a workaround.  It doesn't help your monitor key issues, but at least you will be able to enable the external monitor.
[http://ubuntuforums.org/showthread.php?t=1863459](http://ubuntuforums.org/showthread.php?t=1863459)

---

### Post by isantop on 2011-10-18
The Nvidia proprietary driver breaks the Fn+F7 hotkey, and prevents it from working properly. We recommend using the Nvidia configuration tool instead.

---

### Post by dspurloc on 2011-11-05
"We recommend using the Nvidia configuration tool instead."



I went that route and could only figure out how to extend the laptop's desktop to the external monitor/projector (at a different resolution btw- a real mess). I was never able to make a mirror of the laptop's desktop -critical for a presentation. Any help you can provide would be greatly appreciated so I am able to complete this task.

---

### Post by isantop on 2011-11-08
Once you have the External Monitor set up in Nvidia settings, you can drag the external monitor on top of the built-in display. Make sure the monitors are both set to the same resolution, then hit apply. This will clone the two monitors. I've included two images that should help show what I mean.

---

### Post by dspurloc on 2011-12-09
Thank you for the advice- it's not the most ideal solution but it does fix the problem- Thank you

---

### Post by mgolden on 2011-12-12
You might also try using the nouveau driver, especially if you don't need to hibernate or suspend.

See here:

[http://www.knowledge76.com/index.php/Using_An_External_Monitor_On_A_System76_Laptop_With_an_nVidia_Graphics_Card](http://www.knowledge76.com/index.php/Using_An_External_Monitor_On_A_System76_Laptop_With_an_nVidia_Graphics_Card)

---

