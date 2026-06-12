---
title: "[IDEA]  Make checking for updates work with less bandwidth"
date: 2007-11-09
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2007-11-09
Checking for updates often downloads package lists that can be a few MB in size.

When on dialup, EDGE, GPRS, or even 3G, that can take about 30 mins or more, simply to determine if I need any updates or not. Mobile service providers can charge a lot for transfer of data.

This causes me to never update the system, which in turn means that when I do get updates, there's too many to practically download.  This leaves my system insecure as vital security patches can't be installed.

This could be solved by:
[LIST=1]
[*]doing everything possible to reduce the size of the list (gzip, remove unnecessary info etc.)
[*]Using differential lists - as well as hosting the list on the server, host diffs from older versions.
[/LIST]

Those changes could be made in a way which doesn't break compatibility with older versions of apt accessing the repository.

This is a very necessary feature because in the UK in 2007 nearly 4 million households still have only dial up internet access (15%),  and many are still not within range of any broadband access, and I'm sure in less developed countries the figure will be much higher.

---

