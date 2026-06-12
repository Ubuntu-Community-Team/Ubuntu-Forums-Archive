---
title: "Wine Log"
date: 2009-06-09
forum: Wine
---

### Post by ForMar on 2009-06-09
Wine is constantly crashing on me and I cant figure out why, can any one point me in the right direction as to where to look or even where the hell the wine log is?!
(I'm sure this makes a huge difference, I'm using POL, but id be happy with the wine info and I can figure it out from there, saying POL seems to make people less helpful :P)  


Thanks for your time!
Anthony

FIX:
  as of 6-9-09 : the fix is to use wine 1.1.22 with memdumb fix from : [http://bugs.winehq.org/show_bug.cgi?id=18649](http://bugs.winehq.org/show_bug.cgi?id=18649)

---

### Post by NightMKoder on 2009-06-09
Because POL is modified wine, noone really cares enough to look up in what way POL modifies wine for a particular app.

But it would be nice to know exactly what's crashing. Read the before posting sticky on top and give us some information/log. Also make sure you're using the latest wine version 1.1.23

---

### Post by ForMar on 2009-06-09
Well I'm most interested in the location of the log for wine to see if I can figure it out myself, but the problem is while playing the Sims 3, it randomly crashes, for no good reason ( I keep terminal open and get no reason for it closing). After crashing the screen has a very bright white tone to it, which wont go away till after I restart. I do have the latest stable version of wine.

Thanks for your time, 
Anthony

---

### Post by NightMKoder on 2009-06-09
Wine doesn't have a log file (it outputs to console). If you want to save it to a file, you have to pipe it:

wine Sims3.exe 2>&1 | tee winedebug.log

which will create winedebug.log with your output in it.

What you're looking at is: [http://bugs.winehq.org/show_bug.cgi?id=18649](http://bugs.winehq.org/show_bug.cgi?id=18649) . There are two patches you need to apply (yes this is a wine bug) to get it to work pretty well.

---

### Post by ForMar on 2009-06-09
I had the patches applied and look around a bit more I think it is because I have wine version 1.1.23 when I should have 1.1.22, Dont know if I'm right but ill be sure to post back if it fixs the problem, (assuming I can recreate the situation in a timely manner) 

Again Thank you all for your help! 
 I really love the tip about making a "debug" log :)


UPDATE:
   So im having a hard time recreating the situation, but it seems to have fixed, again thanks for the help! Ill post back if there is a change

---

