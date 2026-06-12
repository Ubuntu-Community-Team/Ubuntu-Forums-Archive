---
title: "[SOLVED] MySQL Replication just... stopped."
date: 2008-12-04
forum: Server Platforms
---

### Post by EvilMarshmallow on 2008-12-04
I had a MySQL server set up to replicate a database from another server.  It's been working fine for several months.  However, it's just stopped replicating the data?  I tried restarting mysql on both machines to no avail.  Where do I go from here?  I checked the config files and everything is exactly as it should be, they just don't replicate any more.

---

### Post by wkitty42 on 2008-12-06
ummm... what do the logs say on the slave server? if they've run into a problem with an insert, for instance, then it won't get past that until the error is corrected or you tell it to skip the error...

i ran into something very similar on my servers when i set up replication and the problem was traced to the insertion of "duplicate" records... i ended up configuring the slave to skip these types of errors and it has been running non-stop for weeks...

it is possible that you might be able to determine the error by logging into the mysql slave and issuing a 'show slave status' to see what it says may be going on...

---

### Post by EvilMarshmallow on 2008-12-06
I did some digging in the past couple of days and found that replication was stopped (There are two fields, can't recall right off-hand what they're called, but if replication is active they're both supposed to be "Yes".  The first one was a "No" and the second was a "Yes".  Apparently the system freaks out if you shut off the master.

My config is like this: the "Master" is a workstation on our plant floor that logs data from a scale system.  I set up the server in the server room as its "slave" because I want them to be able to use the system even if the server's having problems, but I want the data replicated to it because it's where our intranet looks for data when they ask for the data download.

Someone on the floor shut off the master at the end of the shift.  It seems this caused the system to fail.  All I had to do to start it back up was go to the slave and do the following:

slave stop;
reset slave;
slave start;

And I'm back to normal.  It doesn't pull records that were entered while replication was offline but it at least starts getting new data.

I put the above in a bash script and run it via cron every 15 minutes now.  That should take care of my problems!

---

