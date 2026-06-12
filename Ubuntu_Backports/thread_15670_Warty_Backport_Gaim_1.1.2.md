---
title: "Warty Backport: Gaim 1.1.2"
date: 2005-02-15
forum: Ubuntu Backports
---

### Post by rufius on 2005-02-15
**Synopsis**
At the request of a user I rebuilt gaim 1.1.2 to also build gaim-encryption in. 

**Backporting Process**
The source archive directly came from Hoary. I was not able to meet the following dependencies, although the package compiled cleanly:

libgnutls11-dev (>= 1.0.16-5) libebook1.2-dev libedata-book1.2-dev libxss-dev libcamel1.2-dev

**Packaging Status:**
i386 -- Staging at revision 37
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
The only bug I've found is that if you attempt to install the gaim-dev package it will tell you that it cannot remove /usr/share/doc/gaim because it doesn't exist. I found the fix was to just create this directory and later on gaim-dev would fix itself. There is no issue caused by this its just a strange bug that I've not had time to track down.

---

### Post by Technoviking on 2005-02-16
I have notice since upgrading to gaim 1.1.2 that my extra icons (that I added via nautilus applications:///Internet) are not showing up under the menu. 

Mike

---

### Post by rufius on 2005-02-16
[QUOTE=Mike Basinger]I have notice since upgrading to gaim 1.1.2 that my extra icons (that I added via nautilus applications:///Internet) are not showing up under the menu. 

Mike[/QUOTE]
 Odd. That didn't happen to me, I'll be interested to see if it arises again (and then some). If it does, I'll just remove the gaim 1.1.2 update and rebuild gaim-encryption for gaim 1.1.2.

---

### Post by Technoviking on 2005-02-16
I have had the same thing happen on two different computers. It is possible it is the libglib2.0 files from the backport.

---

### Post by jdong on 2005-02-16
[QUOTE=Mike Basinger]It is possible it is the libglib2.0 files from the 
backport.[/QUOTE]


Can you downgrade your libglib2.0 to Warty's version and check again?

---

### Post by Technoviking on 2005-02-16
[QUOTE=jdong]Can you downgrade your libglib2.0 to Warty's version and check again?[/QUOTE]
Downgrading libglib2.0-0 and libglib2.0-data did fix the problem.

---

### Post by rufius on 2005-02-16
[QUOTE=Mike Basinger]Downgrading libglib2.0-0 and libglib2.0-data did fix the problem.[/QUOTE]
 I've redone the libglib2.0-0, if either of you would be so kind as to try it out and tell me if its any improvement I'd be greatly appreciative :).

---

### Post by Technoviking on 2005-02-16
Looks like it works now.

Mike

---

### Post by keyshawn on 2005-02-18
Rufius, you're a little late - V1.1.3. was released just yesterday  :-P

---

### Post by rufius on 2005-02-18
[QUOTE=keyshawn]Rufius, you're a little late - V1.1.3. was released just yesterday  :-P[/QUOTE]
 keyshawn - I only backport from whatever is in Hoary when it comes to gaim, so I'm not late, Hoary is ;).

---

### Post by sparkiegeek on 2005-02-25
Is this backport affected by the recent USN - [http://www.ubuntuforums.org/showthread.php?goto=newpost&t=17011](http://www.ubuntuforums.org/showthread.php?goto=newpost&t=17011) ?

---

### Post by jdong on 2005-02-25
Yes -- we are. 1.1.4 fixes all of them.

However, the author claims that these are minor. We'll build updated GAIM's.

---

### Post by pavkonti on 2005-03-02
gaim 1.1.4?

---

### Post by Nano on 2005-03-02
[QUOTE=pavkonti]gaim 1.1.4?[/QUOTE]

Yup, it's the version I have installed and works perfectly.
Now I'm waiting for Gaim-vv ;)

---

### Post by Davo on 2005-03-07
[QUOTE=Nano]Yup, it's the version I have installed and works perfectly.
Now I'm waiting for Gaim-vv ;)[/QUOTE]

Uh, did you get 1.1.4 from the repositries? I might just end up downloading it from the gaim website and using that ...

---

### Post by earobinson on 2005-03-15
[QUOTE=Davo]Uh, did you get 1.1.4 from the repositries? I might just end up downloading it from the gaim website and using that ...[/QUOTE]
 can u post the deb file for gaim 1.1.4 here?

---

### Post by jdong on 2005-03-15
At this point, we are not going to make a 1.1.4 backport for Warty. Hoary is now very much in a usable condition.

---

