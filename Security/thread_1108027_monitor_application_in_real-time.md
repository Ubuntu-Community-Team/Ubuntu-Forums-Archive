---
title: "monitor application in real-time"
date: 2009-03-27
forum: Security
---

### Post by rawandnet on 2009-03-27
thank you

tail -f messages worked?

---

### Post by shad0w_crash on 2009-03-27
Do you mean a change in the code of that program?
Or in it's config files?

You could make a hash of the program by using: md5sum [filename] and verify this has. This can be done realtime by using a script. It's also provided in Ossec (a HIDS).

---

### Post by rawandnet on 2009-03-27
Not changing program.  I mean running a command in terminal that display logs (messages) while running applications. 

example when login to root, it shows that I am trying to access root user, I have used tail -f messages but doesn't work

---

### Post by shad0w_crash on 2009-03-27
well ossec does that,

Example of my logs;

** Alert 1238185238.2190*: - syslog,sudo
2009 Mar 27 21:20:38 *->/*/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to * executed'
Src IP: (none)
User: *
Mar ** 21:20:36 * sudo:   * : TTY=pts/0 ; PWD=/opt/lampp/* ; USER=* ; COMMAND=/usr/bin/nano *.php

** Alert 1238186827.2221*: - syslog,sudo
2009 Mar 27 21:47:07 *->/*/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to * executed'
Src IP: (none)
User: *
Mar 27 21:47:06 * sudo:   * : TTY=pts/0 ; PWD=/home/* ; USER=* ; COMMAND=/bin/bash

If you want pop-ups or something like you should make a program (example in C or Java) that popups when te log is changed.

---

### Post by rawandnet on 2009-04-06
> **shad0w_crash said:**
> well ossec does that,

Example of my logs;

** Alert 1238185238.2190*: - syslog,sudo
2009 Mar 27 21:20:38 *->/*/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to * executed'
Src IP: (none)
User: *
Mar ** 21:20:36 * sudo:   * : TTY=pts/0 ; PWD=/opt/lampp/* ; USER=* ; COMMAND=/usr/bin/nano *.php

** Alert 1238186827.2221*: - syslog,sudo
2009 Mar 27 21:47:07 *->/*/auth.log
Rule: 5402 (level 3) -> 'Successful sudo to * executed'
Src IP: (none)
User: *
Mar 27 21:47:06 * sudo:   * : TTY=pts/0 ; PWD=/home/* ; USER=* ; COMMAND=/bin/bash

If you want pop-ups or something like you should make a program (example in C or Java) that popups when te log is changed.


thanks for your help.

---

