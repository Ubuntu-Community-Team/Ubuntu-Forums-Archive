---
title: "adduser help"
date: 2007-12-15
forum: The Cafe
---

### Post by ssgatbliss on 2007-12-15
I'm trying to complete a lab for school and I'm sure the instructor is missing some vital information.  We were told to add a group using groupadd -g 333 -o qw333.  No problems there.  Now I am supposed to create an account using adduser.  It should include my full name and the group called qw333 with the bash shell as default.  To check it we are supposed to switch users and log into the account we created and make a vi file.  Here's what I used.

root@ubuntu:/home/ubuntu# useradd -gqw333 -p1351 -s/bin/bash ssgatbliss

Any help would be greatly appreciated.  Oh it's UBUNTU running off a CD

---

### Post by Vorian on 2007-12-15
tsk tsk tsk, thread closed.

---

### Post by nikoPSK on 2007-12-15
althought this has nothing to do with anything, why was this thread locked, vorian posted a comment on it:

> tsk, tsk. Thead locked.

then it was unlocked, moved to the cafe and vorian's comment is gone?

---

### Post by Dr Small on 2007-12-15
[quote=Vorian]tsk, tsk. Thead locked.[/quote]

What happened to that, any why did this get moved to the cafe? I saw nothing wrong with it.

Dr Small

---

### Post by -grubby on 2007-12-15
> **Dr Small said:**
> What happened to that, any why did this get moved to the cafe? I saw nothing wrong with it.

Dr Small

yah I noticed that too, what gives?

---

### Post by Vorian on 2007-12-15
> **Dr Small said:**
> What happened to that, any why did this get moved to the cafe? I saw nothing wrong with it.

Dr Smallactually, it was tsk, tsk, tsk, thread closed.  The beginners forum is not a place for help with homework.  This is a more appropriate forum for this question.

At the friendly request of the OP, I un-locked the thread.  I'm sorry if anyone was offended by this.

---

### Post by p_quarles on 2007-12-15
OP: The problem looks to be the lack of a space between the -g option and group name.

---

### Post by Crashmaxx on 2007-12-16
> **p_quarles said:**
> OP: The problem looks to be the lack of a space between the -g option and group name.

He needs spaces for all the options. Should read:
```

useradd -g qw333 -p 1351 -s /bin/bash ssgatbliss

```

BTW: Helps to read the manual, next time you get stuck try:
```

man [command]

```
For example useradd:
```

man useradd

```

---

