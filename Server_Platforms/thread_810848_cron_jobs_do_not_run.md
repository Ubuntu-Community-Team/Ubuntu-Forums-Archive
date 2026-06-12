---
title: "cron jobs do not run"
date: 2008-05-28
forum: Server Platforms
---

### Post by rayhaque on 2008-05-28
I had an old Ubuntu 7.xx server whose hardware bit the dust on me.  I grabbed some new hardware and built an 8.04 server box.  In the process, I carried over two scripts which ran *fine* previously as cron jobs, but now - do not run at all.

Perhaps I am out of the loop on something - but cron does not seem to want to run my jobs, ever, no matter how I enter them.  I have logged in as root and done a 'crontab -e' to add these.  Here is what I get from 'crontab -l'.

```
root@kchlinux:/data/sterling# crontab -l
# m h  dom mon dow   command
1 16 * * * /root/pribackup.sh > /dev/null
1 1 * * * /root/sterling.sh > /dev/null


```

The files exist and are executable ...

```
root@kchlinux:/data/sterling# ls -l /root
total 12
-rw-r--r-- 1 root root 127 2008-05-19 11:41 crontab.txt
-rwxr-xr-x 1 root root 425 2008-05-19 11:41 pribackup.sh
-rwxr-xr-x 1 root root 843 2008-05-19 11:55 sterling.sh

```

I have also tried copying the two shell scripts (pribackup.sh, and sterling.sh) into /etc/cron.daily.  That didn't work either.

What gives?  I tried looking for a log file to read - but I have nothing in /var/log for cron ... and it is running ...

```
root@kchlinux:/data/sterling# ps -aux | grep cron
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root     12609  0.0  0.0   3320   796 ?        Ss   May22   0:00 /usr/sbin/cron
root     14163  0.0  0.0   3004   756 pts/0    R+   16:26   0:00 grep cron

```

Hopefully someone has some ideas for me.  :-)

---

### Post by heebus on 2008-05-28
Try restarting cron 
  /etc/init.d/cron stop
  /etc/init.d/cron start

Once its up and running check your syslogs.

---

### Post by rayhaque on 2008-05-28
```
root@kchlinux:/data/sterling# /etc/init.d/cron stop
 * Stopping periodic command scheduler crond                             [ OK ]
root@kchlinux:/data/sterling# /etc/init.d/cron start
 * Starting periodic command scheduler crond                             [ OK ]
root@kchlinux:/data/sterling# tail /var/log/messages
May 28 13:25:29 kchlinux -- MARK --
May 28 13:45:29 kchlinux -- MARK --
May 28 14:05:29 kchlinux -- MARK --
May 28 14:25:29 kchlinux -- MARK --
May 28 14:45:29 kchlinux -- MARK --
May 28 15:05:29 kchlinux -- MARK --
May 28 15:25:29 kchlinux -- MARK --
May 28 15:45:29 kchlinux -- MARK --
May 28 16:05:29 kchlinux -- MARK --
May 28 16:25:29 kchlinux -- MARK --
root@kchlinux:/data/sterling# tail /var/log/syslog
May 28 16:21:59 kchlinux crontab[14154]: (root) LIST (root)
May 28 16:22:12 kchlinux crontab[14155]: (root) LIST (root)
May 28 16:22:14 kchlinux crontab[14156]: (root) BEGIN EDIT (root)
May 28 16:22:27 kchlinux crontab[14156]: (root) REPLACE (root)
May 28 16:22:27 kchlinux crontab[14156]: (root) END EDIT (root)
May 28 16:22:30 kchlinux crontab[14159]: (root) LIST (root)
May 28 16:23:01 kchlinux /usr/sbin/cron[12609]: (root) RELOAD (crontabs/root)
May 28 16:37:21 kchlinux /usr/sbin/cron[14185]: (CRON) INFO (pidfile fd = 7)
May 28 16:37:21 kchlinux /usr/sbin/cron[14186]: (CRON) STARTUP (fork ok)
May 28 16:37:21 kchlinux /usr/sbin/cron[14186]: (CRON) INFO (Skipping @reboot jobs -- not system startup)

```

What logs *should* I have for cron?

I see no signs of a cron specific log file.

```
root@kchlinux:/data/sterling# ls -l /var/log
total 872
drwxr-xr-x 2 root   root   4096 2008-04-07 17:39 apparmor
drwxr-xr-x 2 root   root   4096 2008-05-19 10:56 apt
-rw-r----- 1 syslog adm   17284 2008-05-28 16:17 auth.log
-rw-r----- 1 syslog adm   43823 2008-05-25 06:47 auth.log.0
-rw-r----- 1 root   adm      31 2008-05-19 10:55 boot
-rw-rw-r-- 1 root   utmp      0 2008-05-19 10:54 btmp
-rw-r----- 1 syslog adm       0 2008-05-25 06:47 daemon.log
-rw-r----- 1 syslog adm    1115 2008-05-19 13:42 daemon.log.0
-rw-r----- 1 syslog adm       0 2008-05-25 06:47 debug
-rw-r----- 1 syslog adm    6414 2008-05-19 13:45 debug.0
drwxr-xr-x 2 root   root   4096 2008-04-22 02:07 dist-upgrade
-rw-r----- 1 root   adm   19332 2008-05-19 13:45 dmesg
-rw-r----- 1 root   adm   20702 2008-05-19 11:14 dmesg.0
-rw-r----- 1 root   adm      59 2008-05-19 10:55 dmesg.1.gz
-rw-r----- 1 root   adm  182326 2008-05-19 11:53 dpkg.log
-rw-r--r-- 1 root   root  24048 2008-05-19 12:47 faillog
drwxr-xr-x 2 root   root   4096 2008-05-19 10:55 fsck
drwxr-xr-x 3 root   root   4096 2008-05-19 11:12 installer
-rw-r----- 1 syslog adm      88 2008-05-27 07:01 kern.log
-rw-r----- 1 syslog adm   62921 2008-05-19 13:45 kern.log.0
-rw-rw-r-- 1 root   utmp 292584 2008-05-28 16:02 lastlog
-rw-r----- 1 syslog adm       0 2008-05-19 10:56 lpr.log
-rw-r----- 1 syslog adm       0 2008-05-19 10:56 mail.err
-rw-r----- 1 syslog adm       0 2008-05-19 10:56 mail.info
-rw-r----- 1 syslog adm       0 2008-05-19 10:56 mail.log
-rw-r----- 1 syslog adm       0 2008-05-19 10:56 mail.warn
-rw-r----- 1 syslog adm    9104 2008-05-28 16:25 messages
-rw-r----- 1 syslog adm   71391 2008-05-25 06:45 messages.0
drwxr-sr-x 2 news   news   4096 2008-05-19 11:14 news
-rw-r--r-- 1 root   root      0 2008-05-19 11:11 pycentral.log
drwxr-x--- 3 root   adm    4096 2008-05-25 06:25 samba
-rw-r----- 1 syslog adm    2920 2008-05-28 16:37 syslog
-rw-r----- 1 syslog adm    4567 2008-05-28 06:25 syslog.0
-rw-r----- 1 syslog adm     499 2008-05-27 06:25 syslog.1.gz
-rw-r----- 1 syslog adm     526 2008-05-26 06:25 syslog.2.gz
-rw-r----- 1 syslog adm     498 2008-05-25 06:25 syslog.3.gz
-rw-r----- 1 syslog adm     491 2008-05-24 06:25 syslog.4.gz
-rw-r----- 1 syslog adm     600 2008-05-23 06:25 syslog.5.gz
-rw-r----- 1 syslog adm     703 2008-05-22 06:25 syslog.6.gz
-rw-r--r-- 1 root   root 295483 2008-05-19 13:45 udev
-rw-r----- 1 syslog adm       0 2008-05-19 10:56 user.log
-rw-rw-r-- 1 root   utmp  14592 2008-05-28 16:02 wtmp

```

---

### Post by fwre01 on 2008-05-28
you could do this to check its running also

```
* * * * * touch /tmp/test.file
```

That should create a file after no more than a minute or two

or tailing the syslog is always a good one as sugested by heebus

```
tail -f /var/log/syslog
```

EDIT: its seems to be starting in your syslog, but i cant see any jobs being executed. There isnt a cron specific log (or at least not as far as im aware)

---

### Post by rayhaque on 2008-05-28
> **fwre01 said:**
> you could do this to check its running also

```
* * * * * touch /tmp/test.file
```


I tried that trick - and it *did* create the file.  So cron is "working" it seems.  But why wouldn't it run my jobs?

I can run these scripts manually as root without a single error.

---

### Post by srs on 2008-05-28
Drop the file extension, e.g., 'sterling' instead of 'sterling.sh'.

---

### Post by fwre01 on 2008-05-28
funny, you are seeing exactly the same problem i have!! it's driving me mad, i can run the commands from the CLI perfectly, and my cron is deff running. But cron just isnt running my commands or scripts containing the commands

what commands are in your scripts btw? you're not using "screen" are you? becasue thats what im trying to cron and it isnt having it at all (i havent tried other commands except that touch test) i am continuing to investigate

...im sorry to say i havent solved it yet, but maybe if we leave this thread someone else might chirp up with a brilliant sollution...

---

### Post by artesvida on 2008-05-28
I've had some cron jobs appear to not run but are actually bombing because the path or other environment variables are not set correctly.  To test, I would have those scripts write out (extensively!) to a log to make sure they aren't failing somewhere in the middle.

---

### Post by Oldsoldier2003 on 2008-05-28
> **artesvida said:**
> I've had some cron jobs appear to not run but are actually bombing because the path or other environment variables are not set correctly.  To test, I would have those scripts write out (extensively!) to a log to make sure they aren't failing somewhere in the middle.

yeah always set env and use fully qualified paths when you are writing a script that is going to be run under cron. having it log along the way is a lifesaver when it comes time to debug it and figure out where the problem lies.

---

### Post by fwre01 on 2008-05-29
Holly Batman! its only gone and worked!

i had written the absolute path for the program, but there was another sneeky command that didnt have the absolute path. Thats fixed it. Thanks very much!

---

### Post by rayhaque on 2008-05-30
Well, I followed the advice here and added paths for any binaries that needed them.  I also removed the .sh extensions from both scripts.

ONE of them ran, but then this script still didn't.  Can anyone see something wrong with it?  When I run it from terminal, it goes without any issues.

```

#!/bin/bash
# Calculate the date in specified format and make a directory with it
TIME=`date +%m-%d-%Y`
/bin/mkdir "/data/proscheduler/$TIME"
cd "/data/proscheduler/$TIME"
# Go get the backup from the server
/usr/bin/wget ftp://10.0.44.17/../../../u2/top/prodback/tarback/backup.tf.Z --user=username --password=password
# Done - Exit

```

---

### Post by artesvida on 2008-05-30
A few suggestions, although I may be grasping at straws:

A full path to "date" (usually /bin/date)
Check permissions on /data/proscheduler
You're using --user option for wget; do you need --password too?

Good luck!

---

### Post by jgni on 2008-05-30
I'm trying to execute the following
```
#!/bin/bash
lynx https://ssl.gratisdns.dk/ddns.phtml?u=*username*&p=*password*&d=*domain*&h=*domain*


``` in /etc/cron.hourly. 
The files permissions is like this 
```
-rwxr-xr-x 1 a70109 a70109 92 2008-05-31 00:41 jans.sh

``` but nothing is working :confused:

Anyone with any ideas?

---

### Post by fwre01 on 2008-05-30
try including the absolute path of lynx (im not sure where that resides)

you could try a "locate lynx" to try and find it

---

### Post by jgni on 2008-05-30
> **fwre01 said:**
> you could try a "locate lynx" to try and find it

[email]root@ubuntu:/etc/cron.hour[/email]ly# locate lynx
/lib/modules/2.6.22-14-server/kernel/drivers/ieee1394/pcilynx.ko
/lib/modules/2.6.24-16-server/kernel/drivers/ieee1394/pcilynx.ko
/usr/share/doc/w3m/examples/keymap.lynx
/usr/share/doc/w3m/ja/examples/keymap.lynx

:(

---

### Post by fwre01 on 2008-05-30
hmmm...OK, try "sudo find / -name lynx"

its bound to be in /usr/bin or somewhere similar.

---

### Post by jgni on 2008-05-30
> **fwre01 said:**
> /usr/bin or somewhere similar.

Of course in /usr/bin :lolflag:

I'm testing now...

---

### Post by jgni on 2008-05-30
Nothing is happening :(
In /var/log/syslog I have -
May 31 01:10:01 ubuntu /USR/SBIN/CRON[30115]: (root) CMD (cd / && run-parts --report /etc/cron.hourly)

---

### Post by fwre01 on 2008-05-30
you could run this in your main crontab file instead of using cron.hourly, to edit your main crontab use:```
crontab -e
```

```
0 * * * * /usr/bin/lynx https://ssl.gratisdns.dk/ddns.phtml?u=username&p=password&d=domain&h=domain
```

the cron.hourly (as i understand) has to be run from the main cron file anyway, it just adds another point of failure IMO, this command will run the command every hour

---

### Post by jgni on 2008-05-30
> **fwre01 said:**
> you could run this in your main crontab file instead of using cron.hourly, to edit your main crontab use:```
crontab -e
```


Now we are getting somewhere. It's executing now!
It's setup to put out an email when executed.
In that mail I'm now getting this:

```
Subject: Cron <root@ubuntu> /usr/bin/lynx https://ssl.gratisdns.dk/ddns.phtml?u=username&p=password&d=domain&h=domain
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <LOGNAME=root>
Date: Sat, 31 May 2008 00:26:01 +0100 (BST)

**Your Terminal type is unknown!**

Enter a terminal type: [vt100]
TERMINAL TYPE IS SET TO vt100

^[[0;7m^OHTTP/1.1 200 OK^[[m^O^[[22;16HP connection^[[m^O^[[63D^[[0;7m^Onding HTTP request.^[[m^O^[[K

^[[?1l^[>

```

Any ideas about that one?

---

### Post by rayhaque on 2008-06-02
Hello all,

Following your advice(s) I was able to get my jobs running again.  I think what did it was including the paths for all executables.  I ran a 'which' against every binary, and then added that path in the shell script.

I also dropped the .sh extension (not sure if that made a difference) and I modified the crontab.

My crontab now looks like this:

root@kchlinux:/data/sterling# crontab -l
# m h  dom mon dow   command
5 1 * * * /root/pribackup >> /data/pribackup.log 2>&1
1 1 * * * /root/sterling >> /data/sterling.log 2>&1


Thanks again for the hints.

---

### Post by Spiny Norman on 2008-09-15
Gone

---

### Post by Spiny Norman on 2008-09-15
I had this problem when moving from 6.06 to 8.04

It appears to be caused by the Debian Almquist shell which is now used in 8.04.

I got it to work by adding this first line to each of my scripts

#!/bin/bash

Then using an absolute path in my crontab, example line

01 2 * * * /root/ShellScript.sh

I also made the scripts executable using chmod. I set my root crontab up in nano (default) editor using crontab -e 

Red herrings for me were adding aything like MAILTO to my crontab and also dropping the .sh I like to use on my scripts, not required for my example.

I am not saying this is the only way, I am new to this but this worked for me. I hope this summarizes the many posts I had to read to extract a workable solution

---

### Post by AncientPC on 2010-04-10
The only thing I changed was rename my script from update.sh to update and it worked.  I was already using absolute paths within the crontab and script.

---

