---
title: "Should a &quot;find&quot; process ever be running when I look at top?"
date: 2014-02-24
forum: Server Platforms
---

### Post by Lido on 2014-02-24
I just ran "top" on my 12.04 LTS LAMP server and noticed a heavy load on the server momentarily and "find" showed up in the list of processes even though I hadn't run it myself (and I'm the only user on the system). Is that normal or is that a sign I should be looking for intrusions?

---

### Post by nerdtron on 2014-02-24
It should not be running in the background unless a another process (or script or program) used a find command.
Who is the user running the find command? Are there any other users logged in? Are there any crontab scripts that make use of the find command (such as find all files and backup).

---

### Post by Lido on 2014-02-25
There are no other users logged in. I had just run apt-get update and upgrade, but everything was held back so I don't think there should have been any lingering process from that. When I run ps aux | grep find I get this under my user name:
```
790  0.0  0.0   8108   936 pts/0    S+   21:11   0:00 grep --color=auto find
```
...which looks like the only thing with find in it is the grep command that's searching for it.

In syslog about every half hour there's a line like this:
```
CRON[32541]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
```

---

### Post by nerdtron on 2014-02-25
If I understand it correctly, that is a cron job performing the find command to delete the files with creation time of greater than the "maxlifetime".
Anyway, what programs have you recently installed? Something should have triggered this.

---

### Post by Lido on 2014-02-25
Nothing installed since I set it up in the first place. Just a LAMP web server. Tried to keep it as bare as I could.

---

### Post by volkswagner on 2014-02-25
From the output of you ps aux command that does not indicate find is running.

try this:

```
 ps aux | grep tommyHilfiger
```

returns:

```
root     16335  0.0  0.0   9388   936 pts/0    S+   08:15   0:00 grep --color=auto tommyHilfiger
```

What you are seeing is the actual grep command returning.

When you run that command, you should see at least two results if the process is running;

example:```
root@buntu:/var/log# ps aux | grep smbd
root     16427  0.0  0.0   9388   932 pts/0    S+   08:17   0:00 grep --color=auto smbd
root     18555  0.0  0.6 126696  6936 ?        Ss   Feb24   0:00 smbd -F
root     18557  0.0  0.3 127112  3072 ?        S    Feb24   0:03 smbd -F
ro       18693  0.0  0.6 129804  6520 ?        S    Feb24   0:25 smbd -F
```

---

### Post by steeldriver on 2014-02-25
It's a standard php5 cron job for cleaning saved session files, I think

```

$ cat /etc/cron.d/php5
# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete

```

See also --> [http://stackoverflow.com/questions/20742638/fuser-process-php5-cron-job-using-high-amounts-of-cpu](http://stackoverflow.com/questions/20742638/fuser-process-php5-cron-job-using-high-amounts-of-cpu)

---

### Post by Lido on 2014-02-25
Thanks Steeldriver.

---

