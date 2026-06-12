---
title: "How to get MIDI controller working for dummy"
date: 2012-10-25
forum: Ubuntu Studio
---

### Post by AnUbunter on 2012-10-25
I bought a korg nanopad2 to start my experimentation in the world of producing etc.
Thing is, i have no clue how to make it work on ubuntu, i have studio so i suppose i have all the apllications needed.
I just planned on learning and discovering how to do it myself but have failed on step one :P

typing lsusb on terminal shows thats its connected properly and drivers install good on windows but im not sure it does on ubuntu because nothing pops up or anything

on qjack, it only shows up as an alsa device or whatever it stands for :p

I cant give much info becasue i dont know what to give!

Hope someone can help me step by step to get it working!
Thanks in advance.

BTW, i have a Lenovo Thinkpad X220 and am not sure what the sound card is as of now and i think its neceasary to know :P

---

### Post by CrocoDuck on 2012-10-25
Hi. If you can see your nanopad2 into the ALSA tab probably things are going good. Very simplistically speaking: when using jack you have to connect the programs to each other and to the hardware. Have a try by opening some program, for example hydrogen, and connect the nanopad2 to hydrogen input in the ALSA tab. If the pad sends midi events that hydrogen associates to something then you should hear or see something.

---

