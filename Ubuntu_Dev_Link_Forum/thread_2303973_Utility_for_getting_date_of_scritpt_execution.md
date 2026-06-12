---
title: "Utility for getting date of scritpt execution"
date: 2015-11-23
forum: Ubuntu Dev Link Forum
---

### Post by udragu on 2015-11-23
Hello all!

I want to create some utility which will allow to get date of start execution and date of finishing some arbitrary script which filename was passed for this utility like a input param[It's assumed that scritp was started week ago and completed execution 1-2 days ago ]. I guess tha't bash is more preferable, But there is some problem , I think that parsing of Ubuntu logs is not simple tasks.
May be there is another way? My be somebody did such thing?
Thanks

---

### Post by Lars Noodén on 2015-11-23
If you're looking for the duration of the script, you can launch it with "time"

```

time /path/to/some/script

```

---

### Post by udragu on 2015-11-23
thnx, for reply.
But, No, I do not want get duration.
I need date of script successful finishing( I assume that it works without some interruption[cron etc])

---

### Post by Lars Noodén on 2015-11-23
Ok.  Then you can either append [date](http://manpages.ubuntu.com/manpages/trusty/en/man1/date.1.html) to the script itself or to the line when the script is called.

```

/path/to/some/script ; /bin/date +"Script done %F %T" > /var/log/script.log

```

If you want the end time only if the script was successful, use &&

```

/path/to/some/script && /bin/date +"Script done %F %T" > /var/log/script.log

```

---

### Post by udragu on 2015-11-23
Hm...all my attempts failed - "script: command not found"
Path is correct.

---

### Post by Lars Noodén on 2015-11-24
Can you show how you are calling the script?

---

### Post by udragu on 2015-11-24
```

user01@amrtkt: sudo /home/user01/scripts/t123.py ; /bin/date +"Script done %F %T" > ~/script.log

```

t123.py
contains just
```

print "123"

```

Result is "t123.py: command not found", Did  I miss something?

---

### Post by Lars Noodén on 2015-11-24
> **udragu said:**
> Result is "t123.py: command not found", Did  I miss something?


Yes.  The first line of the script needs to tell which interpreter to use.  So t123.py should contain the following at the minimum.

```
#!/usr/bin/python

print "123"

```

---

### Post by udragu on 2015-11-25
First
t123.py: command not found - nothing changes
t123.py works successful
Second:
I think you do not understand me.
Of course, there is a way to add some code into script which will save date and the end of it's execution, but the main Idea is to get date postfactum. For example, some script was started.Duration two weeks, just for fun). Execution of it was completed or interrupted(may be power outage was happened). And I need to know was result successful or not. I need something like windows event log but for scripts.

---

### Post by udragu on 2015-12-10
I understand that there is no method if script doesn't logs anything
If somebody intersted in such cases only auditit could be very useful

---

### Post by ian-weisser on 2015-12-10
> **udragu said:**
> but the main Idea is to get date postfactum. For example, some script was started.Duration two weeks, just for fun). Execution of it was completed or interrupted(may be power outage was happened). And I need to know was result successful or not.

I would use a simple lockfile for that.
Lockfiles are usually placed in /run/lock, though that's merely a convention. That directory is destroyed at reboot, so choose a different location if you want persistence.

When the script starts, it creates the lockfile (file creation time = start time)
When the script ends, it logs completion (including start time and end time, if desired) in /var/log and deletes the lockfile.
If the script starts and detects an existing lockfile, you know that a previous instance of the script did not terminate (yet).
If there is no lockfile, previous run was successful.

---

