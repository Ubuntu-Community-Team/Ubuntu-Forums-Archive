---
title: "No Audio in Guitarix."
date: 2016-11-22
forum: Ubuntu Studio
---

### Post by mike215 on 2016-11-22
Hi, new to Ubuntu studio and I'm having trouble with getting any audio signal out from my screen monitors or when I plug in my headphones while using Guitarix. I have a Saffire 6 USB as an interface which I have selected in the Setup menu in JACK. I can see that the signal is at least reaching the amp in Guitarix, I can see the level on the amp. 

I've tried all connections that I can find online, and every combination in between within JACK, but I know I am close since now I see the signal in Guitarix. I've check the ALSA levels with my mixer and everything is up and unmuted. 

I attached a few screenshots, let me know if there is anything I haven't tried. Thank you!

My setup was built by a friend who put Xenial Xerus on it, but it looks like I have Xfce Desktop Environment? I can find more about my hardware, soundcards, etc if that will help.

---

### Post by CrocoDuck on 2016-11-25
Weird. It appears it should be working. Open a terminal and give the output of

```

aplay -l

```

and

```

cat .jackdrc

```

Looks like you have a standard Ubuntu Studio installation which comes, indeed, with XFCE.

---

