---
title: "Cannot Restart Apache"
date: 2011-02-09
forum: Server Platforms
---

### Post by ubunwhat on 2011-02-09
Ok, so I have had a build of Apache on my Ubuntu system for quite some time and it has worked flawlessly.  No worries, no hassles.  I only use it as a development server so everything is accessed via localhost.  Anyway, I turned my computer on today and for some reason I cannot get Apache running.  This makes no sense as it was running just fine when I turned the computer off.  When I try to restart the server I get the following error:

* Restarting web server apache2                                                Warning: DocumentRoot [/home/user/public_html/] does not exist
 ... waiting Warning: DocumentRoot [/home/user/public_html/] does not exist

I assure you that it most certainly does exist!  Anyway, a visit to the log was not at all helpful.  The last lines in the log are as follows:

[Wed Feb 09 17:08:53 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 09 17:15:49 2011] [error] [client 127.0.0.1] File does not exist: /home/user
[Wed Feb 09 17:15:50 2011] [error] [client 127.0.0.1] File does not exist: /home/user

Again, everything is exactly where it was before.  Nothing has moved.  Any help on this would be greatly appreciated.

---

### Post by gdonwallace on 2011-02-09
I know You probably where, but did the command to restart get executed as root or sudo?  Since it is looking in a specific /home/user/ directory; where you that user.  One last thing, check the permissions on the directories and sub-directories and make sure there is not sticky bit.  (This is a lower case t at the end of the permissions.  Generally happens to the /tmp directory, but can happen to others as well.)

Also, you might try running the restart command with the full path (i.e. /usr/sbin apache restart)  I know in some programs, I have to do that on our server; but don't remember if apache was one of them.

Good luck.

---

### Post by wongo888 on 2011-02-09
Did you recently upgrade the Apache daemon? Did a conf file get clobbered during an upgrade?

Check your conf syntax:

```
$ apache2ctl -t
Syntax OK
```

Check your settings:

```
$ apache2ctl -S

```

---

### Post by ubunwhat on 2011-02-09
Thank you for the replies.  It was indeed a permissions issue.  Feeling pretty stupid right now...

---

