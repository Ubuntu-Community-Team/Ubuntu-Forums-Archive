---
title: "Ctl+Alt+F6 Sends to Login Screen"
date: 2008-02-16
forum: Ubuntu Brainstorm
---

### Post by lexen on 2008-02-16
I love the using Ctl+Alt+F7 and so on to switch users and if things get really bad I press Ctl+Alt+F6 which sends me to terminal where I can shutdown.  Right now, I can go to terminal with Ctl+Alt+F5 and Ctl+Alt+F6 and I was thinking it would be really great if Ctl+Alt+F6 would send me to the login screen, so if the system really locks up, I could just re-login instead of shutting down.

   I don't know how hard this would be from a programmers stand point, but I don't think it would be too hard and it would make Ubuntu a lot more usable when the system crashes.

   If anyone knows why this won't work, let me know.  I would love to hear what everyone thinks.



Thanks,
Lexen

---

### Post by chrisccoulson on 2008-02-16
Ctrl+alt+backspace? This just restarts X, which will take you back to a login screen

---

### Post by smartboyathome on 2008-02-16
> **chrisccoulson said:**
> Ctrl+alt+backspace? This just restarts X, which will take you back to a login screen

It will be like a hard restart, though, and will cause any unsaved data to be lost.

---

### Post by chrisccoulson on 2008-02-16
What was the OP proposing? If X has crashed so that you have to switch VT, you're going to lost data anyway.

---

### Post by maybeway36 on 2008-02-16
You would just have to run two GDMs or KDMs. It shouldn't be that hard to set up, althoguh I'm not really sure how.

---

### Post by chrisccoulson on 2008-02-16
I think you would have to launch a second GDM on another tty after you log in.

But what's the point? If your session freezes to the point that you need to switch VT, are you suggesting we log in via a second GDM (leaving the first one there), as opposed to killing the current session and just starting again? I don't think thats a very good idea.

---

### Post by lexen on 2008-02-17
I don't think I explained the reasons very well, so here are the advantages:

If the computer freezes you don't have to hard boot
Makes it easier to switch users
If you made a mistake in you settings which makes it so you can't see your screen
 
   I can't think of anymore, but I know it would be a real convenience to me and I think it would help others out too.  It might be like multiple desktops, hard to image why you need it, but when you have it, it's frustrating to lose it.


Thanks for the input.

---

