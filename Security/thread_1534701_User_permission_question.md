---
title: "User permission question"
date: 2010-07-19
forum: Security
---

### Post by atmega-ist on 2010-07-19
Greetings, all:

I've just installed xampp and everything works great.  immediately after doing so, i attempted to access the phpMyAdmin config file to update the root password.  my problems arose when i went to open the file and was told i didn't have permission.  so...  after tilting my head back and forth with a great deal of attitude and dealing the machine a sharp "I DO WHAT I WANT!" i thought i'd see if i could clear up my understanding of user privileges.

I've logged in as root from the terminal using "su" but this doesn't seem to help.  i'm not blaming the system at all and accept that this is a result of insufficient understanding.  i feel, however, that getting into this file may shed some light on some dim areas around user privileges as my recent google searches have failed my attempts to solve this specific situation.  (whenever i include "phpmyadmin" and "root" in the same search the results assume i'm talking about the root phpmyadmin user and not the root linux user).  i don't expect anyone to waste any significant amount of time on such a "n00b" issue, though, so just a link or something quick would be fine.

thanks so much!

---

### Post by bodhi.zazen on 2010-07-20
Ubuntu uses sudo 

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

For a root shell, use

```
sudo -i
```

---

### Post by atmega-ist on 2010-07-20
it never fails...  as soon as i post a question i stumble upon the answer immediately after.  turns out a guy i've worked with for about 6 months is a super linux/xampp ninja and straightened me out on the whole root thing...  who knew, lol.

bodhi.zazen -

your link, however, has gone straight to the top of the bookmark list and will be thoroughly read.  it was exactly what i was looking for.

thanks!

---

### Post by bodhi.zazen on 2010-07-20
> **atmega-ist said:**
> it never fails...  as soon as i post a question i stumble upon the answer immediately after.  turns out a guy i've worked with for about 6 months is a super linux/xampp ninja and straightened me out on the whole root thing...  who knew, lol.

bodhi.zazen -

your link, however, has gone straight to the top of the bookmark list and will be thoroughly read.  it was exactly what i was looking for.

thanks!

Glad you got is sorted =)

---

