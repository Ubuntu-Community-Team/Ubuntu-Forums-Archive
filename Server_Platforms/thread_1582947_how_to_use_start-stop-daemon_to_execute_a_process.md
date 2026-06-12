---
title: "how to use start-stop-daemon to execute a process"
date: 2010-09-27
forum: Server Platforms
---

### Post by ndefontenay on 2010-09-27
Hi,

I've just installed subversion.
I need to create a script /etc/init.d/svnserve that will start at boot time.

I want to use start-stop-daemon --start so I can track my process and eventually kill it using start-stop-daemon --stop

My problem is that I can't get it to work and the documentation shows no exemple. 

I've created a variable DAEMON as such
DAEMON=svnserve -d -R -r $REPO_ROOT

I've tried start-stop-daemon this way:
start-stop-daemon --start --quiet --oknodo --exec $DAEMON

I get the error start-stop-daemon: option '--exec' requires an argument.

I've replaced $DAEMON by the whole line: svnserve -d -R -r $REPO_ROOT
and got -d is not an option.

I'm not quite sure what to do at that point. If someone has some experience with start-stop-daemon it would be great.

Nico

---

### Post by the_original_billq on 2010-09-27
> **ndefontenay said:**
> Hi,

I've just installed subversion.
I need to create a script /etc/init.d/svnserve that will start at boot time.

I want to use start-stop-daemon --start so I can track my process and eventually kill it using start-stop-daemon --stop

My problem is that I can't get it to work and the documentation shows no exemple. 

I've created a variable DAEMON as such
DAEMON=svnserve -d -R -r $REPO_ROOT

I've tried start-stop-daemon this way:
start-stop-daemon --start --quiet --oknodo --exec $DAEMON

I get the error start-stop-daemon: option '--exec' requires an argument.

I've replaced $DAEMON by the whole line: svnserve -d -R -r $REPO_ROOT
and got -d is not an option.

I'm not quite sure what to do at that point. If someone has some experience with start-stop-daemon it would be great.

Nico

Nico,

You may need to export DAEMON in order for start-stop-daemon to pick it up.  You don't really say how you're setting it, but if it's in a script, it will need to be exported.

You also need to use "-- snserve -d -R -r $REPO_ROOT" (without the quotes) so start-stop-daemon doesn't think -d -R -r $REPO_ROOT are all options it needs to act upon.

HTH,

-Bill

---

### Post by ndefontenay on 2010-09-30
Thanks a lot Bill.

I'm going to try it that way :)

---

### Post by dazz100 on 2013-01-29
Hi
I had the same problem.  The solution is to split the <command> and <arguments>.
The <command> goes after the “-exec” and the arguments go after the “—“.

Note that it is important to include a space before the “-c” argument. If this space is left out, the argument will be mis-interpreted as “---c” instead of “-- -c”.


Below are extracts of my /etc/init.d/ script showing a working example.
```

DAEMON=/usr/bin/motion2
DAEMONARGS=" -c /etc/motion2/motion2.conf"  # Important : leave space before first argument
…

if start-stop-daemon --start --oknodo --exec $DAEMON -b --chuid motion --$DAEMONARGS; then
            log_end_msg 0
        else
            log_end_msg 1
            RET=1
        fi

```

It took me a while to figure out the importance of the space.  Google returned a number of discussions about start-stop-daemon misinterpreting arguments.

The space can be added in the variable (as I have done) or between the "--" and the variable.
eg.  "-- $ARGS"

I tried all sorts of combinations of quote marks and \ / slashes.  The added space fixed my problem.

Dazz

---

