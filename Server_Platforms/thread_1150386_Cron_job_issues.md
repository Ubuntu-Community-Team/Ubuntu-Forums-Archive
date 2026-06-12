---
title: "Cron job issues"
date: 2009-05-06
forum: Server Platforms
---

### Post by m3bik on 2009-05-06
I have a cronjob that executes a local php script. I currently have it set to:

> wget -O [http://localhost/script.php](http://localhost/script.php)

There is no actual output from the script. Nothing is downloaded or saved to my server. I do, however, get emails sent to my user account letting me know the cronjob was successful.

How can I do this cronjob with now email, no output, nothing... I've tried adding

```
> /dev/null &> /dev/null
```

to the end of the command, but I still get an email sent to the user account.

Is there an easier way to do this cronjob that does NOT send emails?

I ask this because this cronjob is done every 5 minutes and that can be a lot of emails after a few days! I know I could set a cronjob to erase the email file at /var/mail/user but then it would send another email saying that cronjob was successful...

---

### Post by nquinnathome1 on 2009-05-06
Just to be sure; have you tried running the script in a browser or calling it with PHP CGI (if you have that installed)?

You should call it like:
```
wget -O /dev/null http://localhost/script.php
```

Adding /dev/null sends the output to a null device so the file isn't saved to disk.

Also, regarding your cronjob mails; you don't have to have an email sent when you run a job; you could always set a job that doesn't mail you when it deletes the mails.

---

### Post by m3bik on 2009-05-06
I just want to run the php script every 5 minutes, not save anything to the server, and NOT get an email sent to the user account after the cronjob. How ever I have to do that is how I'll do that...

I've tried

> wget -O /dev/null [http://localhost/script.php](http://localhost/script.php)

> wget -O /dev/null [http://localhost/script.php](http://localhost/script.php) > /dev/null &> /dev/null

> wget [http://localhost/script.php](http://localhost/script.php) > /dev/null &> /dev/null

I've even tried lynx instead of wget.

I'm not even sure if each one is completely correct, it's just that I'll do anything for no more emails after a cronjob!

Here's an example of what the emails look like:

> From [email]user@ubuntu.inet[/email]  Wed May  6 16:00:02 2009
Return-Path: <user@ubuntu.inet>
X-Original-To: user
Delivered-To: [email]user@ubuntu.inet[/email]
Received: by ubuntu (Postfix, from userid 1000)
        id 5226E849D; Wed,  6 May 2009 16:00:02 -0500 (CDT)
From: [email]root@ubuntu.inet[/email] (Cron Daemon)
To: [email]user@ubuntu.inet[/email]
Subject: Cron <user@ubuntu> wget -O /dev/null [http://localhost/cron.php](http://localhost/cron.php) > /dev/null &> /dev/null
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/user>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=user>
Message-Id: <20090506210002.5226E849D@ubuntu>
Date: Wed,  6 May 2009 16:00:02 -0500 (CDT)

--2009-05-06 16:00:02--  [http://localhost/cron.php](http://localhost/cron.php)
Resolving localhost... 192.168.2.124
Connecting to localhost|192.168.2.124|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 0 [text/html]
Saving to: `/dev/null'

     0K                                                        0.00 =0s

2009-05-06 16:00:02 (0.00 B/s) - `/dev/null' saved [0/0]


---

### Post by John Cheng on 2009-05-06
> **m3bik said:**
> I just want to run the php script every 5 minutes, not save anything to the server, and NOT get an email sent to the user account after the cronjob. How ever I have to do that is how I'll do that...

I've tried







I've even tried lynx instead of wget.

I'm not even sure if each one is completely correct, it's just that I'll do anything for no more emails after a cronjob!

Here's an example of what the emails look like:

Yikes, did you accidentally overwrite your /dev/null as a file?

What is the output of "stat /dev/null", it should look like

```

stat /dev/null
  File: `/dev/null'
  Size: 0               Blocks: 0          IO Block: 4096   character special file
Device: fh/15d  Inode: 3298        Links: 1     Device type: 1,3
Access: (0666/crw-rw-rw-)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-05-05 21:04:45.000000000 -0700
Modify: 2009-05-05 21:04:45.000000000 -0700
Change: 2009-05-06 06:03:11.465959640 -0700

```

If it has become a real file (instead of a character device), then you can delete it. Once deleted, recreate it with

```

mknod -m 666 /dev/null c 1 3

```

In your cron job listing, you should not use the -O option, in other words:

```
wget -O /dev/null http://localhost/cron.php > /dev/null &> /dev/null
```

Simply the following will be fine:

```
1 2 3 4 * wget http://localhost/cron.php &> /dev/null
```

---

### Post by m3bik on 2009-05-07
This is my outcome for:

stat /dev/null

>   File: `/dev/null'
  Size: 0               Blocks: 0          IO Block: 4096   character special file
Device: eh/14d  Inode: 5152        Links: 1     Device type: 1,3
Access: (0666/crw-rw-rw-)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-04-27 16:37:20.000000000 -0500
Modify: 2009-04-27 16:37:20.000000000 -0500
Change: 2009-05-05 22:25:19.752173230 -0500


It looks right to me.

---

### Post by m3bik on 2009-05-07
/dev/null looks right and I've used

```
wget http://localhost/cron.php &> /dev/null
```

and I still get emails...

---

### Post by m3bik on 2009-05-07
Is this just impossible to do?

---

### Post by gombadi on 2009-05-07
according to the man page for wget there is a quiet option.

> 
       -q
       --quiet
           Turn off Wget’s output.


Have you tried it?

---

### Post by SciFi-Bob on 2009-05-07
One option is to disable all logging from cron, like this:

Alter the last line in /etc/default/cron to this:

EXTRA_OPTS="-L 0"

This will disable audit logging of all cron events.
I don't know if this will affect the mails, but it's certainly stopping the syslog from being filled up with cron lines.

Anyway, try a "man cron" for options to the cron daemon.

---

