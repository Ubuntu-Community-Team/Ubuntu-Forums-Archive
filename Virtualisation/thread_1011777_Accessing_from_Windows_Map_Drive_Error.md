---
title: "Accessing from Windows Map Drive Error"
date: 2008-12-15
forum: Virtualisation
---

### Post by talofo on 2008-12-15
On the virtualized windows XP, when I try to save a file using Any ADOBE CS4 and I then choose the map drive (the one shared on ubuntu), I get this error:

An error occured while reconnecting Z to \\vboxsvr\home 
Adobe Drive CS4 Network: The network name cannot be found.

As anyone experience this already?



Thanks,
MEM

---

### Post by Dedoimedo on 2008-12-15
Do you get this error with any other tool / application?
Can you access the share normally (explorer)?
Dedoimedo

---

### Post by talofo on 2008-12-15
Yes. Normally I can. Yes was another aplication. And you haven't asked but I say: Yes, it's a windows warning window. Since I've just to ubuntu because I was seek of m$, I've well... hmm... behave like an animal, so, I remove the Adobe Drive Bla bla product from adobe master collections. 


No more errors. :)

And... actually, when trying to solve this error: I found a way to **share the same desktop on guest and host machine**, if we are running windows xp.

open regedit. Locate the key:

HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders

Change the desktop key to:

Something like:

z:\home\userblabla\Desktop. BUT: instead of Z we put:\\VBOXSVR\

so:

\\VBOXSVR\home\userblabla\Desktop\


I've used z: but of course, adapt this to your mapped letter on virtualbox.



Yupi!!! :D


Thanks again for your reply,
MEM

---

### Post by CFBauer on 2009-04-06
I'm having the same problem. How do you remove Adobe Drive?

---

