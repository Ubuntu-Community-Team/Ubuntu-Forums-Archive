---
title: "compile wine 1.1.17 in hardy?"
date: 2009-03-14
forum: Wine
---

### Post by Meow27 on 2009-03-14
again im here cause i cant compile wine on my laptop. 

im stuck with the same exact problem
[http://ubuntuforums.org/showthread.php?t=1073707](http://ubuntuforums.org/showthread.php?t=1073707)

edit------------

> 
at the end of doing ./configure, im told that i need a newer version of gnutils

Code:

configure: libgnutls development files not found, no schannel support

what do i do? i need a newer version of libc6 for it >.>

[http://i119.photobucket.com/albums/o144/flamehawk/Screenshot-10.png](http://i119.photobucket.com/albums/o144/flamehawk/Screenshot-10.png)  (pic is too big, dont wanna spam ur screens)

---

### Post by Brinstar on 2009-03-14
its available in the wine repo, just add the wine repos to your sources, and the gpg key, and just install/update from synaptic


just add this line to software sources,


deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

then get the gpg key

[http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg](http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg)

and add it to authentication

if you still don't understand just go to 

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Meow27 on 2009-03-14
there are reasons why i want to compile it

and reasons why you should look in the link i posted above

---

### Post by hikaricore on 2009-03-14
You started a new thread.  No one is obligated to look at your other thread.
Please post all pertinent info in the current thread so that we don't have to hop around.

---

### Post by Meow27 on 2009-03-14
ok ill do that, thanks for the advice

---

### Post by betrunkenaffe on 2009-03-14
I read your thread, I don't understand your reasons.

---

### Post by Meow27 on 2009-03-14
patching and impatience.

but do my reasons matter? my question is not how to get wine, its how to compile it. i didn't mention here that i DONT HAVE THIS PROBLEM IN INTREPID

, yokozar apparently is able to do it but he wont tell me when i reply to his posts (replies when he fixes/adds the links to the archive)

---

### Post by DoktorSeven on 2009-03-14
Well, if it is telling you that you need a certain version of a dependency of wine and that yours is too old, then you will have to go download and compile a suitable version of that dependency manually as well.

From what I am seeing I am assuming that this is the issue.

---

### Post by Meow27 on 2009-03-14
> **DoktorSeven said:**
> Well, if it is telling you that you need a certain version of a dependency of wine and that yours is too old, then you will have to go download and compile a suitable version of that dependency manually as well.

From what I am seeing I am assuming that this is the issue.

ok thanks for the reply,

im wondering how to do that though, the new versions require lib6 2.9, while the hardy is locked to libc6 2.7 :/

---

### Post by hikaricore on 2009-03-14
If the issue is libc6 you have two options.

Build libc6 from source and risk breaking your system.
Or update Ubuntu like any sane person would do in this case.  ^_^

---

### Post by Meow27 on 2009-03-14
i wish i could upgrade my laptop to intrepid. but intrepid is a dismal disaster when it comes to the graphics and handling anything that has to do with the screen.

i just hope jaunty works....... :/

edit, does anyone know how yokozar does it?

---

### Post by betrunkenaffe on 2009-03-14
You said in other thread if anyone had any questions to ask, I was stating I didn't understand your reasons hence was curious for clarification.

When I updated from Hardy to Intrepid on my desktop, I had video issues, it was the nVidia driver though, not Intrepid, when I loaded 180 onto the machine, the video issues went away.

Don't know if you use nVidia but you could always test out.

---

### Post by Meow27 on 2009-03-14
lol its fine

back to offtopic,

im using an intel card.

in intrepid. the back light keeps flickering and always turns off, its uncontrollable and it sucks. 

playing videos was perfect though. its just i had no control over any hardware features and that just made the usability on my computer impossible

mind i ask, what is 180?

---

