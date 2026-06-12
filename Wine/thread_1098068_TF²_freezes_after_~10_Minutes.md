---
title: "TF² freezes after ~10 Minutes"
date: 2009-03-16
forum: Wine
---

### Post by illmatic on 2009-03-16
Hey guys,

I have Problems with wine and Team Fortress2.
I'm running on ubuntu 8.10 64 bit
ati driver 9.1
wine 1.17
and a ati x1900xt

Actually everything works fine but only for about 5-10 minutes.
After That period of time the game simply freezes.
I tried to disable the in game community and to 
Delete the textwindow_temp.html file and make a new one with only read access.

The wered thing is, that if i play music in the background the musik goes on even if tf2 freezes, but i cant close tf² so i have to hard- restart .
I read that there were some of you with the same problem, but i could hardly find any solution.

I hope that someone knows more :)
regards,
Illmatic

EDIT
I just tried to start Counter Strike Source, and like in TF² everything works for some minutes after it freezes,
In CS:S it's exactly the same problem like it is in tf²

---

### Post by illmatic on 2009-03-17
up 
None of you with any idea?

---

### Post by regor210 on 2009-03-17
You could try disabling your screen-saver.

---

### Post by illmatic on 2009-03-17
> **regor210 said:**
> You could try disabling your screen-saver.
i just gave it a try, but unfortunatly that didnt help anything :(

Okay here are some other things i tried:
adding the lines from the how 2 to regedit
[http://gaming.gwos.org/doku.php/wine:team_fortress_2](http://gaming.gwos.org/doku.php/wine:team_fortress_2)

And setting -novid +mat_hdr_level 0 -gl als launch option

But I still have the same Problem.

---

### Post by illmatic on 2009-03-18
okay just another update :)
I ran it in the wine window mode and had the terminal on the right so i could see where the problem would be.

Through the whole gametime in the console there was a message :
"fixme: d3d: streamsrc Tweeing is only valid with vertex shaders"
And in the moment of the freeze nothing special happend in the terminal just that message appeared ( like it did the whole time)

If I'm going to install crossover will tf² work ??

EDIT
I forgot to say that I disabled the sound just to watch the result but as you already read it was negative.

---

### Post by illmatic on 2009-04-02
Hm I read in the wineappdb but couldn't finde anything.
Does Team Fortress II run on ubuntu 9.04 or does it run on 8.10 with crossover?
I reinstalled Ubuntu 8.10 and now I'm going to install TF² again and try it with the new 9.3 ati driver, I hope that it'll work

---

### Post by NightMKoder on 2009-04-02
It seems like a purely graphics driver issue. Check to see that you can switch to a text terminal (Ctrl+Alt+F1-6, Ctrl+Alt+F7 to get back to X). If you can't its most likely your video driver acting up. If you don't like restarting the whole machine, try doing Ctrl+Alt+Backspace to restart the X server. Also, you may be able to just press your power button and get the system to shut down nicely.

---

### Post by illmatic on 2009-04-05
Obviously strg+alt+f1-6 works onyl a few times, but not all the time, it's kind of luck if it works or if it doenst :)
It's kind of konfusing.
Actually I reinstalled windows on my other hd and use it  now   just for gaming :)

---

### Post by Private_Ops on 2009-04-05
You seem to be having the same problem I am with CS:S.

It seems to be purely driver related and sadly there really isn't a fix. Though, I'm running the repository drivers and have yet to try the latest.

I've got an ATI 4830 personally.

---

### Post by illmatic on 2009-04-06
I think I can either play cs:s :D.

---

