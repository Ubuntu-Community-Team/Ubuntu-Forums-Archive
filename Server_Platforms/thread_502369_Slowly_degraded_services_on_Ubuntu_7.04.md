---
title: "Slowly degraded services on Ubuntu 7.04"
date: 2007-07-16
forum: Server Platforms
---

### Post by mjmogo on 2007-07-16
Hello all,

I recently installed Debian Etch to use it as a file/mail/ftp server, and was informed that there is a bug in Debian that prevents Samba from working. As a fix, I was told to use Ubuntu instead. Well, I got everything set up the first time, and things appear to be working fine...

EXCEPT, over time, things just seem to slow way down. It has been running for about a week, and this morning when I put it up for public service, whenever I would log in, it just seemed to move at a snails pace. Also, when trying to reboot the whole system normally, it took about 45 minutes (I kid you not) to shut down all the services and restart.

I am using the latest version of Ubuntu, Samba, ProFTPD, Apache2, and MySQL (most up-to-date with apt-get). I am running on an IBM Think Centre (about 3 years old), with about 1.8 Gig of ram. The only thing that I can think of that might be happening is a memory leak.

Is there something else I should check for? Does anyone have any suggestions?

Thanks,

Mike McG

---

### Post by scrooge_74 on 2007-07-16
Check your disk? Maybe a disk is planning to die on you

---

### Post by mjmogo on 2007-07-19
> **scrooge_74 said:**
> Check your disk? Maybe a disk is planning to die on you

While I could be wrong, I don't think it is a probelm with the harddrive. When I formatted the disk prior to installation, I ran all the tests that Ubuntu has and it didn't complain about anything. Being a very large disk, it took a while for this to complete.

One thing I noticed when shutting everything down was that the system takes FOREVER to stop MySQL. Every time that I have had to reboot, this happens.

Mike McG

---

### Post by scrooge_74 on 2007-07-19
try stopping the MySQL server and then try to shut down, you could have a problem there. 

run top from a terminal maybe that will tell you something about your resources

---

### Post by Snaglpus00 on 2007-07-30
I have the same problem with my ubuntu 7.04 server.  It will stay up and run like a champ for 4-5 days and then it will slow down to a crawl.  Reboots take forever.  My mysql was hanging on shutdown so I removed it from starting up and it still does the same thing.  

I don't see any processes in a ps avx that shows any problems.

But catch this if a run a simple script that counts 5 seconds and reports the time difference back, that 5 seconds takes 32 real time seconds to count.   After  a reboot the server works fine for a few days again and counts 5 seconds accurately.

Start Script:
#!/bin/bash

while [ 1 == 1 ]; do
START=$(date +%s)
echo "$START"
echo "sleeping"
sleep 5
END=$(date +%s)
echo "$END"
DIFF=$(( $END - $START ))
echo "It took $DIFF seconds"
echo "re-running"
done

EOF.

The server is only running Apache 2 with Twiki for our documentation on it, as well as 1 other web page, noting too complex so I can't understand why the server keeps getting slower and slower over time.

Machine is a 2.4Ghz with 1GB ram and should not be having load problems.

Any ideas would be great.

Thanks

~K

---

