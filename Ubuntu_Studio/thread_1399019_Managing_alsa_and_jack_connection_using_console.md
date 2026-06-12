---
title: "Managing alsa and jack connection using console"
date: 2010-02-05
forum: Ubuntu Studio
---

### Post by root.talis on 2010-02-05
Hi!
I am trying to make a script that will manage launching jackd, fluidsynth and connect them properly so I can play my midi keyboard.

Usually I do this:

In first terminal:
jackd -d alsa 

In second terminal:
fluidsynth -l [sf2_name]

Then I launch qjackctl and connect the keyboard's output to the fluidsynth's input, then I connect fluidsynth's left and right outputs to system's playback_1 and playback_2. This is the step I would like to automate. I am sure that there should be a way to make those connections using console utilities.

Thank you.

---

### Post by AutoStatic on 2010-02-05
Hello root.talis,

This tutorial might be helpful: [http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)

It also mentions LASH and LADI which could be of use for your purpose also.

Best,

Jeremy

---

### Post by root.talis on 2010-02-05
Thank you for your reply, AutoStatic.

The article was very helpful and solved the whole problem. It also explains certain things that a newbie needs to know to get started with shell scripts. Thank you very much!

---

