---
title: "/bin/sh: - : invalid option"
date: 2012-05-16
forum: Server Platforms
---

### Post by donotdisturb on 2012-05-16
[FONT=&quot]I've built a new server running Ubuntu 12.04 LTS and I'm using it to host the KBpublisher knowledge base software. The install went fine however when I'm setting up the required scheduled tasks in crontab (detailed here: [http://www.kbpublisher.com/kb/Setting-up-scheduled-tasks_238.html](http://www.kbpublisher.com/kb/Setting-up-scheduled-tasks_238.html)) I'm encountering the error "/bin/sh: - : invalid option."

The task looks like this: */5 * * * * -c /etc/php5/apache2 /usr/bin/php [installdirectory]/admin/cron/daily.php

Any thoughts as to what might be going on? I understand that it is probably a root shell issue but I'm not sure how to troubleshoot since I'm somewhat of an Ubuntu n00b.
[/FONT]

---

### Post by maverickaddicted on 2012-05-16
I have set up many cron job on hosting server, but none of them looks like this - 
```
*/5 * * * * -c /etc/php5/apache2 /usr/bin/php [installdirectory]/admin/cron/daily.php
```

mostly cron jobs look like this -

```
*/5 * * * * /usr/bin/php5 [installdirectory]/admin/cron/daily.php
```

You can confirm the php5 path using this command -

```
whereis php5
```

If it is installed, it will show you something like this -
```
php5: /usr/bin/php5 /etc/php5 /usr/lib/php5 /usr/share/php5 /usr/share/man/man1/php5.1.gz

```

---

### Post by snotplop on 2012-05-16
> **donotdisturb said:**
> [FONT=&quot]I've built a new server running Ubuntu 12.04 LTS and I'm using it to host the KBpublisher knowledge base software. The install went fine however when I'm setting up the required scheduled tasks in crontab (detailed here: [http://www.kbpublisher.com/kb/Setting-up-scheduled-tasks_238.html](http://www.kbpublisher.com/kb/Setting-up-scheduled-tasks_238.html)) I'm encountering the error "/bin/sh: - : invalid option."

The task looks like this: */5 * * * * -c /etc/php5/apache2 /usr/bin/php [installdirectory]/admin/cron/daily.php

Any thoughts as to what might be going on? I understand that it is probably a root shell issue but I'm not sure how to troubleshoot since I'm somewhat of an Ubuntu n00b.
[/FONT]

It looks like it's complaining about the "-c" switch in your from line.
Try removing it.

Also, there are multiple crontabs:
```
$ crontab -e
``` edits your user cron,
```
$ sudo crontab -e
``` edits the root cron

From the sound of it, you should be using the latter.

-Andy

---

### Post by donotdisturb on 2012-05-16
Okay so I set it up to run as root, removed the -c option, and updated the php5 path so now it looks like this:
```
*/5 * * * * usr/bin/php5 [installdirectory]/admin/cron/daily.php
```However, when I run it I get this error: ```

Site error: the file <b>[installdirectory]/admin/cron/daily.php</b> requires the ionCube PHP Loader ioncube_loader_lin_5.3.so to be installed by the site administrator.
``` FYI ionCube is installed and functioning. On the developer site they suggest that when this error is encountered to try adding the -c switch and the path to the php.ini file, which is what I had in the original cron job: 
```
*/5 * * * * -c /etc/php5/apache2 /usr/bin/php [installdirectory]/admin/cron/daily.php
```So I guess what I've figured out is that running the job as root doesn't solve the problem, and I can't get rid of that "-c" switch. Any suggestions about what to try next? Thanks.

---

### Post by hawkmage on 2012-05-16
One suggestion and one comment.  

There is very little in the way of a PATH defined in cron so you have to worry about finding any libs/executable outside the usual locations like /bin.

So what I will usually do is create a shell script with all of the logic needed to run the process you want to do and call that script from cron.  As part of this script use full paths and set the PAT to all the required directories.

---

### Post by koenn on 2012-05-16
you have a slash missing in the crontab
```
*/5 * * * * usr/bin/php5 [installdirectory]/admin/cron/daily.php
```
obviously, that should read  /usr/bin/php5
also, you do understand that you should replace [installdirectory] with a real path, don't you ? just checking. 


furthermore:
> On the developer site they suggest that when this error is encountered to try adding the -c switch and the path to the php.ini file, 

I'd read that as "add the -c switch + the path to the php.ini to the php interpreter", so that would look something like
```

/usr/bin/php5  -c /path/to/php.ini  [...]/admin/cron/daily.php

```
note that you'll need to also replace /path/to/php.ini with a valid path, and copmplete the path to daily.php

run it in a shell to see the errors, is any, before you add it to cron.

---

### Post by donotdisturb on 2012-05-16
> **koenn said:**
> 
I'd read that as "add the -c switch + the path to the php.ini to the php interpreter", so that would look something like
```

/usr/bin/php5  -c /path/to/php.ini  [...]/admin/cron/daily.php

```note that you'll need to also replace /path/to/php.ini with a valid path, and copmplete the path to daily.php

run it in a shell to see the errors, is any, before you add it to cron.
 
Thanks! (And yes I did know to replace [installdirectory] with a real path:).) Here is the working syntax:

```
/usr/bin/php5 -c /etc/php5/apache2/php.ini [installdirectory]/admin/cron/daily.php
```

---

