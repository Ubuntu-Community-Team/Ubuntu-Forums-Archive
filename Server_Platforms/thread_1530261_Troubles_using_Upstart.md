---
title: "Troubles using Upstart"
date: 2010-07-13
forum: Server Platforms
---

### Post by freiquell on 2010-07-13
Hi there,

I've been searching this topic for quite a while. But since upstart is new I never really found a pleasant answer.

My problem actually is very simple.
I'm developing something which does quite some changes to the system - so I need to handle some daemons by script.

For example I need to start/stop squid - quite an easy task before upstart, now I just cant find a safe way...

As I have learned the syntax is like this:
```
initctl stop/start squid
```I already need a workaround to find out if upstart is used - since the .deb package I create should also work on Debian...

Now I discovered that when squid is already down and I do again a stop this causes an error which stops the installation of the package....

Well, you see I just have a lot of trouble doing something very simle. I mean I can keep on coding special solutions but in the end I think there must be a more simple way.

What am I doing wrong?

Here is my code so far:
```

# because ubuntu 10.04 is using upstart for squid
# but debian does not I need to find out which system is used
if which initctl && initctl --version | grep -i upstart
    then
    say "upstart installed, try use upstart..."
    say "stopping squid..."
    initctl stop squid || echo "squid seems to be down" 2>&1 >> $LOGFILE 
    sleep 5
    while ps aux | grep squid | grep -v grep
    do
        say "squid is still up, waiting 3 seconds..."
        sleep 3
    done
    say 'squid is down!'
    sleep 1
    say "starting squid..."
    initctl start squid 2>&1 >> $LOGFILE
else
    say "no upstart installed, try use init script..."
    invoke-rc.d squid restart 2>&1 >> $LOGFILE
fi
```

Also my loop to ensure that the script does not continue before squid is down.... it seems so silly but I found no other way doing that.

Can anybody help?

---

### Post by arrrghhh on 2010-07-13
I thought the syntax was ```
service start/stop squid
``` or ```
service start/stop/restart service
``` - just replace whatever service you're looking to start/stop/restart!

---

### Post by freiquell on 2010-07-15
hmmm...
> service  runs  a  System V init script in as predictable environment as
possible, removing most environment variables and with current  working
directory set to /.
This works for squid on Ubuntu 10.04 but not on Debian Lenny.
Which confuses me again.
When you read the manpage of 'service' they talk about the old Init-System, not Upstart.
So it should not work on 10.04 - but does. On the other hand I don't even find this command on Debian, even not with 'aptitude search'....

what the heck?

---

### Post by arrrghhh on 2010-07-15
There are some scripts still using the "old" Init system.  Perhaps this is where the confusion arises?  Not sure what else to tell ya.  If it's not broken, don't fix it...

---

### Post by freiquell on 2010-07-16
ok, well...
this is so far my attemp to restart squid on debian or ubuntu with trying to allow no error:

```
# SQUID
say "### restart squid"
# because ubuntu 10.04 is using upstart for squid
# but debian does not I need to find out which system is used
if which initctl && initctl --version | grep -i upstart
    then
    say "upstart installed, try use upstart..."
    say "stopping squid..."
    # use Upstart-Stop only if squid is up!
    if ps aux | grep squid | grep -v grep
        then
        initctl stop squid 2>&1 >> $LOGFILE 
        # then wait and check if squid is finally down
        sleep 5
        while ps aux | grep squid | grep -v grep
        do
            say "squid is still up, waiting 3 seconds..."
            sleep 3
        done
    fi
    say 'squid is down!'
    # I hate and/or don't understand Upstart...
    sleep 1
    say "starting squid..."
    # ...at least starting is easy
    initctl start squid 2>&1 >> $LOGFILE
else
    say "no upstart installed, try use init script..."
    # should try invoke-rc.d, like told here:
    # http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.3.3.2
    if which invoke-rc.d >/dev/null 2>&1; then
        invoke-rc.d squid restart 2>&1 >> $LOGFILE
    else
        /etc/init.d/squid restart 2>&1 >> $LOGFILE
    fi
fi
```It's really a monster for a simle task as restart, but it works.
Maybe it would get a little more simple if I replace 'initctl' with 'service'... but since the manpage is confusing me I just leave it like that.

If anybody knows the one and only official correct way how to control demons during a dpkg installation (preinst/postinst) I would really like to hear the solution.

Thx for the help so far anyways!

---

