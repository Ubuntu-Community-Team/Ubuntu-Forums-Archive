---
title: "Mirror/failover configuration"
date: 2008-03-21
forum: Server Platforms
---

### Post by vortmax on 2008-03-21
I have a server that is responsible for handling incoming support emails.  It takes the emails, parses them, logs the parts to a mysql database reformats the email and resends it to the techs.  The server also has the mysql and http portion of the rest of the helpdesk system.  Anyway, the system is too important to not have a failover in place.

What I need to do is have a second machine with a replica of the mysql database and website that is updated in real time.  There also needs to be some sort of heartbeat signal so the backup server knows if the primary server is up or down.  One tricky thing is that I have had an issue with the server clashing with the VMserver it's on causing a bad superblock.  This allows the server to boot appear alive, but the disk is limited to read only.  So the server will appear alive, but it won't be able to do anything.

The other issue is that the server is pulling in the support email off a pop3 server, so I can't just to a straight clone because as soon as one server accesses the email, it's gone.  I could make a third server responsible just for fetching mail and processing, but that would be back to a single point of failure.

So any thoughts on an elegant way to make this happen?  I've thought of some methods, but they just seem to be giant hack jobs with plenty of room for failure.

---

### Post by crouton on 2008-03-21
MySQL replication is one option.  There are also heartbeat/watchdog programs (names escape me at the moment)

As for email, consider IMAP if your email support system handles it.  If not, see if you can tell the software to leave a copy on the POP server (most email clients offer this already).

---

### Post by vortmax on 2008-03-28
I'm made some headway into my project.  I know have a backup server running that is a slave to the main sql server.  As a slave, this server is a real time mirror of the main sql server.  On top of that, I'm rolling hourly dumps using mysqlhotcopy.

So far I'm happy with how this is working.  I now have two more steps to take:

1.  Make the slave server become master when the main server goes down.  I know I can configure the two machines in a Master-Master config which would make them update off each other.  I would have to devise a way to make sure only one was being written to at a time though.  Anyone have experience with this set up?  The server does not see a high volume of update or insert queries so it might not be a big issue.

2.  A heartbeat script.  I've looked at the linux HA packages that would set up a 2 node cluster, but that is more complexity then I need.  All I need to do is test the main server and if it goes down or if it is no longer able to hit the mail server, the backup server would start pulling down mail and processing it into the db.  It could be as easy as a cron script that runs a heartbeat check before issuing the 'fetchmail' command, but I'm not sure how to set up that heartbeat.

---

