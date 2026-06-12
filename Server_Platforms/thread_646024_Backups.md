---
title: "Backups"
date: 2007-12-20
forum: Server Platforms
---

### Post by mattc908 on 2007-12-20
Alright for my server ultimately, how would I backup information, especially with MYSQL? If my system failed how would I regain the information I backed up and re put it back to were it was?

---

### Post by ijason on 2007-12-20
i know that mySql has the capacity to dump its contents to an archive file... i'm not sure how to access it on a local machine, as my web-provider has a semi-automated process to do it :/

if you're asking how to backup whole installs, i totally recommend searching google for 'partimage' :)

---

### Post by foxylad on 2007-12-21
Most settings are in /etc or your home dir, so back those up. For hte database, you need to dump the info first, then backup the dump file. Google "mysqldump".

---

### Post by twistedtwig on 2007-12-21
rysnc can be used to copy the files from one place to another... as mentinoed mysqldump is good for the DB.  Personally I create a "zip" of the whole server each week and backup that up on an external drive as well as doing a mysqldump

---

