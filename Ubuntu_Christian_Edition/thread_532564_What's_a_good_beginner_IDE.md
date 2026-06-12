---
title: "What's a good beginner IDE?"
date: 2007-08-22
forum: Ubuntu Christian Edition
---

### Post by eric_n_va on 2007-08-22
I'm looking for a good IDE to learn to program gui apps for linux.

I am somewhat of a novice with C and C++. I actually learned basic programming on Redhat in the late 90's. I used vi at the time, but really am looking for a fully funcitonal IDE. I'm open to suggestions.

---

### Post by Nekiruhs on 2007-08-22
Geany:
```

sudo apt-get install geany
```

Glade-3 (GUI designer):
```

sudo apt-get install glade-3
```

Build Essentials (Need to be installed, but GUI-fied by Geany):

```
sudo apt-get install build-essentials

```

---

### Post by eric_n_va on 2007-08-22
Thanks Nekiruhs.  While I'm at it I may as well learn the most suitable language.  Suggestions there?  Python?

---

### Post by Nekiruhs on 2007-08-22
> **eric_n_va said:**
> Thanks Nekiruhs.  While I'm at it I may as well learn the most suitable language.  Suggestions there?  Python?
I would recommend Python. Its clean, readable, garbage-collected (If you did C/C++ you know what I mean), and Memory-managed (C/C++ things). If you use Python, Build Essentials aren't needed but the Python interpreter is (Its installed by default, I believe). Glade works with Python too. ([Guide]("http://laguna.fmedic.unam.mx/~daniel/pygtutorial/pygtutorial/x185.html"))
I can upload some of my programs that use Python, PyGTK, and Glade if your more of the hands-on learner.

---

### Post by Fonon on 2007-08-22
For C and C++, as well as other languges, Geany is great.  I recommend it to everyone.  Use IDLE for Python.

---

### Post by eric_n_va on 2007-08-22
> **Nekiruhs said:**
> I would recommend Python. Its clean, readable, garbage-collected (If you did C/C++ you know what I mean), and Memory-managed (C/C++ things). If you use Python, Build Essentials aren't needed but the Python interpreter is (Its installed by default, I believe). Glade works with Python too. ([Guide]("http://laguna.fmedic.unam.mx/~daniel/pygtutorial/pygtutorial/x185.html"))
I can upload some of my programs that use Python, PyGTK, and Glade if your more of the hands-on learner.

Thanks again!  It's been 8 years or more since I've done any programming.  If you have anything small I could get my feet wet with that would be awesome.  I use XFCE btw...  I'll definitely check out the Glade Overview.

---

### Post by mhancoc7 on 2007-08-23
> **eric_n_va said:**
> I'm looking for a good IDE to learn to program gui apps for linux.

I am somewhat of a novice with C and C++. I actually learned basic programming on Redhat in the late 90's. I used vi at the time, but really am looking for a fully funcitonal IDE. I'm open to suggestions.

If you would like to do some Rapid Application Development you might try Gambas.

Jereme

---

### Post by eric_n_va on 2007-08-23
> **mhancoc7 said:**
> If you would like to do some Rapid Application Development you might try Gambas.
Jereme

I'll check that out too.  Thanks!  Is that what you've used for your CE gui installers like e-sword and IEs 4 Linux?  Those are very clean and professional looking...

---

### Post by mhancoc7 on 2007-08-24
> **eric_n_va said:**
> I'll check that out too.  Thanks!  Is that what you've used for your CE gui installers like e-sword and IEs 4 Linux?  Those are very clean and professional looking...

Yes, let me know if you have any questions.

Thanks, Jereme

---

### Post by eric_n_va on 2007-08-26
Anyone tried Ruby?  I'm leaning towards that...  Just wondering if anyone has used it and how they like it...

---

