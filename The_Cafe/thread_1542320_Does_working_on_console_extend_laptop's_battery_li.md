---
title: "Does working on console extend laptop's battery life?"
date: 2010-07-30
forum: The Cafe
---

### Post by mr_hangman on 2010-07-30
Let's say I'm on a journey and want to work on my laptop. The work may include writing, checking e-mails, surfing internet, listening to some music (maybe?). If all of these tasks are run on the console rather than on the GUI (cpu frequencies and other settings should be the same), will the battery last longer?

I haven't tried it in action but I tested with powertop to see the number of wakeups per second (no Watt consumption available on my laptop). Running on GUI at idle causes around 270 wakeups per sec. Then, I logged out and logged in to tty1, checked powertop. The number went down to around 100. Could this number mean significantly longer battery life in practice?

---

### Post by Sam on 2010-07-30
In a word: yes.

---

### Post by McRat on 2010-07-30
CPU, GPU, memory, and HDD all need to run more when doing GUI windowing.  More running == more power.

---

### Post by Legendary_Bibo on 2010-07-30
If you start up Ubuntu normally (with X), and then press ctrl+alt+F2 to go to the console then is it still draining battery from X running?

---

### Post by linux18 on 2010-07-30
not as much, but yes because the screen is darker and that alone will cut battery usage although you should try frequency scaling from the command line that will really cut power usage. I have a command line distro (see sig) if you just need an awesome fast command line system that you can dual boot into.

---

### Post by Dragonbite on 2010-07-30
This sounds like an awesome concept.

I've tossed around the idea of using a CLI only desktop for a really old laptop I have, just to see how well it would work (I did, however, put Ubuntu Studio on it and once it finally booted up it was alright)

---

### Post by forrestcupp on 2010-07-30
What are you going to use to browse the net?

---

### Post by Queue29 on 2010-07-30
You won't notice the difference.

It will draw only *ever so slightly* less power when you don't have to render windows and animations, but realistically, your computer is going to be doing almost just as much for your console programs as for your GUI programs.

Dimming the display would be by far the best power saving technique, along with not using Flash, having it suspend after 1 minute of non usage, hibernate after 5 minutes of non usage, etc. 

> not as much, but yes because the screen is darker and that alone will cut battery usage although you should try frequency scaling from the command line that will really cut power usage
The colors that your LCD display make no difference to power consumption.

---

### Post by mamamia88 on 2010-07-30
if you got rid of the gui completely i bet you would save a bunch of battery.  seriously doubt it takes much juice for scrolling black amd white text

---

### Post by mr_hangman on 2010-07-30
Thanks for all of your opinions. 

> **Queue29 said:**
> You won't notice the difference.

It will draw only *ever so slightly* less power when you don't have to render windows and animations, but realistically, your computer is going to be doing almost just as much for your console programs as for your GUI programs.

I think that could be the case. I'm gonna compare these two methods to get some concrete results. 
And, you're right, black screen on LCD consumes more energy than white screen - [http://www.scientificamerican.com/article.cfm?id=fact-or-fiction-black-is](http://www.scientificamerican.com/article.cfm?id=fact-or-fiction-black-is)

> **forrestcupp said:**
> What are you going to use to browse the net?

You can use w3m for browsing. Other alternatives can be found here - [http://ubuntuforums.org/showthread.php?t=1540597](http://ubuntuforums.org/showthread.php?t=1540597).

---

### Post by Legendary_Bibo on 2010-07-30
On a side note, is it possible to change the colors of the console? I would like Blaring Red on a yellow background. So that if someone on my computer accidentally gets to it I want them to know that they did something they weren't supposed to be doing.

---

