---
title: "SOLVED DansG V. 2.10.1.1 Webmin Module V. 0.7.1 cannot modify exceptionfilesitelist"
date: 2013-05-27
forum: Server Platforms
---

### Post by pcalligaris on 2013-05-27
***SOLVED***
Hi to all,
I'm using an Ubuntu server 12.04 with DansGuardian V. 2.10.1.1 and Webmin Module V. 0.7.1 to allow a graphical access to configuration's files of Dansguardian.
However the webmin page  "View/Edit System-Wide Lists" shows the links just to:
[TABLE="class: ui_table sortable ui_columns"]
[TR="class: mainbody row1"]
[TD][/TD]
[TD][URL="https://192.168.3.253:10000/dansguardian/editfile.cgi?file=/etc/dansguardian/lists/bannediplist&return=%2Fdansguardian%2Feditlists%2Ecgi"][COLOR=#50507c][I]"/etc/dansguardian/lists/bannediplist"
"[/I][/COLOR][/URL][URL="https://192.168.3.253:10000/dansguardian/editfile.cgi?file=/etc/dansguardian/lists/exceptioniplist&return=%2Fdansguardian%2Feditlists%2Ecgi"][COLOR=#50507c][I]/etc/dansguardian/lists/exceptioniplist"
[/I][/COLOR][/URL][/TD]
[/TR]
[/TABLE]
forgetting others configuration's files. 
It's a bug? Maybe it's possible to modify this page?
Thanks in advance for help
Bye
Paolo

---

### Post by pcalligaris on 2013-05-29
SOLVED!!
I discovered that it's necessary to define at least 1 group in "View/Edit A Filter Group's Base Config" and then in "View/Edit A Filter Group's Lists" view appears the full list of exceptionsites, and bannedsites etc.
thanks to all
bye

---

