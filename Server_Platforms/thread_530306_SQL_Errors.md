---
title: "SQL Errors"
date: 2007-08-20
forum: Server Platforms
---

### Post by ctlw83 on 2007-08-20
#1045 - Access denied for user 'www-data'@'localhost' (using password: YES)

I have done multiple Google searches and checked many forums and tried all of their suggestions.

I've created a database, but can' connect ot it as it gives me the same error.

I've tried changing the root password still with no luck.

I have also tried starting/stopping the server.

PHP My Admin won't let me in with the 1045 error above

I tried manually logging in through MySQL directly and it gives me a similar error exceot (using password: NO) instead.

very frustrating.

I don't want to try re-installing MySQL server, I tried that and it messed things up so badly i had to do a full OS reinstall, which is a pain because I have a RAID mirror setup.

any ideas??

---

### Post by meatpan on 2007-08-20
Here are some ideas:
o Verify the server is running.  Do this by running 'pstree', 'top', or 'ps -xfa'
o Verify the server is waiting for user connections.  Run 'netstat -Cvaetpu' and confirm the presence of a mysql entry.
o  Post the full command line you tried with the 'mysql' command.  
o  Learn more information about why you might be refused access.  The directory /var/log/mysql contains logs that might have some useful info.
o  Experiment with mysqladmin.  Lots of things you can do with this command, but make sure you try these other ideas first.

---

