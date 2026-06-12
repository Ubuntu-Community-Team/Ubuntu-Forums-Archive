---
title: "This software wasn't meant for a nuclear facility...."
date: 2007-01-07
forum: The Cafe
---

### Post by jdong on 2007-01-07
[http://www.google.ca/search?q=You+acknowledge+that+software+is+not+designed%2C+licensed+or+intended+for+use+in+the+design%2C+construction%2C+operation+or+maintenance+of+any+nuclear+facility.&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.ca/search?q=You+acknowledge+that+software+is+not+designed%2C+licensed+or+intended+for+use+in+the+design%2C+construction%2C+operation+or+maintenance+of+any+nuclear+facility.&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a)

While reading the Java license, I saw a pretty amusing line that reads like:
> 
You acknowledge that Licensed Software is not designed or intended for use in the design, construction, operation or maintenance of any nuclear facility.


Googling, it seems like a lot of software carry that warning. Does anyone have a good explanation of why this is necessary?


UPDATE: In IRC, crimsun stated that it's because Java isn't RT-capable in its default incarnation. Then again, a lot of software isn't. Does my defragmenter script need to warn that it's not meant to be used in a nuclear facility?

---

### Post by d3v1ant_0n3 on 2007-01-07
I'm guessing the warning is there because the software stability standards for nuclear facilities have to be that bit higher than usual...

Last thing you'd need would be an app locking up an important system:???:

---

### Post by Bloodfen Razormaw on 2007-01-07
It is a legal liability issue.  Nuclear reactors, life support machines, air traffic control, and other situations where software bugs can mean death are a potential source of lawsuits.  By putting statements like that in the license the legal liability for bugs in the software that leads to death falls on the user and not the developer.

---

### Post by jdong on 2007-01-07
I would expect the no warranty catch-all to cover most of that. The fact that it specifically referenced nuclear facilities instead of the other prominent life-or-death mission critical use-cases made me think there was a more specific story behind this warning :)

---

### Post by Polygon on 2007-01-07
what does "rt-capable" mean?

and there must be a reason why it speicifies only nuclear facilites...

and i guess thats why most software licences say that "by using this software you assume all liability for it , use it at your own risk, "etc etc

---

### Post by Sunnz on 2007-01-07
Realtime Capable?

---

### Post by graigsmith on 2007-01-07
Because neuclear reactors need 100% uptime, and  realtime capability. or rt capabable.

You dont run any other software on the computer you are operating a nuclear reactor because.  system crash could be catastrophic.  You don't want to have to wait to lower the rods into a cooling solution because the computer is rebooting, or running some other noncritical piece of code.   I mean, you have a neuclear accident if the rods melt or explode or something.  

you wouldn't use java, just like you wouldn,t use windows 98, or xp.

---

### Post by Sunnz on 2007-01-07
I think they have backup computers too in case the only software that is running does crash...

Well, from what I have been told, in aircrafts they have 3 computers in different architectures (something like SPARC/PPC/x86) in case the hardware chip itself has design flaws...

---

