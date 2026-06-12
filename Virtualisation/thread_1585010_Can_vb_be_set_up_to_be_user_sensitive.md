---
title: "Can vb be set up to be user sensitive?"
date: 2010-09-29
forum: Virtualisation
---

### Post by bdemers on 2010-09-29
This is a pre-install question.  Read through the fantastic manual, but didn't get this question answered, and it affects how I do my install.  I want to separate what vm's are available to each user. If I have a Hardy desktop set up for user1 and a different vm, also of Hardy set up for user2, I'd like user1 to see only user1's image of Hardy on the menu, not user2's.  Without a thorough understanding, my inclination is to set up a distinct host instance for each user, 5 users, 5 running vb hosts, only one member to each host's group.  Is this really necessary?   Yet trying to convince me to pool all vm's together is going to be a formidable task.  I do not want a user to be aware of any other user.  BTW, each user is connected remotely, never from the system console.  Things I may want to look at and consider?

---

### Post by P4man on 2010-09-30
Maybe a dumb question, but why not share the same VM but create different users in the VM ?

Anyway, if I understand the question correctly, then it I think its actually the default behavior. VirtualBox is configured per user. See here:
[http://www.virtualbox.org/manual/ch09.html](http://www.virtualbox.org/manual/ch09.html)

All config files reside in the home folder, which is different per user account. If you create a VM for user Bob then user John will not see it - or even have access to it if you dont give him access to Bob's home folder.

---

### Post by bdemers on 2010-09-30
P4Man..Thanks.  I had read that chapter over, and I want to be where that desktop background is.  Anyway, I had noticed that there is a separate folder for each user, but had not understood that to mean that a distinct menu would come up for each user, but on further reflection, I'd have to say that is the most logical. To date I have vb installed, a single user assigned, no vm's,phpvirtualbox gives the headless server some admin gui.  I want to start moving folders around to different physical volumes next, so that is why I asked the question.  I have very limited space per volume, but lots of volumes, need to figure out best way to divy up.(this is all being put together via the surplus market).

Off topic, your Avatar is great.  I want to steal it and use it as a signature for myself.  Seems I'll never get a good understanding of all those command line switches! Spent too long with Gnome doing it all for me.

---

