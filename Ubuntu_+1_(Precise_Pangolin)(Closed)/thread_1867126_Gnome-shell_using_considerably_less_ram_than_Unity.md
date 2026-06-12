---
title: "Gnome-shell using considerably less ram than Unity"
date: 2011-10-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2011-10-22
I have 2 PP installs.
The first is using gnome-shell (no ricotz.ppa at the moment) and the second is using unity.
The second installation indicates that unity uses much more ram than gnome-shell - up to 200MB more.
It also seems to be the case that both systems seem to ramp up the amount of ram being used (as displayed by conky) even when at idle.
Unity is the worst offender. After about one hour's use the ram use has jumped up to 700-800MB at idle. It seems compiz is the culprit.
Gnome-shell will only have increased to 500 - 600MB in that time.

Is anyone else seeing these types of figures? 
Is it memory leakage or normal-ish ram usage?

---

### Post by masgeeks on 2011-10-22
I noticed how much snappier gnome shell was over unity.

In 11.104, unity seemed fast, but in 11.10 it was a dog and quirky so I tried gnome shell and it rocks...!!!  :)

---

### Post by dino99 on 2011-10-22
you seems so unskilled and dont understand what unity needs for working. Its the price for all that eye candy stuff (and useless).

---

### Post by ventrical on 2011-10-22
> **Quackers said:**
> I have 2 PP installs.
The first is using gnome-shell (no ricotz.ppa at the moment) and the second is using unity.
The second installation indicates that unity uses much more ram than gnome-shell - up to 200MB more.
It also seems to be the case that both systems seem to ramp up the amount of ram being used (as displayed by conky) even when at idle.
Unity is the worst offender. After about one hour's use the ram use has jumped up to 700-800MB at idle. It seems compiz is the culprit.
Gnome-shell will only have increased to 500 - 600MB in that time.

Is anyone else seeing these types of figures? 
Is it memory leakage or normal-ish ram usage?

  All racked up , I got about 12 MB using unity and my PC has been on most of the day.

 and I agree with you .. somthing seriously wrong with compiz core and ccsm... I said this 6 weeks ago during alpha beta .. tried to point out the hooks .. and nothing of any permanence got done  about it..

---

### Post by Quackers on 2011-10-22
> **dino99 said:**
> you seems so unskilled and dont understand what unity needs for working. Its the price for all that eye candy stuff (and useless).

I know I've got compiz running, but honestly no eye candy - yet ;)  :)
Having said that, I like eye candy :-) On modern machines there is plenty of spare resources as a rule. Why save it? :)

---

### Post by jerrylamos on 2011-10-22
> **Quackers said:**
> I know I've got compiz running, but honestly no eye candy - yet ;)  :)
Having said that, I like eye candy :-) On modern machines there is plenty of spare resources as a rule. Why save it? :)

Unity-2D has a certain amount of eye candy.  Much less fuzzy out of focus borders & windows, but some.

No Compiz at all.  Period.  None.  Even on my fastest pc's I want all the cycles available to internet video etc. and since I'm usually full screen applications I don't see anything that Compiz is doing even as it churns away in the background - and nothing it's doing is even visible.  Useless pc cycles.

Jerry

---

### Post by cariboo on 2011-10-22
I seem to be using about 200MiB less ram in Precise, than I was in Oneiric, I haven't tried gnome-shell yet though.

---

### Post by VinDSL on 2011-10-24
> **Quackers said:**
> [...] unity uses much more ram than gnome-shell - up to 200MB more.

Unity is the worst offender. After about one hour's use the ram use has jumped up to 700-800MB at idle.[...]

Gnome-shell will only have increased to 500 - 600MB in that time.

Is anyone else seeing these types of figures?

> **cariboo907 said:**
> I seem to be using about 200MiB less ram in Precise, than I was in Oneiric [...]
True, on all accounts, in my experience.  :)

I just logged out of 10-hour session in Gnome-Shell.

After 10 hours, GS was only using 375Mib resident / 200MiB swap @ idle.  

Under the same conditions, Unity would have been around 500MiB resident / 250Mib swap.

UbuPP pre-alpha 1 is using about 150Mib less RAM @ boot than UbuOO, but...

UbuPP Unity RAM usage seems to be growing during the season.

Might be mem leaks.  Sort of *feels* that way, but I wouldn't swear to it, without watching HTOP for a few days.  ;)

---

### Post by ventrical on 2011-10-24
I have OS,Unity 3D, compiz settings and Cairo doc only grabbing 380MBs<summ>. Precise is a lot faster and more memory efficient.<kernel>

---

### Post by ventrical on 2011-10-24
I take it back I guess. I jsut had a major crash in Precise with RC kernel.  Black Screenshots of death , freeze ups , etc....gobbled up most of sdram.., cpus at 100%!!

  I am going to try  to step back to the previous kernel and see i fi can recover those screenshots.

---

### Post by effenberg0x0 on 2011-10-24
In my case it was v86d. 2 CPUs were 100% with it. Booting with previous RC didn't produce this result.

---

### Post by Quackers on 2011-10-26
Deleted - wrong thread :-)

---

### Post by cariboo on 2011-10-27
I finally got around to checking ram usage in both gnome-shell and unity. On startup on my system both interfaces use about 700MiB (705MiB in gnome shell and 704MiB for unity to be exact). After running unity for about 7 hours unity is using 765MiB, so it looks like there is some work being done on memory leaks

---

### Post by lucazade on 2011-10-27
Both gshell and unity3d eat too much mem.. my minimal installation with unity-2d is about 150mb at startup.

---

### Post by cariboo on 2011-10-27
It really doesn't matter what interface you are using, it seems that Ubuntu uses ram depending on system specifications more than anything else. On my current system ( X2 240 AMD, 2GiB ram GeForce 210) free -m looks like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2003       1716        286          0         76        719
-/+ buffers/cache:        920       1082
Swap:         1999         15       1984
```

It seems ram usage took a fairly large jump since my last post. I'm also using my media center pc to watch a movie while I'm typing this, it runs an atom 230 with 1GiB ram and an nVidia 6150LT graphics, with XBMC on top of natty, ram usage looks like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:           991        974         16          0         60        712
-/+ buffers/cache:        201        790
Swap:         2996          0       2996
```

---

### Post by Quackers on 2011-10-27
I just restarted my GS install and after startup it used 275MB. This quickly climbed a few MB and on opening Firefox it's now running at 376MB.
I'll try with Unity later, but I'm confident it will be using about 200MB more in the same circumstances.
Thanks for the info people :-)

---

