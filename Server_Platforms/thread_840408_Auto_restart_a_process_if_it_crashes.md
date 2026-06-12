---
title: "Auto restart a process if it crashes"
date: 2008-06-25
forum: Server Platforms
---

### Post by _Dan on 2008-06-25
Hi,

Title says it all...

Is there a simple way to set up my ubuntu web server so that if a specific process crashes and thus no longer exists, a specific command will be run (restarting the process + arguments).

Thanks

---

### Post by unixbills on 2008-06-25
There are many ways to do this.  I use a simple script running all of the time that does just that.  If the job is not running when it checks it starts it.  I run this in a never ending while loop and check every 10 seconds or so.  If a minute is enough you can run out of cron.  Anyway just:
ps -ef|grep -v grep|grep <job-you-want-running> || echo start it here

Here is a test.  On the first pass "firefox" is running so it does nothing.  On the second pass "xxxfirefox" is not found so it runs the echo.

user@desktop:~$ ps -ef|grep -v grep|grep firefox >/dev/null || echo start xxx

user@desktop:~$ ps -ef|grep -v grep|grep xxfirefox >/dev/null || echo start xxx
start xxx

Be very specific on your grep.  Make sure you first "grep -v grep" or script will catch itself running "grep <job>" and think the job was running but it was itself.  Like this:
user@desktop:~$ ps -ef|grep -v grep|grep blabla

Not like this:
user@desktop:~$ ps -ef|grep blabla
user 21675 21551  0 16:03 pts/2    00:00:00 grep blabla
(see the grep caught "blabla" in it's own command line"

Bill

---

### Post by chipperuga on 2010-04-07
This just prints out a line saying "start /usr/bin/firefox". How do you actually find if firefox is running and, if not, start it?

---

### Post by Cosma on 2010-04-07
> **_Dan said:**
> Hi,

Title says it all...

Is there a simple way to set up my ubuntu web server so that if a specific process crashes and thus no longer exists, a specific command will be run (restarting the process + arguments).

Thanks

isn't upstart made just for this purpose?
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by chipperuga on 2010-10-25
Here is [one way of doing it.]("http://ubuntuforums.org/showthread.php?t=1448952")

---

### Post by annoyingrob on 2010-10-25
A helpful function, rather than grepping ps is to use pidof. If will return the process id of a program. For example, "pidof firefox" will return the process id of firefox. If it's not running, it will return 0. 

I don't have the script in front of me, but I wrote a quick script that checked pidof %processname, and if it returned zero, would run %processname. I stuck it into cron so that it ran one a minute. Worked really well.

---

### Post by chipperuga on 2010-10-26
I use the script in a public kiosk environment to ensure Firefox returns to the homepage. When a computer is idle, the screen saver is activated. The script is constantly searching for the screensaver, so when it's active, Firefox is refreshed. Works like a champ.

---

### Post by kenji_03 on 2011-11-20
Not to Necro a topic, but I found a solution for how to make a java application (Minecraft server) Automatically restart.  Read the thread here: [http://ubuntuforums.org/showthread.php?t=1881929](http://ubuntuforums.org/showthread.php?t=1881929)

---

