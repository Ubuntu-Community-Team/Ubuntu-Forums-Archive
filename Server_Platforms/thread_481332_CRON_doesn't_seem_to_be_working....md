---
title: "CRON doesn't seem to be working..."
date: 2007-06-22
forum: Server Platforms
---

### Post by johng4 on 2007-06-22
Setup a LAMP server.  I have added several cron jobs, and none of them seem to work.  Such as the Drupal cron jobs, my dyndns_update script, and my apt-mirror updates.  Cron does appear to be running according to syslog.. but I don't see any output on why its not working for all the cron jobs I've added.

I've put scripts in the /etc/cron.d | /etc/cron.daily | /etc/cron.hourly directories... nothing.
I've put them directly into /etc/crontab, as well as user cron tabs... nothing.

Am I just dense or something?

---

### Post by dbstraffin on 2007-06-22
Maybe you have to restart cron? or send it the update signal?
also in the daily/hourly directories you made suyre they were executable?
is anacron installed?
do the other cron jobs on the system work?

---

### Post by craigp84 on 2007-06-22
Hi dbstraffin,

It's possibly something trivial. Tell me at which part below you can no longer follow along.

Check you can see the process - 
```
ps auxww | grep -i cron
```

As root, verify the permissions around the cron spool dir -
```
[root@aqua]:~# ls -ld /var/spool/cron/crontabs/
drwx-wx--T 2 root crontab 4096 Apr 12 09:25 /var/spool/cron/crontabs/

```

Create a really simple test job as any user allowed to do cron jobs -
```
crontab -e
* * * * * touch /tmp/cron.test
```

If you wait just over 2 mins, you should see the file /tmp/cron.test has been created.

-c

---

### Post by johng4 on 2007-06-22
found the issue.  Apparently there were duplicate scripts running with the wrong path for the scripts/programs to be cron'd.

I corrected the path errors, and it works now.  The paths were put in by program installtions.

---

### Post by riutaro on 2007-06-24
Hi Craig,

I also have difficulty running **cron** jobs.

> **craigp84 said:**
> 
Check you can see the process - 
```
ps auxww | grep -i cron
```
My results are:
```
root      6497  0.0  0.1   2284   900 ?        Ss   10:30   0:00 /usr/sbin/cron
MyUser  10023  0.0  0.1   2896   836 pts/0    S+   11:29   0:00 grep -i cron

```
Sorry don't know if the above means MyUser can see the process.

```
[root@aqua]:~# ls -ld /var/spool/cron/crontabs/
drwx-wx--T 2 root crontab 4096 Apr 12 09:25 /var/spool/cron/crontabs/

```
I get the same results except for the timestamp.



Create a really simple test job as any user allowed to do **cron** jobs -
```
crontab -e
* * * * * touch /tmp/cron.test
```

Oh, yes.  This creates an file in /tmp/, "cron.test".

I know it sounds irritating to people with more knowledge but I have the impression that cron just suddenly stopped working.  I was figuring out how to use **cron** and how to convince it that a space is not the end of the path but part of a filename or foldername.  When I tried something with no space in the path, **cron** worked alright.  Then I tried paths with spaces in the foldername or filename.  Several times it worked.  Then suddenly (sorry to say this) **cron** stopped processing any kind of jobs.

I have been testing with something like this
44 11 * * * /usr/bin/mplayer /home/MyUser/MyAudioFolder/"Music file with space in it.mp3"
(The command and the path have been tested via the terminal.)

---

### Post by Mr. C. on 2007-06-25
Cron and other time-test unix/linux utilities are not fickle. If something isn't working, you'll have to examine your logs and configuration.

What does your cron log show ?

MrC

---

### Post by riutaro on 2007-06-25
This is the content of my crontab.
```
* * * * * touch /tmp/cron.test
* * * * * touch /usr/bin/mplayer /home/foo/MyAudioFolder/"Name with space.mp3"

```

I used the command below to check cron logs:
foo@bar:~$ tail -f /var/log/syslog | grep /USR/SBIN/CRON.
The terminal returns two lines per minute like this
```
Jun 25 19:46:01 bar /USR/SBIN/CRON[9101]: (foo) CMD (touch /tmp/cron.test)
Jun 25 19:46:01 bar /USR/SBIN/CRON[9102]: (foo) CMD (/usr/bin/mplayer /home/foo/MyAudioFolder/"Name with space.mp3")

```

I searched for cron-related files by
foo@bar:~$ ls /etc | grep cron
with the results
```
anacrontab
cron.d
cron.daily
cron.hourly
cron.monthly
crontab
cron.weekly
```

The permissions for the Mplayer binary are:
Owner: root
Access: read and write

Group: root
Access: read only

Others
Access: read only

---

### Post by Mr. C. on 2007-06-25
So you've demonstrated that cron is running your job every minute as you've configured.

You are probably wondering why your mplayer doesn't startup.

Cron does not run its jobs attached to your desktop environment.  Those jobs run in a shell, with minimal environment setup.  Cron is the wrong utility for what you are trying to do.

If you are trying to get movies/sound files to play, use a simple shell script run from *your* terminal sessions.

MrC

---

