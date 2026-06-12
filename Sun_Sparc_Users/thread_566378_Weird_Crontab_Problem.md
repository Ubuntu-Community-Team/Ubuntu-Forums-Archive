---
title: "Weird Crontab Problem"
date: 2007-10-03
forum: Sun Sparc Users
---

### Post by RobSand on 2007-10-03
Greetings To All!

I am running Solaris 10 in a sparc environment.

Here is the deal:

In /var/spool/cron/crontabs, there is a cron user named "sys".  If I do a
crontab -l sys,  it returns:

# 0 * * * 0-6 /usr/lib/sa/sa1
# 20,40 8-17 * * 1-5 /usr/lib/sa/sa1
# 5 18 * * 1-5 /usr/lib/sa/sa2 -s 8:00 -e 18:01 -i 1200 -A

I have tried to modify the above job by changing the first line...and uncommenting all 3 lines, so that it will read the following at run time:

0,5,10,15,20,25,30,35,40,45,50,55 * * * 0-6 /usr/lib/sa/sa1
20,40 8-17 * * 1-5 /usr/lib/sa/sa1
5 18 * * 1-5 /usr/lib/sa/sa2 -s 8:00 -e 18:01 -i 1200 -A

I am making the above mentioned modification as user "sys", who owns this particular cron job.

The problem is this:

For some weird, unexplainable reason,  the modified cron job:

0,5,10,15,20,25,30,35,40,45,50,55 * * * 0-6 /usr/lib/sa/sa1
20,40 8-17 * * 1-5 /usr/lib/sa/sa1
5 18 * * 1-5 /usr/lib/sa/sa2 -s 8:00 -e 18:01 -i 1200 -A

_will always revert back to its original default_ to read:

# 0 * * * 0-6 /usr/lib/sa/sa1
# 20,40 8-17 * * 1-5 /usr/lib/sa/sa1
# 5 18 * * 1-5 /usr/lib/sa/sa2 -s 8:00 -e 18:01 -i 1200 -A

Anyone have any ideas what could be causing this?  This one has me scratching my head...

Your replies are greatly appreciated!

Sincerely

RobSand

---

### Post by Zurd on 2007-10-03
You should say what command you use to modify it... or are you using a text editor to manually edit the crontab file?

Else try 'sudo crontab -u sys -e', it should work fine.

---

### Post by RobSand on 2007-10-03
> **Zurd said:**
> You should say what command you use to modify it... or are you using a text editor to manually edit the crontab file?

Else try 'sudo crontab -u sys -e', it should work fine.


I used:   crontab -e sys

---

