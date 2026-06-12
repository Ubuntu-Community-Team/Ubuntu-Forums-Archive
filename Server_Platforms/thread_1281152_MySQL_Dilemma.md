---
title: "MySQL Dilemma"
date: 2009-10-03
forum: Server Platforms
---

### Post by sdlynx on 2009-10-03
Hello everyone,

I'm working on a site (see my sig), and at one point I want to run a mysql_query($var1, $con);  My $var1 is:
```
INSERT INTO stories(dateTime,story,nerdy,fail,type) values(NOW(),'Today <large story> MLIN','15','4','I Don't Know')
```

I do have a table named stories, with those fields, and am using the correct data types for everything.  In fact, this code worked just yesterday but has now failed to work.  Ideas?

P.S. I've noticed the problem only happens when a large 'story' value is tried to be inserted.

---

### Post by yabbadabbadont on 2009-10-03
If you are doing this from a shell script, be advised that the shell only allows commands to be something like 32K characters (including spaces) long.  It may be possible to change that setting but, if so, I don't know how.

---

### Post by sdlynx on 2009-10-03
I figured it out.  Me and my stupid quotes haha, the 'I Don't Know' value was being cut off and giving me an error due to that extra apostrophe inside.  Thanks for the insight though.  By the way I'm doing it through PHP.

---

### Post by yabbadabbadont on 2009-10-03
I figured it was php, but I didn't know if the back-end ever passed the sql commands using a shell.  (I've never messed with php)  Misplaced and/or mismatched quotes really do bite one on the posterior occasionally.  :D

---

### Post by sdlynx on 2009-10-03
> **yabbadabbadont said:**
> I figured it was php, but I didn't know if the back-end ever passed the sql commands using a shell.  (I've never messed with php)  Misplaced and/or mismatched quotes really do bite one on the posterior occasionally.  :D

yeah xD unfortunate.

---

