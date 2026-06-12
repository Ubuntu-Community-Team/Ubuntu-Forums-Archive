---
title: "gnome partly braindead? (Confessions of a software cowboy)"
date: 2007-02-17
forum: The Cafe
---

### Post by dlbolton on 2007-02-17
Well I have managed to damage gnome. I am currently running edgy and recently did a dist-upgrade. When I start, I see a crash notification and any app that is pygtk based will not start (like quodlibet, listen or gdebi.  otherwise, gnome seems functional.  I can run amarok, evolution and firefox, etc.  Most utilities, like synaptic seem to work fine.

I also have kde and xfce installed. They both seem to work fine; however, these same apps also do not work there.   I have tried making sure that dependencies of the affted apps have been installed (especially python* and anything with gtk in the name).

I would just like to get some opinions on whether I should:
a) continue to try to repair edgy-gnome
b) do a clean install of edgy
c) just do nothing

My current plan is to do a clean install of feisty when it becomes a bit more stable.  I guess that might be in April or so.

---

### Post by bonzodog on 2007-02-18
Right, not much is actually broken for a start - it's just that 2 libraries were updated, and as a result, anything that depends on them doesn't work, as they were compiled/packaged against the older libraries. The 2 Libraries updated were:

Pygtk
Python (Update to 2.5, I believe. This broke ALOT of things in Zenwalk Linux, too.)

Quodlibet uses pygtk to present the gtk front end in the python program. What you will now need to look/wait for is updated versions of the programs concerned.

---

### Post by dlbolton on 2007-02-18
First, thanks for the reply!  I suspected that pygtk and python were broken. I have to say I am a little reluctant to start over with a clean install when so much is working well.

I do have a follow up question. When I go into synaptic it appears that there are several versions of python (2.4, 2.5 and even at least two different versions of 2.4.x).  Is it ok to have more than one version installed? I am not sure how I would manage to keep only one version given that these seem to get install automatically in order to resolve missing dependencies.

Thanks again,

Dave

---

