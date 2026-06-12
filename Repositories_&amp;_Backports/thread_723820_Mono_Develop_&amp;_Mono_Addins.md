---
title: "Mono Develop &amp; Mono Addins"
date: 2008-03-13
forum: Repositories &amp; Backports
---

### Post by KuraKai on 2008-03-13
The latest version of Mono Develop is currently 0.19, but the one obtained through the package manager is 0.14. Also there is one at GetDeb that is at 0.16.

Also ontop of that the latest version of Mono Addins is 0.3, while the one given from the package manage is 0.2. The latest one is needed to make and install Mono Develop 0.19.

I have tried to do it manually and I am currently using the latest Ubuntu for AMD64 but it fails to properly configure and make Mono Addins 0.3, since it isn't 100% complete Mono Develop 0.19 won't properly be configured since it stops when it checks for Addins 0.3! I have tried to look for a fix for this and I am having issues, will someone work about on updating the package manger to the latest?

Edit: Note mono is also up to 1.9 right now and if I am looking at it right the one Ubuntu is using is 1.2.4(etc. etc.). Is that also correct? Cause it would be nice to update it, the one given by mono's website works but I am not sure if it 100% safe to update.

---

### Post by JackBak on 2008-03-17
A more thorough search may have yielded,

[http://ubuntuforums.org/showthread.php?t=701830](http://ubuntuforums.org/showthread.php?t=701830)

Hope that helps, note that over the weekend the Mono team released the official monodevelop 1.0. What I gave you is pretty darn close though.

Have fun.

---

### Post by KuraKai on 2008-03-17
Yes I actually did find that site in a google search, but like I stated this is for an AMD 64 bit processor and the files located there are I386. So by default it won't even let me install them, and trust me I already tried it before hand.

---

### Post by JackBak on 2008-03-18
Sorry, I read AMD64 and thought only of the processor. I purposely steer clear of the bleeding edge when I'm in the middle of projects (not to say that using the latest bleeding edge from mono isn't real close to the edge but I can keep things to a minimum).

Hopefully the Hardy release will have the full MD 1.0 and mono 1.2.6 incorporated in it.

---

### Post by KuraKai on 2008-03-21
Is there any dates on when Hardy might be released? Or is there a way to get Mono Addins to compile properly cause that is where I am having the issues, Mono Develop won't let me get past the part where it checks for it. I have tried ./configure ; make ; sudo make install , and it looks like it installed properly but apparantly not. I will go re-get the source packages so that I can get the output.

---

