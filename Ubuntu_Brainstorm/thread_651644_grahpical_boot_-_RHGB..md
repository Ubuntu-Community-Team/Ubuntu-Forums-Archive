---
title: "grahpical boot - RHGB."
date: 2007-12-27
forum: Ubuntu Brainstorm
---

### Post by puccaso on 2007-12-27
get RHGB installed on ubuntu

i am seeing posts about getting fortunes printed on screen, or replace usplash. 


if we got rhgb installed on boot up - it would knock the socks of splashy, usplash gensplash and all that nonsense.. 

and im sure, eventully something could be built into it - so tomboy todo lists/evolution calender could be shown on boot up

---

### Post by smartboyathome on 2007-12-28
What is RHGB, and does it require patches to the kernel? If so, I would say splashy is still the best bet (since we don't want people who have to recompile their kernel to have more trouble).

---

### Post by puccaso on 2007-12-28
rhgb is the redhatgraphicalboot.

it doesnt just start grahpics at boot time - it starts XWINDOWS at boottime..

your mouse and all grahpics beauty like opengl etc works at boot time.

---

### Post by smartboyathome on 2007-12-28
> **puccaso said:**
> rhgb is the redhatgraphicalboot.

it doesnt just start grahpics at boot time - it starts XWINDOWS at boottime..

your mouse and all grahpics beauty like opengl etc works at boot time.

That would make me think it slows down boot, but do you have experience with it?

---

### Post by foerdi on 2007-12-28
is it default in fedora?

system requirements?

opengl at boot time sounds nice

EDIT:
something like this? [http://www.youtube.com/watch?v=_Ncm2aKGCzU](http://www.youtube.com/watch?v=_Ncm2aKGCzU)

---

### Post by puccaso on 2007-12-28
yes, thats exactly it.


thats gtk running there, 
you could have your volume control, there too

---

### Post by el_itur on 2007-12-28
It has some flikler here and there but looks cool in did.
[this one]("http://jronnholm.blogspot.com/2007/06/on-boot-splash-solutions.html") is a great article on this one with comparison and all

---

### Post by gnomeuser on 2007-12-31
> **el_itur said:**
> It has some flikler here and there but looks cool in did.
[this one]("http://jronnholm.blogspot.com/2007/06/on-boot-splash-solutions.html") is a great article on this one with comparison and all

Please note that this article looks at things from the prespective of the user. It totally ignores issues like modesetting (something splashy' reliance on directfb makes ******* atrociously hard to get right). Why is this important to note.. well since it makes suspend and resume really hard to get right.

Right now there is work being done to get modesetting into the kernel which will make all that easier (and a bunch of other really cool things). The technically best solution right now is probably rhgb, especially once the modesetting work is completed as we no longer have to rely on a second X server.

---

