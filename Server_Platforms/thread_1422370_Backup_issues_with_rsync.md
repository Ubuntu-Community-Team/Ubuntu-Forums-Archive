---
title: "Backup issues with rsync"
date: 2010-03-05
forum: Server Platforms
---

### Post by webdirector on 2010-03-05
Hi,

I have a server with a second drive where i want to backup my data from 3 directories.

the second drive is /media/HD2 to get daily , weekly and monthly backups I put this in the crontab:

40 2    * * *   root    rsync –av --delete /var /media/HD2/daily/var
40 3    * * *   root    rsync -av --delete /etc /media/HD2/daily/etc
10 3    * * *   root    rsync -av --delet /mysqlbackup /media/HD2/daily/mysql
40 4    * * 5   root    rsync -av --delete /media/HD2/daily /media/HD2/weekly
15 5    2 * *   root    tar -cvjf /media/HD2/monthly/monthly.tar.bz2 daily/

my problem is when i run "rsync –av --delete /var /media/HD2/daily/var" at the command line I get this error message:
 "
rsync: --delete does not work without -r or -d.
rsync error: syntax or usage error (code 1) at main.c(1440) [client=3.0.6]
root@server1:/#
"

I tried it with the -r:

 rsync –rav --delete /var /media/HD2/daily/var

I also get this error message again:

rsync: --delete does not work without -r or -d.
rsync error: syntax or usage error (code 1) at main.c(1440) [client=3.0.6]
root@server1:/#

any ideas what I am doing wrong ?

Thanks for the help

p.s. what directories  would you backup ?

---

### Post by lykwydchykyn on 2010-03-05
"rsync -av --delete" should work, so either you've encountered a bug or there's a typo somewhere in your scripts.

Searching on the error shows that  a few bugs were reported with this issue, but turned out to be missed typos on the part of the bug reporter.

Is the above the EXACT output of your crontab?  If so "delete" is mispelled in one line.  If not, paste the actual contents.

EDIT: I just notice in your command, the "-av" is actually a "&#8211;av" -- notice the difference between the hyphen and the dash.  Two different characters.  This may be causing rsync to ignore the -av.  Did you copy and paste the command off a website or something like that?

If so, try retyping the commands from scratch.

---

### Post by webdirector on 2010-03-05
yes that worked !

Thanks !

What other directories would you backup ?

---

### Post by lykwydchykyn on 2010-03-05
> **webdirector said:**
> yes that worked !

Thanks !

What other directories would you backup ?

It kind of depends on what the server does.

Personally I try to get all my services concentrating data in a common location, such as /home or /srv.  I try to get away from having data under /var, since there is so much junk I don't care to back up under /var (the apt cache, for example).

I can see backing up /etc/ in many cases, particularly if you have a lot of complex or regularly changing configurations.

---

