---
title: "Some random thoughts on sleep(OS related)"
date: 2008-02-04
forum: The Cafe
---

### Post by ninjkiran on 2008-02-04
like most linux users that also like to play games I dual boot between Windows and Linux, mainly for fun since  I like playing with linux and its application speed.  Yea I do have Wine and can install windows apps but well that doesnt cut it for most games.

Anyway when you put windows to sleep it saves the current image of whats going on so when you press a button oh your keyboard or what not it quickly loads.  Of course that is a standard feature that many OS's have these days nothing new.

Anyway heres my idea that I have no claim of being able to do, but just an idea annd ide like input if it would be "possible".  This is assuming you have Linux install on a seperate drive.

Anyway would it be possible to develop of "sleep" style mode that rather then shutting down the computer being able to switch between operating systems in a "faster" way without having to do a full reboot and going through Grub(or Lilo) by taking advantage of a sleep style mode.  

Eh just a random thought I had while sitting on the toilet that probally isnt even anywhere near possible, it would just be nice to be able to switch between OS's as easy as you switch sources on your TV.  Maybe a random idea for the future.  

Anyway dont take this thread too seriously~ have fun and share your thoughts and ideas, maybe ones you get while sitting on the can to haha.

---

### Post by SunnyRabbiera on 2008-02-04
sadly I dont think this is ever to happen, as both need to be held in seperate sessions.
currently the only way to come close is to have windows run virtually.

---

### Post by Vadi on 2008-02-04
Not unless you have insane amounts of RAM. When you put your computer to 'sleep', it really isn't turned off. It's still on, and all programs are still loaded in your ram (so if you pull your plug - you'll lose your work just as if you've pulled it with the comp on).

So to have one OS sleep, it would still take up ram, then getting another one up will result in less ram. Plus they, the other one could simply overwrite the other OS's "share" of ram, or complain as to why is that space taken up..

Not practical to implement

---

### Post by igknighted on 2008-02-04
If you used "hibernate" instead of suspend/sleep, you could cut the time down.  Not quite as snappy, but more feasible.  SSD drives, open/customizable bioses, and more streamlined boot sequences will also help in the future.

---

### Post by ninjkiran on 2008-02-04
Yea like I said, probally not feasable but an interesting idea non the less.  The goal would be to be able to almost completely hot swap between systems without going through a full reboot.

Perhaps saving the session would be tough but lets say it didnt and you where able to load from linux straight to the boot loader(Grub being it on my system) would be a big improvement.  I doubt you would be able to do it from the Windows side but from the linux side it might be more feasible.

---

