---
title: "Upgraded to Karmic, and motd stopped updating"
date: 2009-12-28
forum: Server Platforms
---

### Post by BKonkle on 2009-12-28
I upgraded my server from Jaunty to Karmic over the weekend, and I've been having a little trouble with the motd.  I really like the extra landscape info, and I'd like to begin adding my own scripts to the motd.

At first, after upgrading the motd stopped working altogether.  I fixed it thanks to a quick responder to [this thread]("http://ubuntuforums.org/showthread.php?t=1366442").

Now, the problem is that the motd is not updating at all.  Am I missing a cron script somewhere?  The only thing I have in /etc/cron.d/ is a php5 entry.  I understand that update-motd has been deprecated in favor of the pam_motd module, but I don't understand how that is supposed to be periodically updated.

Any help would be greatly appreciated!  Thanks!

---

