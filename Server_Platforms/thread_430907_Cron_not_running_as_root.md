---
title: "Cron not running as root"
date: 2007-05-02
forum: Server Platforms
---

### Post by sucellus on 2007-05-02
```

harris@svn:/tmp$ crontab -l
# m h  dom mon dow   command
* * * * * /bin/echo "Hello World, I'm working" >> /tmp/cronlog.harris.txt
harris@svn:/tmp$ sudo -s
root@svn:/tmp# crontab -l
# m h  dom mon dow   command
* * * * * /bin/echo "Hello World, I'm working" >> /tmp/cronlog.txt


root@svn:/tmp# ll
total 28
-rw-r--r-- 1 harris domain users    25 2007-05-02 15:06 cronlog.harris.txt
drwx------ 2 root   root         16384 2007-04-20 06:59 lost+found
-rw-r--r-- 1 root   root          1322 2007-05-02 11:49 svn_backup.erout
-rw-r--r-- 1 root   root             0 2007-05-01 16:23 svn_backup.stout
drwxr-xr-x 3 root   root          4096 2007-05-01 09:18 vmware-config0
root@svn:/tmp# ll
total 28
-rw-r--r-- 1 harris domain users    50 2007-05-02 15:07 cronlog.harris.txt
drwx------ 2 root   root         16384 2007-04-20 06:59 lost+found
-rw-r--r-- 1 root   root          1322 2007-05-02 11:49 svn_backup.erout
-rw-r--r-- 1 root   root             0 2007-05-01 16:23 svn_backup.stout
drwxr-xr-x 3 root   root          4096 2007-05-01 09:18 vmware-config0
root@svn:/tmp# cat cronlog.harris.txt
Hello World, I'm working
Hello World, I'm working
Hello World, I'm working

```

As you can see cron is working perfectly for a regular user, but anything I add to root's crontab doesn't get run.  Any ideas why?

Thanks in advance

---

### Post by kidders on 2007-05-03
Hi there,

To be honest, it would surprise me if this is the cause of your problem, but could you check that the very last character in root's user-specific crontab is a line break? Just a shot in the dark.

---

### Post by sucellus on 2007-05-04
I had checked before, but I just tripple checked and thats definitely not the problem.

---

### Post by kidders on 2007-05-04
I suspected you might have. I'd say you've also checked that /etc/cron.allow and /etc/cron.deny (if they exist) aren't to blame.

Does anything interesting crop up in /var/log/syslog when root's tasks are supposed to be executing?

---

### Post by sucellus on 2007-05-04
Well, /etc/cron.allow and /etc/cron.deny don't exist.  I uncommented the line sin syslog.conf to log cron to its own file but left the other reference to cron in the messages section.

/etc/syslog.conf (abreviated w/ only cron related info):
```

cron.*                          /var/log/cron.log

*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages



```

/var/log/messages doesn't show anything related to cron, at least since the last time it rolled over.
/var/log/cron.log shows the user tasks running, and it shows when root edits crontab, but it doesnt show root's tasks running, nor does it show any cron related errors.

Here is a sample of cron.log:
```

May  4 08:49:01 svn /USR/SBIN/CRON[601]: (drosenbloom) CMD ('/usr/bin/mail -s test drosenbloom@svn < ""')
May  4 08:50:01 svn /USR/SBIN/CRON[607]: (drosenbloom) CMD ('/usr/bin/mail -s test drosenbloom@svn < ""')
May  4 08:51:01 svn /USR/SBIN/CRON[643]: (drosenbloom) CMD ('/usr/bin/mail -s test drosenbloom@svn < ""')
May  4 08:51:58 svn crontab[692]: (drosenbloom) BEGIN EDIT (drosenbloom)
May  4 08:52:01 svn /USR/SBIN/CRON[697]: (drosenbloom) CMD ('/usr/bin/mail -s test drosenbloom@svn < ""')
May  4 08:52:12 svn crontab[692]: (drosenbloom) REPLACE (drosenbloom)
May  4 08:52:12 svn crontab[692]: (drosenbloom) END EDIT (drosenbloom)
May  4 08:53:01 svn /usr/sbin/cron[10224]: (drosenbloom) RELOAD (crontabs/drosenbloom)
May  4 09:03:48 svn crontab[756]: (root) BEGIN EDIT (root)
May  4 09:03:58 svn crontab[756]: (root) END EDIT (root)
May  4 09:03:59 svn crontab[761]: (root) BEGIN EDIT (root)
May  4 09:04:06 svn crontab[761]: (root) REPLACE (root)
May  4 09:04:06 svn crontab[761]: (root) END EDIT (root)
May  4 09:05:01 svn /usr/sbin/cron[10224]: (root) RELOAD (crontabs/root)

```

---

### Post by kidders on 2007-05-04
Argh this is a frustrating problem! I think the absence of any error messages rules out problems accessing /var/spool (that might cause trouble for cron, when it tries to execute scripts, and so on).

It occurred to me (in desperation) that Ubuntu could be hard-wired to ignore root's crontab for some reason, so I checked my own system. Simple tasks similar to the example in your o/p work as expected though, on Feisty...

[SIZE=1]```
$ uname -a
Linux x2 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux
```

```
$ sudo apt-get -s --reinstall install anacron      [COLOR=Sienna][I was interested in the version numbers][/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Inst anacron [2.3-13ubuntu2] (2.3-13ubuntu2 Ubuntu:7.04/feisty)
Conf anacron (2.3-13ubuntu2 Ubuntu:7.04/feisty)
```

[/SIZE]I'm completely stumped. :-( Have you tried blindly reinstalling your cron tools & crossing your fingers?

Sorry I can't offer you anything more constructive, but I didn't want to see your post drop off the end of the unanswered posts lists without *some* sort of attempt to help.

It might be worth filing a bug report. Whether there is a real bug here, or you have somehow managed to break cron without realising it is irrelevant, if you ask me ... it shouldn't be possible for someone with your knowledge (which appears high) to break something, and then be unable to find any evidence of the problem!

---

### Post by sucellus on 2007-05-04
I guess I never mentioned but I'm running Feisty Fawn
```
root@svn:/tmp# uname -a
Linux svn 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686 GNU/Linux

```

I tried reinstalling anacron, but that didn't seem to help either.

I am an experienced linux user, but this is my first time using Ubuntu or really any debian based distro.  I've fooled around with them, but not more than that, until now.  I've mostly worked with RedHat based distros since until recently thats what Oracle has certified on and its just been easier to work with a single distro in our organization.  I'm branching out :-)

Thanks for the help even if the problem isn't fixed yet.  I'll post here if I find an existing bug or after I file one.

Thanks again

---

### Post by kidders on 2007-05-04
> **sucellus said:**
> I am an experienced linux userI guessed that hehe, in which case you'll certainly appreciate how daft your problem is! It has _got_ to be a bug of some sort. I hope it gets sorted out quickly for you.

By the way, don't forget to dpkg-reconfigure anacron (just to be sure), when reinstalling.

---

### Post by sucellus on 2007-05-04
Here is the bug I posted:
[https://bugs.launchpad.net/ubuntu/+source/cron/+bug/112355](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/112355)

---

### Post by mbower on 2007-05-04
I seem to be hanving the same issue.  Cron job tasks (root) that were running (under Edgy) no longer are running.

---

