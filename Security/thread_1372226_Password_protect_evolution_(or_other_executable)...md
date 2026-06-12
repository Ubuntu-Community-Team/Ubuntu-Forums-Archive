---
title: "Password protect evolution (or other executable)..."
date: 2010-01-04
forum: Security
---

### Post by encompass on 2010-01-04
I want to password protect evolution.  How would I do that?  I want to allow anyone to access all my other software, but my business email needs to be private.  Ideas?
My current solution seems to be to setup another account.  But all the user switching and other what not seems a little much for one program.

---

### Post by BkkBonanza on 2010-01-04
I'm not sure if there's a better/easier way but here's one fairly easy way.

You do create a second user just for your email handling. But you don't have to switch desktop users to get to it.

Modify your menu item or shortcut icon to "gksudo -u otheruser evolution" (just add the gksudo -u user as prefix what you have now). Then when you run this it will use sudo to run as the other user, which will prompt for your password. 

You may have to toy with this a bit as I don't have another user here to test it out, but I think the idea is workable.

---

### Post by encompass on 2010-01-04
Never thought of that.  Thanks.  That just might work. :D  I will return and report on the proposal.

---

