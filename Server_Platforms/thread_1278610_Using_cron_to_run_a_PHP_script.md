---
title: "Using cron to run a PHP script"
date: 2009-09-29
forum: Server Platforms
---

### Post by Fliggerty on 2009-09-29
Hey all,

I've got a publicly accessible PHP script that I want to run automatically every 5 minutes.  It harvests some data from an SQL database, writes that data to a file, then FTPs that file to a remote server.  The script runs just fine when I run it from a browser.

I've not done much with cronjobs in the past, so I've done a lot of searching and reading about it the past couple of days.  I was able to succesfully run a cronjob that writes a simple file to my home directory.

The user that I have set the cron up for is a member of the www-data group which owns the directory the PHP script is in, and it is group executable (775.)

This is the crontab entry:

1,6,11,16,21,26,31,36,41,46,51,56 * * * * /var/www/ghfchat/users/sendonline.php

For some reason it doesn't appear to be running; the file is not written on either system.

I've also tried this for testing purposes:

* * * * * /var/www/ghfchat/users/sendonline.php

And finally, as per a forum suggestion I read, I set it up as root as so:

sudo -s
crontab -e

* * * * * /var/www/ghfchat/users/sendonline.php


Does anyone have a suggestion as to what I can try to get this functioning?

TIA!

---

### Post by undecim on 2009-09-29
You can't execute the script directly... It needs to be run by php. Easiest thing to do would be to use wget output to /dev/null.

also, you can use */5 to represent each number divisible by 5 (unless being 1 minute ahead of the minutes you posted is an issue?)

just put this in a file in /etc/cron.d/
```
*/5 * * * * nobody wget -O http://localhost/ghfchat/users/sendonline.php
```though you may also be able to call php to execute the script (i.e. bypassing apache), but I have no idea how to do that.

EDIT: Also, make the script in /etc/crond.d/ executable with "chmod a+x /etc/cron.d/[scriptname]

EDIT: ACK! just realized I left the username field out of that... Files in cron.d./ need a username field... fixed just now. (using the user "nobody" which is sort of an unprivileged root user. After all, no administrative permissions required to view a web page is there?)

---

### Post by brian mcgee on 2009-09-30
Try:
```

* * * * * php /var/www/ghfchat/users/sendonline.php
```

---

### Post by Fliggerty on 2009-09-30
Thanks guys!

It's funny, I just sorted out the problem and came by to see if anyone had replied.  I got it right.  :D

I finally got it work by installing php5-cli, then modifying the crontab entry like so:

*/5 * * * * php /home/fliggerty/sendonline.php


I appreciate the help!

--Fligg

---

### Post by Mike The KID on 2010-11-23
I'm trying to do the same thing and I just want to make sure I'm placing the cron config file in the same location you did

```
/etc/cron.d/myconfile
```

I've read that I can use

```
crontab -e
```

which will open a nano editor but I don't have a clue where that file gets saved and every time I've tried putting my alterations there nothing works. Same goes for uploading a text file then using

```
crontab mytextfile.txt
```

which then i can use the crontab editor i see that text file loaded into the cron but still no luck getting it to run.

---

### Post by brian mcgee on 2010-12-02
> **Mike The KID said:**
> I'm trying to do the same thing and I just want to make sure I'm placing the cron config file in the same location you did

```
/etc/cron.d/myconfile
```

I've read that I can use

```
crontab -e
```

which will open a nano editor but I don't have a clue where that file gets saved and every time I've tried putting my alterations there nothing works. Same goes for uploading a text file then using

```
crontab mytextfile.txt
```

which then i can use the crontab editor i see that text file loaded into the cron but still no luck getting it to run.

This should work:
```
crontab -e
```

Then make your changes and save the file. It will be installed automatically. Here is some documentation that you might find helpful.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

To view your current crontab, run the following command:

```
crontab -l
```

---

### Post by chrislynch8 on 2010-12-03
Hi,

You need something like the following

* * * * * cd /var/www/application; php -f yourfile.php

That will work - I'm using this for one I must run.

Also make sure your php cli is working

---

