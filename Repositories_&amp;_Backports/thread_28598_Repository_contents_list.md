---
title: "Repository contents list"
date: 2005-04-20
forum: Repositories &amp; Backports
---

### Post by fishbone on 2005-04-20
Apologies if this question has been asked in the FAQ before, but I saw a link somewhere in a Components section that said a list of what packages are contained in each repository was being worked on - is this true ? 

I am trying to install webmin  & shorewall packages on Hoary 5.4 using apt-get (No X so I'm not using the GUI ver of apt) - are there security update supported vers of these in the main repo or am I better grabbing source tarballs ??

---

### Post by mendicant on 2005-04-20
The typical way to check is to use aptitude show:

% aptitude show webmin
Package: webmin
State: not installed
Version: 1.180-2
Priority: optional
Section: universe/admin
...

% aptitude show shorewall
...
Section: net

So shorewall is in main, but webmin is in universe.

---

### Post by fishbone on 2005-04-21
Cool ! well that was easy - thank you

---

### Post by mendicant on 2005-04-21
By the way, I'm sure synaptic has something for this as well, if you're into using the GUI.  I don't use it, though, so I couldn't tell you what to do there.

---

