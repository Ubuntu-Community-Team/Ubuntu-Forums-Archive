---
title: "Missing auth.log data"
date: 2007-01-04
forum: Server Platforms
---

### Post by Jeeevs2001 on 2007-01-04
Hello, 

I have been reading up on ssh security and the advice is to keep an eye on the auth.log file. Having looked through it today it seems to be missing data. For example I know I logged in yesterday (and if I use the 'last' command I can see when) but this does not show up in the auth.log file, it only has 3 entries for the last 2 days and they are all cron jobs by root. 

Does anyone know why these log-ins would not appear in the auth.log? 

Thanks 

Jeeves

---

### Post by MJN on 2007-01-05
Are you saying **no** SSH logins are showing in auth.log?

Mathew

---

### Post by Jeeevs2001 on 2007-01-08
Yes, it doesn't seem to be recording them at all.

---

### Post by Biggus on 2007-01-14
Maybe there is something in the configuration file which is preventing external logins being logged?

---

