---
title: "Crontab with shell script for creating tar issue"
date: 2011-04-13
forum: Ubuntu Cloud and Juju
---

### Post by hiteshrawal on 2011-04-13
Hi All,
I m using ubuntu 10.04, I have created on simple shell script to create tar of given folder the script is working fine. I have set crontab to run this script periodically it is also working fine on my local pc.
but **on cloud server this same thing gives me unexpected result**.
on server 
- If I run **shell script directly** it is working fine, create tar file and **size of tar file around 20mb**
- If I use **crontab** then it create tar file but **size of tar file around 15kb**

I have also try to view the cron log file, but it didnt give me any error message related with this issue.

Please can any one help me to sort this issue.
I will really appreciate your help.

---

### Post by DaithiF on 2011-04-13
Hi, add logging to capture the stdout and stderr output of the script.

```
* * * * * /path/to/your/script > /path/to/logfile 2>&1

```

one possibility -- the issue described in this thread: [http://ubuntuforums.org/showthread.php?t=825242](http://ubuntuforums.org/showthread.php?t=825242)

if this is the problem, then the very fact of redirecting output as shown above should allow the job to complete.

---

### Post by hiteshrawal on 2011-04-15
> **DaithiF said:**
> Hi, add logging to capture the stdout and stderr output of the script.

```
* * * * * /path/to/your/script > /path/to/logfile 2>&1

```

one possibility -- the issue described in this thread: [http://ubuntuforums.org/showthread.php?t=825242](http://ubuntuforums.org/showthread.php?t=825242)

if this is the problem, then the very fact of redirecting output as shown above should allow the job to complete.
Thanks DaithiF,

It is working.

---

