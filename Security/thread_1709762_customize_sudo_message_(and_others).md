---
title: "customize sudo message (and others)?"
date: 2011-03-18
forum: Security
---

### Post by fela on 2011-03-18
Is it possible to customize this message:

user username isn't allowed to execute /bin/somecommand as root on host

I want it to say something like:

Sorry, that command is prohibited. Email [email]sysadmin@myhost.com[/email] and ask him to allow /bin/somecommand

I'm guessing these kinds of messages aren't hard-coded into the program, right?

Cheers, Fela

---

### Post by BkkBonanza on 2011-03-19
Try **man sudoers** - see strings section. It doesn't appear to have a string for when permission is denied but it does have a message (lecture) for first/every use and badpassword, which may be enough for what you need.

---

### Post by fela on 2011-03-19
> **BkkBonanza said:**
> Try **man sudoers** - see strings section. It doesn't appear to have a string for when permission is denied but it does have a message (lecture) for first/every use and badpassword, which may be enough for what you need.

Thanks, I managed to make it give a good enough lecture for what I needed :)

---

### Post by earthdan on 2011-10-06
Please explain... I am having same problem.

---

