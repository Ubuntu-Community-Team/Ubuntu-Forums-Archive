---
title: "Amarok and jack problem--&gt;JACK freezes/ scratching noises"
date: 2011-04-03
forum: Ubuntu Studio
---

### Post by 8ER on 2011-04-03
hi all, sorry for bad english. I have a rather odd problem

I'm running **Ubuntu Studio 10.10** on a hp **presario cq71** and i'm using **Audio Kontrol 1** as audio interface. Everything works fine.

But recently I have  installed **Amarok** and for some reason every time i run** JACK** (not the same time with amarok) it freezes and i have to restart. 


So i **unistalled** amarok and JACK is working again but now i have a different problem:
when i plug Audio Kontrol in i hear some "*scratching*" sounds from the headphones.

Previously I had also installed **Deluge **(i dont know if this affects something)

what should i do? please help

P.S. the audio before amarok installation was crystal clear, and i haven't changed the Jack settings.

***JACK setup***
> 
Parameters: real-time checked
frames: 128
Lattency: 5.8 msec
Sample rate: 44100
Periods/buffer: 2
interface: hw: 1,0 (audio kontrol)
the rest are set to default
[B]
*cat /proc/asound/version*[/B]
> 
Advanced Linux Sound Architecture Driver Version 1.0.23.


---

### Post by 8ER on 2011-04-04
**UPDATE**

ok i think i solve the sound problem by reducing the frames from 128 to 64, but with Amarok unistalled.

Is there a way to install amarok without these problems?

---

### Post by 8ER on 2011-04-08
**SOLUTION**

ok i think i found what the problem is 

in order to install programs such as **amarok**, **skype**, **flash** or **open office** you need to enable the [B][I]Medibuntu repository


[/I][/B]more info and how to in here: 
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-9.04-p3](http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-9.04-p3)

more about Medibuntu here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

if you want to install open office you need to follow this guide:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)
I**mportant**: in order to uninstall open office correctly you must do with **synaptic package manager **

system --> administration --> synaptic package manager

---

### Post by kayosiii on 2011-04-11
You could possibly try running phonon with a different backend...
perhaps Xine rather than GSTreamer.


Hmmm Amarok might be the culprite for breaking firewire for me sometimes on session load. If you are running KDE there is an option to stop certain programs from being loading on session startup I think I might try that.

---

