---
title: "I dont believe it. Solved my problems."
date: 2007-10-09
forum: The Cafe
---

### Post by anaconda on 2007-10-09
I just solved my cdrom and sound problems with my work machine.

Couldn't get the sound working and couldn't write CD:s

Guess what was the problem:

**I didn't belong to audio or cdrom groups!** (but I was in admin group)

I think this is a bug/annouance. the first user belongs to those groups as he should, but if you make more users they wont belong to audio or cdrom or floppy etc..groups.

unbeliavable!!!!!!!!1

---

### Post by FuturePilot on 2007-10-09
Interesting. But I've created other users and it works as it should.

---

### Post by wieman01 on 2007-10-09
Apparently it is a bug. I had the same problem, but a new (standard) user would work fine. A new ADMIN user, however, would face the same issue.

---

### Post by wieman01 on 2007-10-09
> **FuturePilot said:**
> Interesting. But I've created other users and it works as it should.
I did mentioned that twice in the other thread, didn't I? ;-) People seem to ignore me. :-(

---

### Post by anaconda on 2007-10-09
How do you add new users?

I always use the terminal and adduser -command. Could this be the problem? 

I prefer adduser to a GUI, because it is faster, you can add users to groups with it and it works even if x wont start.. And I learned it before coming to ubuntu.

And by the way, I remember I had this same problem in edgy too. Should have remembered. now I wasted over an hour reading solutions to "sound problems"

And wieman01. No we dont ignore you ;)

---

### Post by FuturePilot on 2007-10-09
> **wieman01 said:**
> I did mentioned that twice in the other thread, didn't I? ;-) People seem to ignore me. :-(

Yes you did;) I've only created desktop users not admin users. So maybe the same thing would happen if I created an admin user.

---

### Post by anaconda on 2007-10-09
Actually I didn'r create an admin user!

I created an user and then afterwards added him to admin group.

But when I created the user I gave him a certain UID, which I have to have at work..

eg.
adduser username --uid 1234

Would this have any effect in which groups the user belongs? It shouldn't.

---

### Post by wieman01 on 2007-10-10
> **FuturePilot said:**
> Yes you did;) I've only created desktop users not admin users. So maybe the same thing would happen if I created an admin user.
Yes, you are right. I think it would. Somehow the admin rights are messed up. Perhaps on purose, who knows.

---

### Post by wieman01 on 2007-10-10
> **anaconda said:**
> Actually I didn'r create an admin user!

I created an user and then afterwards added him to admin group.

But when I created the user I gave him a certain UID, which I have to have at work..

eg.
adduser username --uid 1234

Would this have any effect in which groups the user belongs? It shouldn't.
Honestly... I am using the graphical tool most of the time. ;-) There you can assign primary as well as secondary groups. Have you used it before or do you do "command line" only? :-)

---

### Post by southernman on 2007-10-10
> **wieman01 said:**
> I did mentioned that twice in the other thread, didn't I? ;-) People seem to ignore me. :-(
What did you say again? :p 

;) jk ya

---

### Post by wieman01 on 2007-10-10
> **southernman said:**
> What did you say again? :p 

;) jk ya
Now I cannot remember either. Must be my alter ego. Who are you by the way? ;-)

---

