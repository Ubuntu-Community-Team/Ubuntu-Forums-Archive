---
title: "have warning with rkhunter"
date: 2022-11-12
forum: Security
---

### Post by buill on 2022-11-12
Hi just scanned with rkhunter on my laptop with mate desktop environment installed and got this error

 Warning: The following suspicious (large) shared memory segments have been found:
[17:48:37]          Process: /usr/bin/mate-panel    PID: 1501    Owner: me    Size: 64MB (configured size allowed: 1.0MB)
[17:48:37]          Process: /usr/bin/mate-terminal    PID: 5005    Owner: me   Size: 16MB (configured size allowed: 1.0MB)
[17:48:37]          Process: /usr/bin/caja    PID: 1515    Owner: me    Size: 64MB (configured size allowed: 1.0MB)
[17:48:37]          Process: /usr/lib/mate-panel/wnck-applet    PID: 1522    Owner: me    Size: 32MB (configured size allowed: 1.0MB)

do i need to be worried about this ? 64mb is allot more than 1mb but i know nothing about it anyone could give me some info or links to would be great just found out about rootkits and although from what i read it seems to be more aimed at servers but still would like to keep safe thanks

---

### Post by TheFu on 2022-11-12
Do the research, but rkunter is known for generating many, many, false reports.  It got so bad that I just removed it.
I bet the reported sizes are wrong too.

---

