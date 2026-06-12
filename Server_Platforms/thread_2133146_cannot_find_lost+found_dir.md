---
title: "cannot find lost+found dir"
date: 2013-04-07
forum: Server Platforms
---

### Post by AvengerX9 on 2013-04-07
I get this error report in my servers's mailbox 

> /etc/cron.daily/logrotate:
error: httpd:1 duplicate log entry for /var/log/apache2/access.log
error: found error in /var/log/apache2/*log , skipping
/etc/cron.daily/standard:

Some local file systems lack a lost+found directory. This means if the
file system is damaged and needs to be repaired, fsck will not have
anywhere to put stray files for recovery. You should consider creating
a lost+found directory with mklost+found(8).

The following lost+found directories were not available:

/var/www/lost+found

What does it mean ? I thought the lost+found directory were made by itself it it coudnt find it. Any information on this kind of error?


Thanks for reading :)

---

### Post by conradin on 2013-04-07
Is this on your compromised server? 
anyhow, you could use the command:
```

cd /var/www/
sudo mklost+found

```

why do you have duplicate logs? 
can you move one of them to an appended filename?
drwx------ 2 H H    49152 Apr  7 16:30 lost+found/        #mklost+found permissions
drwxrwxr-x 2 H H     4096 Apr  7 16:31 lost+found1/       #mkdir permissions

if your wondering about  the difference in those commands.

---

### Post by AvengerX9 on 2013-04-07
Yea, its on my compromised server or the one they used for spamming, but I haven't received any complaints since then so I guess its okay now :) Also I have no idea why I have multiple logs. Where can you see that ?

---

### Post by AvengerX9 on 2013-04-08
Now I'm getting this

> /etc/cron.daily/logrotate:
error: httpd:1 duplicate log entry for /var/log/apache2/access.log
error: found error in /var/log/apache2/*log , skipping

I get one of these errer reports a day

---

### Post by conradin on 2013-04-08
In your position I would seriously consider (clean) re-installation save your content and start over fresh. Get the guys here to help you secure your server. 
 
Your logs are cooked, hacked, tampered. The source of your error is in logrotate.
personally, cooked logs intrigue me, I would save them and read them later, but for practical purposes, you can just delete all your logs. New ones will be generated
```

sudo logrotate -d  /var/log/apache2/access.log
sudo logrotate -f  /var/log/apache2/access.log


```

please show the output of commands:
```

ls- al /var/log/apache2/
sudo ufw status verbose

```

You may want to monitor your outgoing traffic as well. Just beacuse your ISP isnt complaining, doenst mean nothing is wrong.
you could also post your site here, or if its an adult site post me directly, so we can see if there are things to fix there.

---

### Post by AvengerX9 on 2013-04-08
The output for the first command were

> 
roger@roger-G31T-M7:~$ ls -al /var/log/apache2/
total 151668
drwxrwxrwx  2 root adm      4096 Apr  7 12:48 .
drwxrwxrwx 20 root root     4096 Apr  8 07:43 ..
-rw-r-----  1 root adm  13763581 Apr  8 17:07 access.log
-rw-r--r--  1 root adm  34409955 Apr  7 07:55 access.log.1
-rw-r-----  1 root adm   1522003 Mar 31 07:49 access.log.2.gz
-rw-r-----  1 root adm   1112520 Mar 24 07:47 access.log.3.gz
-rw-r-----  1 root adm  28187327 Apr  8 17:07 error.log
-rw-r--r--  1 root adm  75874162 Apr  7 07:55 error.log.1
-rw-r-----  1 root adm         0 Apr  7 07:55 other_vhosts_access.log
-rw-r-----  1 root adm     23240 Apr  6 01:31 other_vhosts_access.log.1
-rw-r--r--  1 root root     3204 Apr  5 02:21 other_vhosts_access.log.2.gz
-rw-r-----  1 root adm         0 Apr  7 07:55 ssl_access.log
-rw-r--r--  1 root root   365788 Apr  5 01:39 ssl_access.log.1


and the second one were

> Status: inactive

---

### Post by AvengerX9 on 2013-04-09
I think your right. I should do a clean install :) Now the server shuts down once Im in. I have no idea how to fix that.

This time I think I want to install the Ubuntu Server. Is there much difference between normal ubuntu and the ubuntu server ?

---

### Post by conradin on 2013-04-10
Once your install is complete:

Install and configure Firewall - ufw
Secure shared memory - fstab 
SSH - Disable root login and change port. 
disable ICMP requests.

80% of your future problems with hackers will be dealt with. (deliberately not saying solved.)
good luck.

---

### Post by AvengerX9 on 2013-04-10
Thanks. Are doing the install now on another computer. Ubuntu server :)

---

