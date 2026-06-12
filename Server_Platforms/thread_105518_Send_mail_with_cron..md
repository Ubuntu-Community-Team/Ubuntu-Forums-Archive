---
title: "Send mail with cron."
date: 2005-12-18
forum: Server Platforms
---

### Post by xeo_pt on 2005-12-18
Hi,
I have a server running ubuntu and I need to receive in may office a
mail with lets say the disk usage.

How can I put the server sending e-mail with cron.

thanks in advance for your help.

---

### Post by schilcha on 2005-12-18
Here's a script that checks (started by cron), if updates are available. If so, it sends a mail. You can adapt it to your needs. (I can't really remember, if the command "mail" is installed by default.)
```

#!/bin/bash

TMPFILE=/tmp/ubuntuchecker.out

apt-get update

apt-get upgrade --dry-run > $TMPFILE
if tail -1 $TMPFILE | grep '^0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded\.' &> /dev/null
then
  /bin/rm $TMPFILE
else
  mail -s 'New updates available for ralph!' user@myhost.mydomain < $TMPFILE
  /bin/rm $TMPFILE
fi

```

---

### Post by LordHunter317 on 2005-12-18
To get cron to send mail is really quite simple:[list=1][*]Configure your local MTA to send mail[*]Have a CRON script write anything to stdout or stderr.  Cron will mail that output.[*]If you need to mail that to another user, then in the crontab, set MAILTO to whatever user needs to be mailed, like so:```
MAILTO=bob
* * * * 1-5 /usr/local/bin/maintaince.sh
```[/list]

As for that script, better would be:```
#!/bin.sh

apt-get update > /dev/null 2>&1

if ( apt-get upgrade --dry-run 2>/dev/null | tail -1 | \
     grep -vq '^0 upgraded, 0 newly installed, 0 to remove, and 0 not upgraded' )
then
    echo "New updates for $HOSTNAME"
fi
```Untested, but it ought to work just fine.

---

### Post by xeo_pt on 2005-12-19
```
Configure your local MTA to send mail
```

Thats it how do I cofigure the MTA to send mail? any tutorial out there?

Thank you fellows for you help.

Regars.

---

