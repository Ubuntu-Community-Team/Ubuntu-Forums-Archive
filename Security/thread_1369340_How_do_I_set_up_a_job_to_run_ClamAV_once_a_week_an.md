---
title: "How do I set up a job to run ClamAV once a week and email me the results?"
date: 2009-12-31
forum: Security
---

### Post by humphreybc on 2009-12-31
At the bottom of [this documentation]("https://help.ubuntu.com/community/ClamAV") it very briefly explains how to set up a job to scan for viruses.

I'd like to make a recurring event, say, at midday every second Monday that runs freshclam to update the virus database, then runs clamscan -r / and emails me the results (showing only infected files).

I'd also like it to know when the computer was off at that time, and to defer the scan to the next time it's on.

(This is a home file server)

Thankyou so much for your help!

---

### Post by humphreybc on 2009-12-31
I was just thinking, it would be even cooler if the server could automatically turn on at 3am in the morning once a fortnight, run a file system check before the drive is mounted, then run freshclam and clamscan, email me the results of both the filesystem check and the virus scan, and then shutdown all on its own.

Is this asking too much to set up? :P

---

### Post by CharlesA on 2010-01-01
This is the script I used when I ran clamAV.

```
clamscan -ri --exclude-dir=^/sys\|^/proc\|^/dev / | mail -s "ClamAV Scan Results for `date +%D`" email@email.domain
```

You'd just have to throw it in a file and add it to a crontab.

---

### Post by actetylcholine on 2010-01-02
I have a similar issue as the OP; I want ClamAV to run weekly on my laptop and mail the results to me. Charles, when you say throw it in a file, would that be a .sh file? or .txt file? And how would I point crontab to the file?

---

### Post by BkkBonanza on 2010-01-02
To make a crontab for this you would type,

sudo crontab -e

this starts an editor for the cron (sudo for the root crontab, but if the cron runs under your user name then don't use sudo)

Now enter the cron statement into this editor and save. (It will use your default editor).

The cron statment consists of some time values and the program/script to run. I won't list it all here - just google "man cron" and you'll find lots of tutorials on cron.

There's probably a gui interface for this somewhere but I don't know where they hide it.

---

### Post by CharlesA on 2010-01-02
> **actetylcholine said:**
> I have a similar issue as the OP; I want ClamAV to run weekly on my laptop and mail the results to me. Charles, when you say throw it in a file, would that be a .sh file? or .txt file? And how would I point crontab to the file?

I just had it in a file called "avscan" with no extension, just execute permissions.

You just add an entry to the root crontab with *sudo crontab -e*.
If I wanted to run it daily (at midnight), it would look something like this:

```
0 0 * * * /path/to/script
```

---

### Post by HermanAB on 2010-01-03
There is a set of directories in /etc called cron.hourly, cron.daily, cron.weekly and so on.  If you drop a script in there and make it executable, then cron will do the rest.

---

### Post by humphreybc on 2010-01-04
So, if I put:

```

clamscan -ri --exclude-dir=^/sys\|^/proc\|^/dev / | mail -s "ClamAV Scan Results for `date +%D`" email@email.domain

```

into an empty file with no extension, make it executable and stick it in cron.weekly then it will be run every week, regardless?

Does ClamAV have a sort of "quick scan" function? The last scan took over 2 hours... although I suppose this doesn't matter for a server that runs 24/7.

---

### Post by CharlesA on 2010-01-04
I don't know if there is a quick scan option for clamav, since I switched to BitDefender (due to too many false positives)

That's pretty much all you need to do: Stick it in a file, and add it to cron.

I think the weekly setting (scan every Sunday at Midnight) is:
```
0 0 * * 0 /path/to/script
```

---

### Post by BkkBonanza on 2010-01-05
Wait. Either stick it in a file in /etc/cron.weekly or add it with "crontab -e" but don't do both or it will run twice.

You should probably add "#!/bin/bash" as the first line of script file if you go that way.

---

### Post by humphreybc on 2010-01-05
I've put it in cron.weekly and made it executable - do I need to add bin/bash?

---

### Post by BkkBonanza on 2010-01-05
I'm not sure it will fail in this case but generally scripts start with a line indicating what shell/language they are to be run with. If nothing else, it's good form.

---

### Post by humphreybc on 2010-01-05
Neat. And what about my second post in this thread?

I presume the lack of replies means everyone is too afraid to answer haha

---

### Post by BkkBonanza on 2010-01-05
I had to go back and re-read to see what your second question was... ahh.

The main problem is getting your machine to power up. If you have another machine on the net that could trigger it into a net boot then that may work. You would have to set up some BIOS option (if available) to allow WakeOnLAN. I've never played with that but I've read of people doing it. If not that then maybe one of those cheap power timers that people use to keep thieves away when they go on vacations. Even then you would have to have the BIOS set to boot on power-on always.

Once powered up you could script the needed scans etc. or just leave the normal cron job running as long as the power comes on a bit before the cron is due to run. Final command in script would be to "sudo poweroff".

---

### Post by humphreybc on 2010-01-05
I've got Wakeonlan working fine with the server. I can power it on by sending a magic packet from my laptop.

Hmm so what you're saying is that power on can only be achieved by external sources. Damn.

Oh well, it looks like it'll be running 24/7 now anyway so that's not a problem anymore!

Thanks for your help. Come next Monday if I don't have an email in my inbox then i'll be back here for more help haha

---

### Post by BkkBonanza on 2010-01-05
Maybe you can get a magic packet sent by somewhere on the web. There is cron services out there that can be setup to make a http request at certain times. I used one for a while - don't recall the site name now.

---

### Post by humphreybc on 2010-01-06
Meh I won't bother now that it runs 24/7.

Since we're on the topic of Cron jobs, may I ask this:

How can I run a sudo apt-get update and apt-get upgrade every week at the same time as the AV Scan? Is it just a matter of creating another script for that and sticking it in cron.weekly?

Also, I should run freshclam before each clamscan - can I just put 'freshclam' one line above the clamscan command in my avscan script?

---

### Post by BkkBonanza on 2010-01-06
Yes, easy enough to add another script or add it to the same script. If you add another one it likely runs concurrently with the first script. If you add it into your current script then it would be run either before or after depending on which order you use.

The gui desktop (if you have that) has update manager options for auto updating too.

---

### Post by humphreybc on 2010-01-10
Ha, didn't work. It's Monday here and I haven't got an email in my inbox.

---

### Post by BkkBonanza on 2010-01-10
Check your logs to see if it ran. It should have run but if not there may be an error message. Or it may be a script problem.

cat /var/log/syslog | grep cron

You should see a line for cron.weekly.

Note that these regular crons are not controlled by crontab but by /etc/anacrontab.

For more info about the timing read, man anacron. It counts 7 days between runs so may not be on Monday. If you need it to be at a specific time then don't use cron.weekly, instead set a time with crontab.

---

### Post by humphreybc on 2010-01-11
```

benjamin@benjamin-server:~$ cat /var/log/syslog | grep cron
Jan 11 07:17:01 benjamin-server CRON[4789]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 08:17:01 benjamin-server CRON[4809]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 09:17:01 benjamin-server CRON[4829]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 10:17:02 benjamin-server CRON[4849]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 11:17:01 benjamin-server CRON[4869]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 12:17:01 benjamin-server CRON[4889]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 13:17:01 benjamin-server CRON[4909]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 14:17:01 benjamin-server CRON[4930]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 15:17:01 benjamin-server CRON[4949]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 16:17:01 benjamin-server CRON[4969]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 17:17:01 benjamin-server CRON[4989]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 18:17:01 benjamin-server CRON[5009]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 19:17:01 benjamin-server CRON[5029]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

---

### Post by BkkBonanza on 2010-01-11
Looks like it hasn't run yet. You will see a line cron.weekly when it has.

You can look at the /var/spool/anacron/cron.weekly file to see what date was last run, then add 7 days.

---

### Post by humphreybc on 2010-01-11
I don't have an anacron directory there...

```

benjamin@benjamin-server:~$ sudo nano /var/spool/anacron/cron.weekly
[sudo] password for benjamin: 
benjamin@benjamin-server:~$ cd /var/spool/anacron/cron.weekly
-bash: cd: /var/spool/anacron/cron.weekly: No such file or directory
benjamin@benjamin-server:~$ cd /var/spool/anacron/
-bash: cd: /var/spool/anacron/: No such file or directory
benjamin@benjamin-server:~$ cd /var/spool/anacron
-bash: cd: /var/spool/anacron: No such file or directory
benjamin@benjamin-server:~$ cd /var/spool
benjamin@benjamin-server:/var/spool$ ls
cron  mail
benjamin@benjamin-server:/var/spool$ cd cron
benjamin@benjamin-server:/var/spool/cron$ ls
atjobs  atspool  crontabs

```

---

### Post by BkkBonanza on 2010-01-11
That's weird. I'm on 9.10 as well and have that directory.
Maybe try find and see if it's located elsewhere,

find /var -name cron.weekly

(don't worry about permission messages)

Anacron is different from cron in that it will run jobs if they were missed while the system was down. Don't know why you haven't got that. You should have /etc/init.d/anacron. Also you could see what you get from,

status anacron

---

### Post by humphreybc on 2010-01-11
```

benjamin@benjamin-server:~$ find /var -name cron.weekly
find: `/var/cache/ldconfig': Permission denied
find: `/var/run/sudo': Permission denied
find: `/var/spool/cron/atspool': Permission denied
find: `/var/spool/cron/atjobs': Permission denied
find: `/var/spool/cron/crontabs': Permission denied
find: `/var/lib/php5': Permission denied
benjamin@benjamin-server:~$ status anacron
status: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

```

---

### Post by BkkBonanza on 2010-01-11
Seems like something's messed up with dbus.
Maybe try to reboot and try status again on some services that should be running,

status cron
status dbus

Could be dbus has been nuked somehow. Both above services should return a running  status with a pid. It seems like dbus isn't. You may be able to start it but probably you're better off to restart everything and see if it comes up normally.

---

### Post by humphreybc on 2010-01-11
After restarting:

```

benjamin@benjamin-server:~$ status cron
status: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
benjamin@benjamin-server:~$ status dbus
status: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

```

---

### Post by humphreybc on 2010-02-04
Still haven't got this working :(

---

### Post by CharlesA on 2010-02-04
I have the same error if I run "status cron." Running 9.10 x64.

I checked /var/spool/cron on my server and all I have are:

```
drwxrwx--T 2 daemon daemon  4096 2009-12-19 14:28 atjobs
drwxrwx--T 2 daemon daemon  4096 2009-09-15 15:29 atspool
drwx-wx--T 2 root   crontab 4096 2010-01-11 10:25 crontabs

```

Cronjobs are running fine for me.

---

### Post by rookcifer on 2010-02-04
OP,

Unless you have a Windows box on your network, you are wasting your time with all of this.  If you do have a 'doze box, then, carry on. ;)

---

### Post by ikt on 2010-02-04
> **rookcifer said:**
> OP,

Unless you have a Windows box on your network, you are wasting your time with all of this.  If you do have a 'doze box, then, carry on. ;)

it would still be nice to have this work in case one does have a windows box on the network..

---

### Post by drdos2006 on 2010-02-24
What some people are doing is setting up a Web interface in a box to turn on equipment.
[http://www.siliconchip.com.au/cms/A_111807/article.html](http://www.siliconchip.com.au/cms/A_111807/article.html)

The unit is connected to router and powered permanently.

More discussions are here.

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1372624.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1372624.html)

:)

---

