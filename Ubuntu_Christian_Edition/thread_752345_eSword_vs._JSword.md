---
title: "eSword vs. JSword"
date: 2008-04-11
forum: Ubuntu Christian Edition
---

### Post by Pursuer on 2008-04-11
Are these two even comparable? I looked at screen shots for both of them, and to my very new-to-the-world-of-linux eyes, they seemed to look similar, but maybe I am missing something.
I do want to learn how to navigate in Ubuntu CE, but if there are easier ways to learn and get it done right, I would also rather save precious time with my family than learning how to do it a long, tedious, difficult way.

If eSword is just way better than JSword, is there an easier way to get it onto my computer and working, than installing through Wine?

---

### Post by retiree on 2008-04-11
It will have to run under WINE and it will have to be tweaked a little to run on Ubuntu. Look at the thread by DAVID and follow his instructions. It took me a while to get it right, but I finally did and it is a good program with a lot of resources. Regards, Clayton

---

### Post by retiree on 2008-04-11
I forgot, but I am talking about E-Sword. I have not been able to get J-Sword to run yet.

---

### Post by david_kt on 2008-04-11
> **Pursuer said:**
> If eSword is just way better than JSword, is there an easier way to get it onto my computer and working, than installing through Wine?

In that case you have to wait for Jeremy to get his laptop back, and wait for him to make the deb program for you to install e-sword. 

Unfortunately I am just a user, not programmer. I am thinking to make a script for easy installation but that would take time as I am new to this area as well. But if you try to follow the instruction I give you before, it would help to increase your knowledge of using linux in general, and wine in particular. That instruction is not for ubuntu ce, but for ubuntu, but it could also been used in any other linux distro running wine.

DK

---

### Post by MonkeeSage on 2008-07-22
> **Pursuer said:**
> Are these two even comparable? I looked at screen shots for both of them, and to my very new-to-the-world-of-linux eyes, they seemed to look similar, but maybe I am missing something.
I do want to learn how to navigate in Ubuntu CE, but if there are easier ways to learn and get it done right, I would also rather save precious time with my family than learning how to do it a long, tedious, difficult way.

If eSword is just way better than JSword, is there an easier way to get it onto my computer and working, than installing through Wine?

In terms of features, they are very similar (JSword uses the SWORD project as a backend, so it supports all the same modules and features like cross-refs., strong's numbers and so on). Jsword has a really ugly default GUI using the Java SWING Metal theme. There is a way to make it use the GTK look and feel, but it's still being worked on, and you'd have to get the source from SVN and compile it to Java bytecode, which a big pain. You'd probably do better using GnomeSword or Bibletime (both are in the respositories), which are, respectively, native GNOME / KDE frontends for the SWORD project.

Ps. It's technically possible to view and dump e-Sword modules with mdbtools and import them as SWORD modules. Someday I may write a program to automatically do that. It wouldn't be too awful hard.

Pss. There's also a really nice new GUI based on the SWORD project, using python and wxWindows. It's called bpbible, but currently it takes [a bit of work]("http://code.google.com/p/bpbible/wiki/RunningBPBible") to get it running. Attached is a screenshot.

---

### Post by pneaveill on 2010-09-01
> **MonkeeSage said:**
> In terms of features, they are very similar (JSword uses the SWORD project as a backend, so it supports all the same modules and features like cross-refs., strong's numbers and so on). Jsword has a really ugly default GUI using the Java SWING Metal theme. There is a way to make it use the GTK look and feel, but it's still being worked on, and you'd have to get the source from SVN and compile it to Java bytecode, which a big pain. You'd probably do better using GnomeSword or Bibletime (both are in the respositories), which are, respectively, native GNOME / KDE frontends for the SWORD project.

Ps. It's technically possible to view and dump e-Sword modules with mdbtools and import them as SWORD modules. Someday I may write a program to automatically do that. It wouldn't be too awful hard.

Have no idea if this thread is still active/alive or not, but am curious if this script was ever written?  Was given about 100 or so e-sword files (as far as I can tell they are legal) and my dream is to batch convert if possible.  Or if someone could provide steps to do so, that would be fantastic.

---

### Post by jonathonblake on 2010-09-02
> **pneaveill said:**
> Have no idea if this thread is still active

Two years since the prior message would be a good indication that it is dead.

>  am curious if this script was ever written? 

A tool chain for converting resources between e-Sword and The Sword Project has been available since at least 2004;

Anybody who creates a tool that directly converts between the two formats is potentially risking either criminal or civil lawsuits for copyright violations. "Contributory copyright infringement", and "conspiracy to violate copyright" are what copyright lawyers representing the publishers have cited the most.

Will a publisher file a lawsuit? I don't know. Publishers much prefer to settle things out of court. But, if they see repeated infringement, they will feel that they have no choice but to file a lawsuit. Three years ago, it was touch and go for e-Sword. A settlement was negotiated.  Publishers were more willing to turn a blind eye to copyright infringements that did not appear to impact on their sales, or distribution rights then, than today. Currently, they aren't quite so willing to turn a blind eye to infringements, when they become aware of them. (There is a direct correlation between releases of *Currently Available e-Sword Resources*, and publishers sending DMCA take down notice, and other legal documents.)

>  Was given about 100 or so e-sword files (as far as I can tell they are legal)

Given any 100 random e-Sword resources, I wouldn't make any claims about whether or not any were being legally distributed, until I had done the copyright clearances for all of them. 

To throw a slight nuance on that:
* Three sites have done the paperwork to obtain the required clearances to distribute the resources they offer. However, format shifting is a violation of the EULA that those resources are distributed under;
* Three sites that have checked the providence of the resources, that one can be fairly confident that the majority (90%+) of the resources they offer are being distributed legally. Their resources usually can be legally format shifted;
* On all other sites that offer e-Sword resource, you're looking at a minimum of 40% of the resources being distributed in violation of copyright law, the original EULA that the resource was distributed under, or both;

jonathon

---

### Post by pneaveill on 2010-09-02
> **jonathonblake said:**
> Two years since the prior message would be a good indication that it is dead.

Guessed that, but hoped someone would contact anyway.  Hopes were honored. Thanks.

> 
A tool chain for converting resources between e-Sword and The Sword Project has been available since at least 2004; Did not know that and could not find it online.

Not wanting to make any money off of the stuff, just use them is all.  Can contact offline iff needed.

---

