---
title: "Does anyone know about how to fix Counter Strike Source on Ubuntu 9.04 Jaunty"
date: 2009-05-06
forum: Wine
---

### Post by Snyper450 on 2009-05-06
:P                                            I installed Jaunty for a test to see what the new distro was like and i found that ppl was able to play CSS on 8.10 with wine but 9.04 seem to break it anyone have a idea or HAVE fixxed it and has proof coz i play CSS a lot and i would liek to know for sure it will work??:guitar:

And can an admin plz delete the post of this that is in gaming and leasure did not see the sticky post about wine sorry

---

### Post by NightMKoder on 2009-05-06
A couple of things:
1) Punctuation makes reading your message easier. Use it.
2) Have you followed the howto from appdb? [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)
3) Make sure you disabled desktop effects
4) If all else fails, post the console, and video card/driver and we might be able to help you. (If you have intel/ati graphics - good chance it wont work)

---

### Post by Snyper450 on 2009-05-06
Well sorry about the Punctuation :-?

and i have Nvidia but how do you get the console?

and cant find the instructions but installed it like you do install wine then steam then though steam download CSS

---

### Post by NightMKoder on 2009-05-06
There's a section that says HOWTO on that page.

To get terminal output - open a terminal, and type something like:

```

cd ~/.wine/drive_c/Program\ Files/Steam && wine steam -applaunch 240

```

Assuming you installed steam in the default location.

Did disabling desktop effects help?

---

### Post by Snyper450 on 2009-05-06
All it says "Sorry this version of steam is not supported on this operating system" and yes tried disabling visual effects dint work:(

---

### Post by NightMKoder on 2009-05-06
open winecfg and check what operating system wine is set to. should be xp.

---

### Post by Snyper450 on 2009-05-07
Yep its deffo XP :( its weird maybe WineHQ need to make an update for Jaunty because the new distro seem to have a few bugs :( but im sure it will all be fixxed soon its not like windows when they say soon you would eb waitign till next year :o thanks for the help btw:guitar:

---

