---
title: "Privacy- Dot dirs on ~home"
date: 2014-08-09
forum: Security
---

### Post by bruce-euphon on 2014-08-09
I am alarmed at the amount of hidden files applications spray out on your home directory.

Most of the usage under my home dir is in hidden files and quite a bit of that is files that cannot be audited and removed for privacy reasons.

I know about browser caches; they are a sizable portion of the problem, but file managers and any number of other applications spray information into your files with little discipline, such as thumbnails and images that are nearly impossible to track and control. 

Just removing hidden files is not an answer since config of important programs like your command line shell use hidden files, but from a security and privacy issue the chaos of what applications put in those hidden directories is a real serious issue, maybe the snoops in the UK and elsewhere want that, but I am concerned both for privacy and the sheer disk usage.

---

### Post by The Cog on 2014-08-09
I'm not quite sure what you think the problem is. Is it just the number of settings files? I don't see why there should be a security issue - why do you think there is?.

I agree that it's not that nice to see lots of hidden files in your home directory, and it seems that recently there has been a move to use .config/application-name instead, which tidies things up a bit. But applications have to store their settings somewhere and your home directory (and below) is the only place they can freely write to.

---

