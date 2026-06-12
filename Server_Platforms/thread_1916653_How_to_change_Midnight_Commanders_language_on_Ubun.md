---
title: "How to change Midnight Commanders language on Ubuntu 8.04 LTS Server"
date: 2012-01-28
forum: Server Platforms
---

### Post by SicKk on 2012-01-28
Hi everyone,

as the topic says, I need to change the language of the installed Midnight Commander for a user in the terminal. The user is connecting over SSH. Does anyone knows where and how I can change the displaying language in Midnight Commander ?

cheers

---

### Post by sisco311 on 2012-01-28
```
LANG=lang mc
```
Where lang is the locale you want to use. For example:
```
LANG=hu_HU.utf8 mc
```will run mc in Hungarian. 

You can list the available locales with:
```
locale -a
```

See: [uhelp]community/Locale[/uhelp]

---

### Post by SicKk on 2012-02-03
sry for the late reply, thanks that worked :)

---

### Post by sisco311 on 2012-02-03
You're welcome!

Please don't forget to mark this thread as [SOLVED].

---

### Post by pauladiord on 2013-04-01
How many files are around to set this line into?
I guess you just forgot to mention this, too?
Without mentioning the file for the line you shouldnt set this topic to "solved".

---

