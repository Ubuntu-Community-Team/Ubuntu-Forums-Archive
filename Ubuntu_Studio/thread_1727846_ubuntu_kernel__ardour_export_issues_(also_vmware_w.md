---
title: "ubuntu kernel / ardour export issues (also vmware with rt kernel result)"
date: 2011-04-13
forum: Ubuntu Studio
---

### Post by ubnewbie2 on 2011-04-13
I started chasing down a problem where Ardour would hang for me, sometimes for minutes, at the end of exporting a simple session to a wav file.  I found some threads about this problem (mostly a couple of years old), and more often than not, the kernel was blamed - sometimes specifically ubuntu.  Well, the problem is/was back - for me anyway.

I was running Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic.  I was afraid to go to a real time kernel because of possible issues with vmware - which I also use on this machine. However, I tried the rt kernel, specifically Ubuntu 10.04.2 LTS, kernel 2.6.31-11-rt.    

This fixed the Ardour export problem for me !! 

Also, VMWare player recompiled itself automatically when next run, and did what it had to to the kernel, and it works too!!  At least so far, more testing needed. 

So, in case this helps someone else - I am posting what happened.

Does anyone know why Ardour/Jack and the generic kernel don't get along properly for exports?

---

