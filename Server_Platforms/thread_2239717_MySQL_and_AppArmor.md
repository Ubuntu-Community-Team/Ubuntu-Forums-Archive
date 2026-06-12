---
title: "MySQL and AppArmor"
date: 2014-08-15
forum: Server Platforms
---

### Post by guymerritt on 2014-08-15
Okay, I will probably be (1) criticized for posting this in the wrong place, or, (2) simpy not get an answer.  But I sort of presume that folks running servers might have a clue regarding this issue. I downloaded a Debian-based distro called PinguyOS strictly for the purposes of fooling around.  I have multiple "real" servers which use both Ubuntu and Centos.   Unlike most debian folks I compile many of my core packages - and it's generally not a problem.  Anyway, I compiled an older version of MySQL on PinguyOS and got some strange results which, I am guessing, may have something to do with AppArmor.  MySQL built with a few warnings, but, could not connect to a socket - it just would not start.  The logs described MySQL looking for files and directories which had nothing to do with my build commands.  It was looking for a data directory at /var/lib/data (as I recall), looking for a language file at /usr/share/mysql, etc.  It should have been looking for all of these things under the parent directory at /usr/local/mysql (based on how I built the thing....).   The only binary on the system was libmysqlclient18.  It's as if something had hard-coded the wrong paths into the system.  Is this something which AppArmor does?  I did a Google search and found some pages which described problems which were similar, but, not really identical.  Any input would be appreciated.....

---

### Post by JetStorm on 2014-08-15
Have you tried disabling AppArmor and recompiling MySQL again? This way you can be sure that's the cause of the problem.

---

### Post by guymerritt on 2014-08-15
Yep - that's what I'm going to need to do.....just been busy.  Also, I'm going to have to do some reading because I have no idea how you disable AppArmor.  I think I really wondered if anyone knew if having entries related to MySQL, in AppArmor, would cause MySQL (a compiled version) to look in the "wrong" places for MySQL.  in other words, does AppArmor amount to having the paths for MySQL "hard coded" into the system?  I've been drywalling a house - gonna take a break and give it all another whirl, and, attempt to re-configure/disable AppArmor.

---

