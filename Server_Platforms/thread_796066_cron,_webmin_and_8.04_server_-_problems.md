---
title: "cron, webmin and 8.04 server - problems"
date: 2008-05-16
forum: Server Platforms
---

### Post by neill on 2008-05-16
hi

i have a couple of headless servers administered with webmin 1.410 - a 7.10 mailserver and an 8.04 samba fileserver

i use webmin to set up cron jobs in both

in the 7.10 server everything works fine as i'd expect

in the 8.04 server, the same (or very similar - running shell scripts from /home) cron jobs are created in webmin in *exactly *the same way and if i run these manually from webmin they run fine

however, theses jobs do not (appear) to run from cron automatically as i'd anticipate :(

i have checked and triple checked all the webmin settings and they are identical across the 2 servers - i can see no obvious config reason why the one set of cron jobs runs and the other doesn't 

:confused:

how can i pick apart if this is a webmin issue, an ubuntu server 8.04 issue or something else going on ??

thanks

/neill

---

