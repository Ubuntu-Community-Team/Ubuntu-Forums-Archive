---
title: "fail2ban-regex print matches"
date: 2014-01-17
forum: Server Platforms
---

### Post by markmckee6011 on 2014-01-17
Is there a way to print matches when using the command fail2ban-regex <logfile> <filter>

When I use the --print-all-missed switch, it displays the whole log file without highlighting the regexp matches.

Version: fail2ban-regex 0.8.11

Ignoreregex: 0 total

Date template hits:
|- [# of hits] date format
|  [274] Day/MONTH/Year:Hour:Minute:Second
`-

Lines: 274 lines, 0 ignored, 15 matched, 259 missed
Missed line(s):: too many to print.  Use --print-all-missed to print all 259 lines

---

