---
title: "cant find log file from logger"
date: 2008-06-07
forum: Security
---

### Post by 565Customz on 2008-06-07
ok i set up a keylogger (lkl) and now i cant find the log file. i created it in /usr/share/lkl  but it isnt there (or hidden) wondering if it went somewhere else or if i have to manually create it or what.  dont want to have a huge file full of passwords on my computer and me not know where they are...know what i mean.

---

### Post by 565Customz on 2008-06-09
bump

---

### Post by p_quarles on 2008-06-09
I haven't used lkl specifically, but I can throw out a guess here: if you specified a directory to write the log to, but then run the program as an unprivileged user, it won't have the permission to create the file. Is this possible? 

Otherwise, you will find that most background applications store their log files in /var/log.

---

### Post by 565Customz on 2008-06-09
i think that you have to be su in order to install it and thats when it creates the file..but the file definatly isnt there. i created it manually it still wouldnt load anything into it,

---

