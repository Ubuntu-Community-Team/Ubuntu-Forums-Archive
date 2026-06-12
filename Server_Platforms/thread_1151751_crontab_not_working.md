---
title: "crontab not working"
date: 2009-05-07
forum: Server Platforms
---

### Post by wonderingwout on 2009-05-07
Hi,

Recently I installed a new Ubuntu server (8.04 LTS) with Rails and all went very smooth.
Things are running better than ever.

There's only one little thing I can't figure out.
The crontab is not running.

This might be a silly question, but I always used systems that have the crontab ready to go.
On Ubuntu I had to install it but I can't get it to work.

And also, there are various files named 'crontab' in the system.
The command crontab -e opens a different file than the one fount in /etc.

I'm a tiny bit confused.
Could you guys give me some hints?

Thanx in advance!

---

### Post by cdenley on 2009-05-07
> **wonderingwout said:**
> Hi,

Recently I installed a new Ubuntu server (8.04 LTS) with Rails and all went very smooth.
Things are running better than ever.

There's only one little thing I can't figure out.
The crontab is not running.

This might be a silly question, but I always used systems that have the crontab ready to go.
On Ubuntu I had to install it but I can't get it to work.

And also, there are various files named 'crontab' in the system.
The command crontab -e opens a different file than the one fount in /etc.

I'm a tiny bit confused.
Could you guys give me some hints?

Thanx in advance!

Each user has their own crontab. The crontab for root would be at /var/spool/cron/crontabs/root, but you shouldn't edit this file directly.
```

man crontab

```
The file /etc/crontab is the system-wide crontab, and not edited by the "crontab" command (as explained in the comments at the top of the file).

---

### Post by albinootje on 2009-05-07
> **wonderingwout said:**
> 
And also, there are various files named 'crontab' in the system.
The command crontab -e opens a different file than the one fount in /etc.

Yes. There is indeed /etc/crontab which I've seen people use before.

I stick to "crontab -e" to help me prevent syntax errors, and that has always worked for me.

Are you trying to run a script ? Does it have the right permissions ?
What about errors in the logfiles ? 
Did you set up smtp and an alias for "root" ? If you did this then you can usually receive the cron errors by email.

---

### Post by wonderingwout on 2009-05-07
Well now I edited the file through:

```
crontab -u root -e
```

I'm running a simple job to generate a new xml file for a website.
In the crontab file I've put:

```
05 * * * * /usr/local/bin/generate.sh
```

But still it doesn't work.
When I run:

```
/usr/local/bin/generate.sh
```

in the cli it works perfectly.
I guess I need to start digging in the log files. to see what's going wrong.

---

### Post by cdenley on 2009-05-07
The mistake I usually make with scripts started by cron is that they don't have environment variables like "PATH", so you need to use full paths for any commands you run.

---

### Post by wonderingwout on 2009-05-07
Could have been a problem but I already tried that.
This is what my crontab file looks like:

```
PATH=/usr/bin:/usr/local/bin:/bin:/usr/sbin:/usr/bin

05 * * * * /usr/local/bin/generate.sh
```

Curl, the only command used in the generate.sh file is located in /usr/bin/curl
Should cron be enabled maybe?

---

### Post by albinootje on 2009-05-07
> **wonderingwout said:**
> 
```

05 * * * * /usr/local/bin/generate.sh
```


You want this to be run every 5 minutes ? 
If so, please check these :
[http://ubuntuforums.org/showthread.php?t=83356](http://ubuntuforums.org/showthread.php?t=83356)
[http://ubuntuforums.org/showthread.php?t=184915](http://ubuntuforums.org/showthread.php?t=184915)

---

### Post by cdenley on 2009-05-07
That runs every hour 5 minutes after the hour. If you want every 5 minutes:
```

*/5 * * * * /usr/local/bin/generate.sh

```
I tested it, and it seems to work for me. Did you make it executable? If you're still having problems, post the script, because everything else is correct.

---

### Post by wonderingwout on 2009-05-07
Yes!
Great.

The */5 did the trick.
Actually quite stupid of me to think that 05 would be every 5 minutes :o

Anyway, muchas gracias!
Thanx for the help.

---

