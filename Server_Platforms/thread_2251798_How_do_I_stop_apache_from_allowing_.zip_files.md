---
title: "How do I stop apache from allowing .zip files?"
date: 2014-11-06
forum: Server Platforms
---

### Post by RavenLX on 2014-11-06
I want to stop scripts like wordpress wp-cron and backups and the like from creating .zip or .tgz or .tar files on the server. In fact, I'd rather stop these types of scripts from running on the server altogether. Is there a way to do this?

Right now I'm using Ubuntu 10.04 server (old I know). I'm going to create a new 14.04 server in the coming months but right now I really need to stop this on the 10.04 server as I don't have time to build a new server right now.

---

### Post by Habitual on 2014-11-07
> **RavenLX said:**
> I want to stop scripts like wordpress wp-cron and backupsYou mean wordpress 'backups'?

for wp crons you can use this in your wp-config.php file ```
define( 'DISABLE_WP_CRON', true );
```

If wp-cron is making these backups, you should be set.
If it's some other 'backups' being run, you'll have to be more specific.

Please let us know...

---

### Post by RavenLX on 2014-11-15
I'm very sorry I didn't get to reply until now. Setting up a brand new PC took a lot of time. Anyway, the server I'm working on is shared hosting, with many people who have their own web sites on it. I want to be able to stop them from using scripts like WordPress backup scripts. I can't manually track down and find everyone's wp-config and if I did they can always change it back. I was hoping for something that they can't change.

---

