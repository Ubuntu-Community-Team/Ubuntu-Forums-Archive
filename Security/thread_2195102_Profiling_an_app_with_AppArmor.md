---
title: "Profiling an app with AppArmor?"
date: 2013-12-22
forum: Security
---

### Post by tji on 2013-12-22
I want to check out an app's required capabilities in order to build a profile for it.   So, I tried enabling logging of the app's actions with 'aa-complain'.   But, it doesn't seem to have any effect.

Any tips, or pointers to docs, on how to do that?  It's got to be a common process.  

I basically want to make app armor watch a binary,  log its actions, then view/summarize the logs.

---

### Post by claracc on 2013-12-22
Have you tried the sticky in this security subforum : [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906) , "Introduction to AppArmor" ?

---

### Post by Hungry Man on 2013-12-23
You must first create a profile for the app using aa-autodep. Then set th eprofile to complain with the command you used.

---

