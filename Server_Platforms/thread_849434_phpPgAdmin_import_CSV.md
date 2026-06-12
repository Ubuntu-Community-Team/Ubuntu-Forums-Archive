---
title: "phpPgAdmin import CSV"
date: 2008-07-04
forum: Server Platforms
---

### Post by Garyu on 2008-07-04
I've set up my own server with apache, postgresql, php and a few other tools (such as phppgadmin) to remote administer it. So far, everything works great. But I find the documentation for phppgadmin to be very lacking.

**Can anyone tell me how to import CSV-files (exported from Excel) into postgresql through phppgadmin? **

According to the phppgadmin release notes, it supports CSV imports, but i can't figure out how. Am I supposed to enter SQL code for it with the COPY command? I've also seen people mentioning php functions such as pg_open_from() or something similar, but nothing on how to use it. I'm pretty new at this, so I appreciate any help you could provide. 

Server is Ubuntu Hardy Heron 8.04.1 handling its own domain, and I use SSH to access it from anywhere. Purpose is to keep a working database of biological research and use R to perform some statistical analyses that I can share with others in my team.

---

### Post by Garyu on 2008-07-04
ah, nevermind... I just have to create the table first, and then import into it. Too bad they didn't implement using the column headers as table column names (shouldn't be too hard)... Oh well.

---

