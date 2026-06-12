---
title: "Syslink to a different folder?"
date: 2010-04-12
forum: Ubuntu One (CLOSED)
---

### Post by tylersontag on 2010-04-12
I have my backup system setup how i like it and i fear change!  I use RSYNC to backup my stuff on 2 boxes on my local network.   I set this up before i had Ubuntu one so the Ubuntu one folder isn't included in this.

So, rather than rework my RSYNC process, id just want to add a symbolic link within my Ubuntu One folder to my /home/user/Documents/ folder.   For those of you shaking your head out there, yes, this in fact does not work.

Can anyone help me set this up?   Or should i just not rock the boat?

---

### Post by sanemanmad on 2010-04-12
Hi... Please be more specific. Can you provide some detail on how you have this setup and what you need to accomplish?

---

### Post by tylersontag on 2010-04-12
Sorry, allow me to elaborate.

I have Ubuntu One installed, it is attempting to sync with my Ubuntu One folder (/home/user/Ubuntu One/)  I would like the sync process to actually use my Documents folder (/home/user/Documents).  While I could copy the contents of Documents into Ubuntu One, to the same end, I would prefer to not alter my existing file structure.

My initial solution was to create a symbolic link within Ubuntu One to point at the contents of Documents, however it seems my current implementation of Ubuntu One will not dive into symbolic links.  Is there anyway to force Ubuntu One to exhibit this behavior?

---

### Post by joshuahoover on 2010-04-12
> **tylersontag said:**
> Sorry, allow me to elaborate.

I have Ubuntu One installed, it is attempting to sync with my Ubuntu One folder (/home/user/Ubuntu One/)  I would like the sync process to actually use my Documents folder (/home/user/Documents).  While I could copy the contents of Documents into Ubuntu One, to the same end, I would prefer to not alter my existing file structure.

My initial solution was to create a symbolic link within Ubuntu One to point at the contents of Documents, however it seems my current implementation of Ubuntu One will not dive into symbolic links.  Is there anyway to force Ubuntu One to exhibit this behavior?

In Lucid (and our beta PPA), you can choose which folders you want to synchronize. So, in your example, you can tell Ubuntu One you want to synchronize ~/Documents by right-clicking on the folder in Nautilus and selecting "Synchronize on Ubuntu One". 

Thank you,

Joshua

---

### Post by tylersontag on 2010-04-23
There you go, the ubuntu team is one step ahead of my whining :-)

---

### Post by joshuahoover on 2010-04-23
> **tylersontag said:**
> There you go, the ubuntu team is one step ahead of my whining :-)

No whining, just a very popular feature request we're happy to be able to offer in 10.04 LTS. :)

---

