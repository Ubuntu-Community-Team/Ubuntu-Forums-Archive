---
title: "Rsync fails..."
date: 2006-08-23
forum: Server Platforms
---

### Post by ScatterBrain on 2006-08-23
I have two machines - one running Hoary (I know, I know) named Columbia and the other running Dapper named Challenger.  I'm trying to keep a directory on Columbia sync'ed on Challenger.

Every night for the past two nights, the process seems to have failed:

```
rsync: read error: Connection timed out (110) rsync error: error in rsync protocol data stream (code 12) at io.c(584)
rsync: connection unexpectedly closed (1595221 bytes received so far) [generator] rsync error: error in rsync protocol data stream (code 12) at io.c(434)
``` 
I'm running Rsync in daemon mode on Columbia and running the following command on Challenger:

```
rsync -a --stats --compress --delete columbia.klcollins.org::backup/ /data/columbia/backup/
``` 
Could it be that the different versions of Rsync on the two machines is causing the problem?  If not, can someone else give me a clue as to how to cure the problem?

BTW:  If it matters, I'm doing the syncing across an aDSL line with a maximum upload speed of 384kb/s.

---

### Post by jordilin on 2006-08-23
Try to do an rsync with two different folders (origin->target) in your Dapper Drake machine and see if this problem happens too. Try to do it within your hoary machine as well. If no problems arise, then the problem is a consequence of the connection.

---

### Post by MJN on 2006-08-23
Give Q3 and Q4 from the debugging FAQ a go...
 
[http://samba.anu.edu.au/rsync/issues.html](http://samba.anu.edu.au/rsync/issues.html)
 
(and let us know how you get on!)
 
I suspect it could well be down to the version of Rsync in Hoary not supporting one of the options sent to it by that in Dapper. Check both log files - any clues?
 
Mathew

---

### Post by ScatterBrain on 2006-08-23
Based on some of the hints on the RSYNC troubleshooting page, I'm currently running the rsync command by hand and through an SSH tunnel.  In addition, I'm not using the rsync daemon on Columbia either.

If this test works without any failures (it's about 68% through now), I'll probably change my script to run it this way and use SSH keys to handle authentication.

Time will tell.  Thanks for the help.  I'll let you know how it turns out.

---

### Post by ScatterBrain on 2006-08-25
Well it appears as though running the rsync through an SSH tunnel has fixed my problem.  My backup processes have run successfully for two night in a row and has just started on a third.

Thanks for all the help.

---

