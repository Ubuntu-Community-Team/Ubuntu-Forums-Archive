---
title: "Rsync Issue"
date: 2010-04-01
forum: Ubuntu Dev Link Forum
---

### Post by Stryker777 on 2010-04-01
Not sure this is the right place to post this.  I have a script to keep some folders synchronized.  It works fine when called manually.  Ex:
/usr/bin/updateFolder vocals

Vocals tells it what to update.  I have 5 cases in the script.

Now I need it to run from crontab so I added the following:
*/5 * * * * /usr/bin/updateFolder vocals > /dev/null 2>&1;

Of course cron tries to run it but nothing ever happens.  Any help?

Here is the rsync part:
rsync --password-file=/home/myuser/.oasswordfile -bHlpogtrv rsync://mywebsite.com:myport/

---

