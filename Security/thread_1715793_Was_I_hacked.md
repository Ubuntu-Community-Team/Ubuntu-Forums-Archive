---
title: "Was I hacked?"
date: 2011-03-27
forum: Security
---

### Post by wily_one on 2011-03-27
I'm running a simple WordPress site on Ubuntu 10.10, which runs inside a VM.  I installed LAMP and WordPress, and tried to lock things down as much as possible.

Being the paranoid person I am, checking my logs this morning I notice some anomalies:

File /var/log/apache2/error.log starts with:
```
PHP Warning:  Directive 'safe_mode' is deprecated in PHP 5.3 and greater in Unknown on line 0
[Sun Mar 27 07:35:03 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
```File /var/log/apache2/error.log.1 ends with:
```
[Sun Mar 27 07:35:03 2011] [notice] Graceful restart requested, doing restart
```This looks like apache was restarted, but what's odd is I was not awake or online at 07:35. (yes the system time is correct)   Is there some internal process that would cause apache to restart automatically, or does this indicate some external entity did something to cause it?

---

### Post by SeijiSensei on 2011-03-27
My logs were rotated this morning at about the same time.  Do you see files with .1 extensions in /var/log and a similar timestamp?  It's probably just the result of logrotate being run.

---

### Post by wily_one on 2011-03-27
Yes, I've both access.log.1 & error.log.1.

But does the log rotate actually restart apache?

---

### Post by d3v1150m471c on 2011-03-27
cross reference incoming and outgoing traffic with the time it was restarted. also, check out psad and denyhosts.

---

### Post by cariboo on 2011-03-27
I have the same thing in /var/log/apache2/error.log, my server has no access to the outside world, it's only for internal usage:

> [Sun Mar 27 06:53:01 2011] [notice] Apache/2.2.14 (Ubuntu) DAV/2 PHP/5.3.2-1ubuntu4.7 with Suhosin-Patch configured -- resuming normal operations

---

### Post by SeijiSensei on 2011-03-27
> **wily_one said:**
> Yes, I've both access.log.1 & error.log.1.

But does the log rotate actually restart apache?

Yes, it has to restart the daemon so it will begin writing to the new log.  Take a look at /etc/logrotate.d/apache2.  You'll see these lines:

```

        postrotate
                /etc/init.d/apache2 reload > /dev/null
        endscript

```

It actually does a "graceful" reload rather than a full restart, but the outcome from the point of view of logging is the same.

---

### Post by wily_one on 2011-03-27
OK cool - thanks guys.  There's nothing critical on this VM, but I am trying to be as secure as possible.

As of now I'm checking logs manually from the shell.  Is there a better way, like a GUI dashboard or something?  Something non-resource intensive preferably.

---

### Post by Sporkman on 2011-03-28
> **wily_one said:**
> OK cool - thanks guys.  There's nothing critical on this VM, but I am trying to be as secure as possible.

As of now I'm checking logs manually from the shell.  Is there a better way, like a GUI dashboard or something?  Something non-resource intensive preferably.

"logwatch" is pretty good.

---

