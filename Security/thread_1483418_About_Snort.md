---
title: "About Snort"
date: 2010-05-14
forum: Security
---

### Post by EftekasatMasreya on 2010-05-14
Hi all 
I'm an graduate student and I have a graduation project :D :D
IDS :S :S using snort-mysql and base with SAM web eddittion
So, I have a question about snort because I want to make a test i my project by attacking another PC using Snort 
But I didn't Know where I can get Snort in Ubuntu
can help me ??
and THX

---

### Post by lisati on 2010-05-14
I edited your post to show that you are talking about "[snort]("http://en.wikipedia.org/wiki/Snort_%28software%29")", not "[snot]("http://en.wikipedia.org/wiki/Snot")".

We don't usually do homework for people here, but can provide hints if you are stuck. We also discourage breaking into other people's computers.

---

### Post by EftekasatMasreya on 2010-05-14
Mr. Lisati I talked about SNOT not SNORT
I just want know where are can Download SNOT for Ubuntu :D
to make my own test 
Are you Understand me??

---

### Post by OpSecShellshock on 2010-05-14
SAM stands for Snort Activity Monitor, and BASE is a graphic viewer for snort events, so it seems to me that in context the edit was correct. Can't provide all the answers, but I'll say it's certainly an interesting choice of vectors.

---

### Post by uRock on 2010-05-14
In a terminal enter, ```
sudo apt-get install snort
```

---

### Post by EftekasatMasreya on 2010-05-14
Guys ... I know Snort
I talked about Snot
It's a program for attacking used to test Snort :D
my question is how to install SNOT (not snort) in Ubuntu
:D :D

---

### Post by OpSecShellshock on 2010-05-14
In that case, all you have to do is download the source code from somewhere and compile it. Mind where you get it from, though. There's free as in speech, free as in beer, and free as in backdoored.

---

### Post by uRock on 2010-05-14
If it isn't installed in BackTrack Linux, then I wouldn't trust it. BackTrack is a penetration testing operating system, which is built off of ubuntu. You may wanna check that out.

---

### Post by lisati on 2010-05-14
> **EftekasatMasreya said:**
> Guys ... I know Snort
I talked about Snot
It's a program for attacking used to test Snort :D
my question is how to install SNOT (not snort) in Ubuntu
:D :D

My apologies: you referred to snort-mysql in your original question, hence my confusion.

---

### Post by Kinstonian on 2010-05-14
Snot and Stick are pretty ancient now.

> Q: I've heard IDSes are vulnerable to noise generators like "Stick" and "Snot", is snort vulnerable ?

A: It is now pssible to defeat these kids of noise generators with
   the stream4 preprocessor.  Even without this enabled snort will 
   weather the alert storm without falling over or losing a lot of 
   alerts due to its highly optimized nature... and using these
   kinds of gimmicks hardly qualifies as executing a stealthy attack...


[http://www.tux.org/~karl/SNORT-FAQ-v1.8.1.html#1.9](http://www.tux.org/~karl/SNORT-FAQ-v1.8.1.html#1.9)

---

### Post by OpSecShellshock on 2010-05-14
> **Kinstonian said:**
> Snot and Stick are pretty ancient now.



[http://www.tux.org/~karl/SNORT-FAQ-v1.8.1.html#1.9]("http://www.tux.org/%7Ekarl/SNORT-FAQ-v1.8.1.html#1.9")

True. If Snort is deployed correctly and used well, most of the noise won't touch the sensor, a lot of it won't get tagged or generate events at all, and the rest will lay the payloads open for examination and response. And honestly, for a test case this doesn't make much sense since the tester is both configuring the Snort deployment and running the testing tools.

---

### Post by EftekasatMasreya on 2010-05-15
Never mind mr. lisati
Thx all

---

