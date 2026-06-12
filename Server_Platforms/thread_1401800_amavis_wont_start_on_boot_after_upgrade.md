---
title: "amavis wont start on boot after upgrade"
date: 2010-02-08
forum: Server Platforms
---

### Post by noway2 on 2010-02-08
This last weekend, I decided to do a server distribution upgrade from 9.04 to 9.10.  All appeared to go well at first, but I have since discovered a slight problem.  The system acts as a mail server using postfix with amavis and spamassassin.  I have discovered that after the upgrade, amavis no longer starts automatically upon re-boot.  This is a problem because incoming and outgoing mail are passed through amavis for spam and virus checking.  With amavis not starting, nothing is listening on the port that postfix attempts to send to and mail simply gets 'deferred' due to a connection refused.

This has only been a problem following the upgrade.  Amavis may be started manually via "sudo /etc/init.d/amavis start" and it starts without apparent error.  After being started, the daemon process shows up in a ps list and the port shows as listening in a netstat list. I have verified that all of the configuration files (related to amavis, spam assassin, and postfix) are the same, following the upgrade.  The amavis script is linked to in the RC.d files for the appropriate run levels.  I have removed and re-installed amavis and spam assassin to no avail.  I have been unable to locate a log entry with any error message to indicate why it is not starting.

Does anyone have any ideas or suggestions?

---

### Post by noway2 on 2010-02-09
While I am extremely surprised at the lack of any sort of response to this thread, I appear to have finally stumbled on to a solution.  This thread from 3.5 years ago lead me to a resolution: [http://ubuntuforums.org/showthread.php?t=277838](http://ubuntuforums.org/showthread.php?t=277838).

There is a current thread on launchpad [https://bugs.launchpad.net/ubuntu/+source/amavisd-new/+bug/251377](https://bugs.launchpad.net/ubuntu/+source/amavisd-new/+bug/251377) indicating that this is a problem again (as of Jan 31st).  

Apparently there is a change to amavis in the 05-node-id configuration file effecting how the fqdn gets read and this is causing some difficulty.

---

