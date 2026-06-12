---
title: "Cron not running for normal user"
date: 2010-04-06
forum: Server Platforms
---

### Post by mdittmer on 2010-04-06
I recently tried to setup a cron to run on a little backup server I've created, but something isn't working. I'm running a fresh install (from about a week ago) of Ubuntu Sever 9.10.

Here's what I did to setup cron:

```
user@server$ crontab -e
# Inside text editor:
*/5 * * * * python /home/user/scripts/test_script.py
```

test_script.py creates a file whose name contains a date format (to help track when cron runs... just to test).

/etc/cron.allow and /etc/cron.deny do not exist. Crontab reports that my edits to my crontab are successful, as does /var/log/syslog. However, I waited over 1/2 and hour, and syslog did not report running my script (and the files to be created never appeared). The only thin syslog did report in that time was running root's cron.hourly scripts (using run-parts).

Here's what syslog looks like:

```
user@server$ tail -f /var/log/syslog
[...] crontab[pid]: (user) BEGIN EDIT (user)
[...] crontab[pid]: (user) RELOAD (user)
[...] crontab[pid]: (user) END EDIT (user)
[...] CRON[pid]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Any suggestions?

---

### Post by littlegreiger on 2010-04-06
I just tried this on my machine and I figured out that, for me at least, I needed to put absolute paths in my python script. So if it said ```
test.txt
``` I needed to replace it with ```
/home/user/test.txt
```
I'd check that and see if that is your problem too. Of course change the paths accordingly.

---

### Post by mdittmer on 2010-04-06
Thanks! It turned out that it was in fact a path problem. The Python script needed absolute paths to commands and files. I also specified PATH in user's crontab to simplify each crontab line. Also, There may have been an issue with newlines in my crontab before. When I used crontab -l, I noticed no newline at the end of the file which may have been affecting the crontab's behaviour.

Thanks for the tip!

---

