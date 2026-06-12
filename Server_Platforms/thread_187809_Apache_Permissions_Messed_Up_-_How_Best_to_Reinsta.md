---
title: "Apache Permissions Messed Up - How Best to Reinstall"
date: 2006-06-03
forum: Server Platforms
---

### Post by goneskiing on 2006-06-03
Since upgrading to Dapper from Breezy, I'm getting all sorts of weird problems trying to run PHP/Postgres scripts.  I'm getting 404's, 403's, permission issues, etc

I'm willing to just wipe out my Apache and PHP programs and configs and try fresh - what is best approach to this ?

---

### Post by gombadi on 2006-06-03
In a situation like this, with many errors, it is best to pick one and fix that.

Pick a 404 error. Why did it fail? 

Check the error logs. Make sure the file exists where the mappings point to. Is document root pointing to the correct place. What are the file permissions. Can the web server read the file.

If you fix the errors on one problem quite often all the other problems will be fixed :-)

I would leave a reinstall as the last option.

---

