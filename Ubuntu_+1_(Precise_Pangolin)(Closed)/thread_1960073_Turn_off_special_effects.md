---
title: "Turn off special effects"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mmasroorali on 2012-04-16
Previously we could turn off special effects in desktop. This was very handy specially if you had a slow machine or many processor or memory intensive processes are running.


Any suggestions or pointers?

---

### Post by alphacrucis2 on 2012-04-16
> **mmasroorali said:**
> Previously we could turn off special effects in desktop. This was very handy specially if you had a slow machine or many processor or memory intensive processes are running.


Any suggestions or pointers?


Just select a unity 2D session at login.

---

### Post by jerrylamos on 2012-04-17
> **mmasroorali said:**
> Previously we could turn off special effects in desktop. This was very handy specially if you had a slow machine or many processor or memory intensive processes are running.


Any suggestions or pointers?

Sure.  Unity-2D is the first one, Lubuntu is super at getting rid of the "pseudo ipad smartphone" eye candy while having lots of function and efficiency.  I haven't tried Xubuntu lately since on the older but still fast and responsive notebooks like this one, lubuntu is fine.

I'm all about getting things done with my applications.  Apparently Ubuntu development is far more interested in desktop appearance - which doesn't even show when I'm using full screen applications.

Do be aware, with system monitor and Compiz bug failures, with Unity-3D Compiz is busy using up processor cycles even though I'm in full screen internet.  Microsoft and Apple solution and Unity solution: "Buy a faster computer with each major release".

Jerry

---

### Post by thatguruguy on 2012-04-17
> **jerrylamos said:**
> Sure.  Unity-2D is the first one, Lubuntu is super at getting rid of the "pseudo ipad smartphone" eye candy while having lots of function and efficiency.  I haven't tried Xubuntu lately since on the older but still fast and responsive notebooks like this one, lubuntu is fine.

I'm all about getting things done with my applications.  Apparently Ubuntu development is far more interested in desktop appearance - which doesn't even show when I'm using full screen applications.

Do be aware, with system monitor and Compiz bug failures, with Unity-3D Compiz is busy using up processor cycles even though I'm in full screen internet.  Microsoft and Apple solution and Unity solution: "Buy a faster computer with each major release".

Jerry

Would it be at all possible to keep the editorializing to the Testimonials forum, and use this forum to simply answer people's questions directly?  That would be neat.

---

### Post by ubuntu27 on 2012-04-18
> **mmasroorali said:**
> Previously we could turn off special effects in desktop. This was very handy specially if you had a slow machine or many processor or memory intensive processes are running.


Any suggestions or pointers?

You can use Unity 2D, or install Gnome-Panel

```
sudo apt-get install gnome-panel
```


and then login as "Gnome Classic (No effect)"

---

### Post by keithpeter on 2012-04-18
Hello mmasroorali and all

To answer your question: you can't switch off the desktop effects during a session in the same way that you could in the Gnome desktop that came with 10.04.

I think that that old visual effects control worked by using the Metacity window manager for the 'no effects' option. When you selected the 'moderate' or 'full' effects options another window manager called Compiz was loaded up instead. You may remember the way the screen 'flickered' a bit as the windows re-drew themselves when you went from 'no effects' to 'moderate effects'. I think that was the Compiz window manager taking over from Metacity.

A Unity session relies on Compiz all the time. To switch off effects, you have to select the unity2d session when you log in. If you use autologin as I do, you just log out and then change the session to Unity2d and log in again.

As Ubuntu27 has pointed out, you can install more 'sessions' that you can choose at login. The Gnome Classic (no effects) session will look very similar to the old two panel Gnome interface.

@jerrylamos: XFCE4 on this Atom N270 notebook installed from the daily just now (zsynced up to today) is running at around 130Mb on bootup and is quite responsive, a tad lighter than Unity2d but no featherweight. I used to run puredyne.org on my old T42, that used XFCE4 and was really quite fast.

---

### Post by Ghil on 2012-04-18
wouldn't installing CCSM fix the problem?

---

### Post by 3rdalbum on 2012-04-18
> **jerrylamos said:**
> Apparently Ubuntu development is far more interested in desktop appearance - which doesn't even show when I'm using full screen applications.

Unity is designed to mostly get out of the way when using maximised windows - which is one of its benefits.

---

### Post by meborc on 2012-04-19
> **Ghil said:**
> wouldn't installing CCSM fix the problem?

just installing will do nothing ;) you would need to play with the settings

---

