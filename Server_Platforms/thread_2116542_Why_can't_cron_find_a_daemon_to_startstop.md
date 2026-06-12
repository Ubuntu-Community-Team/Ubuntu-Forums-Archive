---
title: "Why can't cron find a daemon to start/stop?"
date: 2013-02-16
forum: Server Platforms
---

### Post by dazz100 on 2013-02-16
Hello

I am trying to start and stop the applications <motion> and <motion2> using crond. The cron jobs are running as root.  I have tried </etc/init.d/motion stop> and <service motion stop> type commands.  Both commands work from the command line as sudo.  Neither work in cron.

The cron jobs run as root so permissions shouldn't be a problem.

I don't know why cron can't find the jobs.  What can cause cron to be unable to find commands????

Below are the commands in cron.

```

# Shutdown motion
 00 21 * * * /etc/init.d/motion stop
 00 21 * * * /etc/init.d/motion2 stop

# Start motion
 00 05 * * * /etc/init.d/motion start
 00 05 * * * /etc/init.d/motion2 start


```

Below is the email received from the failed cron job.  I get the same error message for all attempts to start/stop the daemons.

```

 * Stopping motion2 detection daemon motion2
/etc/init.d/motion2: 78: /etc/init.d/motion2: start-stop-daemon: not found
   ...fail!

```

---

### Post by dazz100 on 2013-02-18
Hi

It seems that the default cron root environment path setting does not include the location of the program I want to run.

I fixed this by doing a:
echo $PATH  
in bash then pasting the path into the first line of root crontab

$PATH=<pasted in path>   

Thanks to peter pilsl for this answer.

---

### Post by Habitual on 2013-02-18
> **dazz100 said:**
> Hi

It seems that the default cron root environment path setting does not include the location of the program I want to run.You nearly nailed it.
Cron doesn't have an environment (or at least a very limited one).

/full/path/to/scripts.xx is always good form, modified "$PATH" or not.

---

