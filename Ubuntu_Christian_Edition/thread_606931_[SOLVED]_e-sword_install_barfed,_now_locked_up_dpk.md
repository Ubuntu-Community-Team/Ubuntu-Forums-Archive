---
title: "[SOLVED] e-sword install barfed, now locked up dpkg"
date: 2007-11-08
forum: Ubuntu Christian Edition
---

### Post by mholdeman on 2007-11-08
I was setting up my 2nd computer (Wife's) with Ubuntu CE and trying to install e-sword. It gave a couple of errors then seemed to work. It works and runs fine, modules manager works too, but now when I try and run synaptic, apt-get, dpkg or anything to maintain the system I get an error stating that the package e-sword-ubuntu is in a terrible state, needs reinstalling but cant locate a package?

(OK not the exact language as I'm at work now)
Anyway I cant do anything with it, I have tried all I know. 
dpgk --configure -a yeilds the same.

Anyone have a solution?

Thanks in advance.

Mike

---

### Post by Prospero2006 on 2007-11-08
try 
```
 
apt-get -f install

```

Also, 
/var/lib/dpkg/status is a text file that controls what dpkg knows about each installed file. You can delete the bad package from the file and the error will go away.

---

### Post by mholdeman on 2007-11-23
That worked,Thanks.

I know I should have known that already!

Mike

---

### Post by carlinuxlearner on 2007-11-24
HOLD ON!!! How did you install "e-sword"??? I used WINE and that didn't work at all!! I would LOVE to use e-sword but can't get it working.

C@RL

EDIT:: 
Never mind, I googled it and found a way!

---

### Post by ke4ke on 2007-12-29
Many thanks to those who made e-sword work in Feisty! Now we have newer versions of wine and Gutsy. e-sword no longer works even on a fresh install of Feisty. Is there any work being done to update this?

Hopefully,

Tim

---

### Post by bhavard on 2007-12-29
If there are any still monitoring this post, I, too , and having trouble installing E-sword under ver. 7.0X. I have done the upgrades to modules which automatically appeared when the install was first completed. 
I could not get E-sword to install by using the GUI, but it did using Wine. However, it would not recognize the lone Bible file. Now, no other modules will install period.
Bill

---

### Post by happypup on 2007-12-30
I am looking how to install to gutsy also it won't even work on a fresh install of ce ?  This is the only program I really need besides firefox :)

any links or pointers to get the deb package working on gutsy?

---

