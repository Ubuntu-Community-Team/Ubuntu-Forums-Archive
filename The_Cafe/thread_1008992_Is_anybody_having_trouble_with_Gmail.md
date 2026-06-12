---
title: "Is anybody having trouble with Gmail?"
date: 2008-12-12
forum: The Cafe
---

### Post by s.fox on 2008-12-12
Hi,

I have tried to access Gmail for the last few days on different internet connections on different machines and I can't seem to load Gmail.   I can load it Okay if I choose to load it in basic HTML version.

Anyone else having similar troubles?  It would be nice to know I am not alone :p

-Ash R

---

### Post by howlep on 2008-12-12
no problems here :)

---

### Post by kerry_s on 2008-12-12
works fine for me.

---

### Post by Hume's doona on 2008-12-12
i can access it, i just seem to be getting my emails 12-24 hours late.

---

### Post by howefield on 2008-12-12
Likewise, no issues here pulling into Evolution via IMAP, or going to the site.

Can you load all other web pages correctly ?

---

### Post by s.fox on 2008-12-12
Hmmm.

Well I was able to access it okay on an iMac with a wired connection.  :confused:  

All other pages load fine.  Normally I use wireless internet and all other pages load with no problems.  Its a mystery :confused:

---

### Post by dannytatom on 2008-12-12
Mine did the same earlier, wouldn't load for a long time then asked me to view the "Regular HTML Version."  I f5'd instead, and it loaded the regular version pretty quick.  ;o

---

### Post by spupy on 2008-12-12
Recently it has problems logging me out. I suspect it might have something to do with the Labs features that I enabled.

---

### Post by will1911a1 on 2008-12-12
Haven't had an issue with it.  I checked it this morning actually.

---

### Post by Vadi on 2008-12-12
Loads fine but it's become one buggy email now and it is annoying.

---

### Post by sydbat on 2008-12-12
I haven't had any trouble...just checked it and it loads fine. Do you have anything extra enabled? If so, that might be the cause. Also, I find wireless connections to be significantly slower than wired ones, so that might also be an issue.

---

### Post by m_l17 on 2008-12-12
Working fine here.

---

### Post by Kernel Sanders on 2008-12-12
Gmail FTW! 8)

---

### Post by luispic on 2008-12-14
Yes I'm having trouble as well, it's very odd... Ive been loosing my google talk connection as well... I suspect gmail servers having problems, anyone know where to confirm that? (although I will try to disable all the google labs things I have enabled)

---

### Post by s.fox on 2008-12-14
I don't think its the fact that I am using wifi as other pages load pretty sharpish. 

Thanks for all the replies :)

Ash R

---

### Post by luispic on 2008-12-22
Hey everybody, so I found a solution to that gmail problem, I reduced the size of the MTU to 1400 and it worked, I called my ISP and reported the problem, they imediatly talked to me about changing my ITU but I had to do a bit more research to really modifing windows registry in order for me to change it, since they don't do troubleshooting in linux. But after a while and some tests it worked and gmail stoped giving trouble, later on I looked on how to do it on linux and it was a lot easier:

```
ifconfig <interface for MTU to be canged> MTU 1400
```

ok well I hope it helps anyone... more info on MTU troubles:
[http://help.expedient.com/broadband/mtu.shtml]("http://help.expedient.com/broadband/mtu.shtml")

---

### Post by CrazyArcher on 2008-12-22
When I think about it, some 12 hours ago my Gmail page just refused to work. I tried to log in one more time and then it worked.

---

