---
title: "user restrictions"
date: 2008-05-29
forum: Security
---

### Post by braganfamily on 2008-05-29
I hope this is the correct forum for this topic.

I was wanting to know of any software that I can install which will control how much time users can access the computer.  I am wanting to limit my kids to a certain amount of time when they login under their own user name.  Perhaps even limit the time an individual user can use the browser.

These settings would be different for each user.

Anyone aware of such a thing?  

bobby

---

### Post by nunki on 2008-05-30
I dont know of any software, but perhaps you could do something primitive like add a "at" command into one of their login scripts. Something like:
```

at now + 2 hours << !!
logout
!!

```

Maybe something like this would work.

---

### Post by braganfamily on 2008-05-30
Interesting!  But, I don't know how to do that, never messed with scripts before.  I'll read up on it.

Thanks.

bobby

---

### Post by Dark Angel on 2008-05-31
I set up a cron job to shut down the browser, chat client and music player before locking the screen at a set time each day, if that's any good to you.

---

