---
title: "OneNote crash on copy then paste outside of WINE"
date: 2010-03-22
forum: Wine
---

### Post by univremonster on 2010-03-22
Hi everybody,

I have OneNote up and running fine in WINE.  However, when I select and copy a section of text from OneNote, then try to paste to any program not running in WINE, OneNote crashes.  I get the "Do you want to recover and restart OneNote" error, also somewhat amusingly asking if I want to report the issue to Microsoft.  I'm sure they would be devastated to learn that there are compatibility issues with Linux... *liberal dose of sarcasm*.  

I can paste to other programs in WINE, such as Excel and Word.  I cannot paste to Firefox, OpenOffice, etc.  Any ideas?

---

### Post by asdfoo on 2010-03-22
edit: replied in wrong thread

---

### Post by univremonster on 2010-03-22
asdfoo:  I think maybe you misunderstood my problem, or else I misunderstood your answer.  I am referring to OneNote, part of Microsoft Office.  I'm not attempting to play/save any games.  Also, I don't see any NightKModder reply...

---

### Post by asdfoo on 2010-03-22
you're right. I was replying to a different thread.

Please include which version of Wine you are using.

---

### Post by univremonster on 2010-03-23
dan@dan-laptop:~$ wine --version
wine-1.1.40

---

### Post by asdfoo on 2010-03-23
> **univremonster said:**
> dan@dan-laptop:~$ wine --version
wine-1.1.40

it looks like a known issue

[http://bugs.winehq.org/show_bug.cgi?id=18242](http://bugs.winehq.org/show_bug.cgi?id=18242)

You should register and post a comment to say it's still a problem with 1.1.40.

It looks like you can also compile from source and then post a proper backtrace so that maybe a dev will fix the problem.

If you run into issues doing that or need help I suggest to ask at [http://forum.winehq.org](http://forum.winehq.org)

---

### Post by univremonster on 2010-03-26
Not really "Solved," but marked as such in the conviction that the folks at WINE will figure this one out!

Bug report filed...

---

