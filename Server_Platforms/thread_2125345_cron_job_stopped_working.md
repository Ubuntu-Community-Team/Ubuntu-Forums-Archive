---
title: "cron job stopped working"
date: 2013-03-13
forum: Server Platforms
---

### Post by sdmike6 on 2013-03-13
I have a server running ubuntu server 11.04 x64. This server also has LDAP running on it which I think might be playing a role in my cron job not running.

The cron job looks like this:
```
MAILTO=backups@foobar.com
#min hour, day, month, weekday
* * 1 * * deploy /usr/bin/rsync -avzP deploy@cldserver.foobar.net:/srv/data/backups/redis_backups /srv/data/redis_backups
```

Now I can run this command as the user and it works by using these commands:
```
$ sudo -u deploy -i 
$  /usr/bin/rsync -avzP deploy@cldserver.foobar.net:/srv/data/backups/redis_backups /srv/data/redis_backups
```

But for whatever reason when I touch the cron job to reload it I still do not see the backups coming in.

What could be causing my cron job to not work?

---

### Post by papibe on 2013-03-13
Hi sdmike6.

A couple of ideas:
[LIST]
[*]Your cron job run on the 1th of the month. For testing purposes I would change it for a shorter span.
[*]Unattended rsync scripts need ssh keys with no passphrase. Are they set properly? 
[/LIST]
Regards.

---

### Post by sdmike6 on 2013-03-21
This was an issue I was having with LDAP or Pam.

Unfortunately I didn't have enough time to troubleshoot this. I do know that when I removed LDAP that the local users were not having the Authentication issues anymore. I'm going to setup another server with similar setup and see if I get this issue again.

---

