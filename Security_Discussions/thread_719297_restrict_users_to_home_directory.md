---
title: "restrict users to home directory"
date: 2008-03-09
forum: Security Discussions
---

### Post by samona on 2008-03-09
Is there a way to restrict users to their own home directory?  For example, users shouldn't be able to "cd /" or "cd " into another users home directory.

---

### Post by kevdog on 2008-03-09
Like using a jailkit? or do you just want to change permissions so they cant see the other files?

---

### Post by samona on 2008-03-09
Yes, is that possible on ubuntu server?   How would i do it?

---

### Post by kevdog on 2008-03-09
Im no expert on jailkit, as it really is a way to setup a chroot kit -- Just be forewarned that these are not absolutely secure -- If a determined hacker where in a jail, Im sure he could break out of it, so dont ultimately use this as you sole measure of security.  For most users however it really works great.

Because Im a novice with setting up chrootkits, I just used this kit to help me: [http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

It basically is a set of scripts that automates creation and management of your chrootkits.  Since Im no expert on the matter, I figure I would depend more on the expert to provide for some basic settings.  In addition the forum although small, has turn around time of about 1/2 day for answering your questions -- which isnt really all that bad I think!

---

### Post by samona on 2008-03-09
Thanks for the help and information.  I really appreciate it.  I didn't know there was another way besides using jailkits.

---

