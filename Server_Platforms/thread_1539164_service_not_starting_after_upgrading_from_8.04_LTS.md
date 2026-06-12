---
title: "service not starting after upgrading from 8.04 LTS to 10.04 LTS"
date: 2010-07-26
forum: Server Platforms
---

### Post by Tupsi on 2010-07-26
Hallo

I just upgraded my server from 8 LTS to 10 LTS via the do-release-upgrade method which on the first look worked like a charm.
Rebooting into the new system although showed no running services besides mysqld and sshd (got lucky here, its a remote system). Everything else like apache, postfix etc. is not. After trying out some stuff I managed to get the stuff started when I user

telinit 2

or

telinit 3

afterwards everything gets properly started. But I dont find any reference on the net to it, how I can achieve this during boot time, as it seems apparent that something changed to the boot process, so that my stuff isnt started properly any longer as it was used to be.

I guess it has something todo with how ubuntu starts these days (upstart?) compared to old times, but I have no clue how to fix it.

Any help apprechiated.

---

### Post by Tupsi on 2010-07-26
edit:

the only thing running is:
```

root       310  0.0  0.2   3904  2424 ?        S    14:39   0:00 /sbin/plymouthd --mode=boot --attach-to-session
root       334  0.0  0.0   2312   848 ?        S    14:39   0:00 upstart-udev-bridge --daemon
root       339  0.0  0.0   2520   840 ?        S<s  14:39   0:00 udevd --daemon
root       569  0.0  0.0      0     0 ?        S    14:39   0:00 [kpsmoused]
root       636  0.0  0.0      0     0 ?        S    14:39   0:00 [radeon/0]
root       637  0.0  0.0      0     0 ?        S    14:39   0:00 [ttm_swap]
root       642  0.0  0.0   2516   736 ?        S<   14:39   0:00 udevd --daemon
root       645  0.0  0.0   2516   716 ?        S<   14:39   0:00 udevd --daemon
root       688  0.0  0.0   1828   504 ?        Ss   14:39   0:00 /bin/sh -e /proc/self/fd/10
mysql      702  0.1  2.4 147172 25112 ?        Ssl  14:39   0:00 /usr/sbin/mysqld
root       710  0.0  0.0   1828   588 ?        S    14:39   0:00 /bin/sh /etc/init.d/rc S
root       713  0.0  0.0   5548   928 ?        Ss   14:39   0:00 /usr/sbin/sshd
root       726  0.0  0.0   1828   572 ?        S    14:39   0:00 /bin/sh /etc/rcS.d/S05keymap.sh start
root       734  0.0  0.0   1828   524 ?        S    14:39   0:00 /bin/sh /usr/bin/unicode_start
root       738  0.0  0.0   1864   568 ?        S    14:39   0:00 /usr/bin/vt-is-UTF8 --quiet

```

As I said it all goes away with manually entering "telinit 2", but thats not really how a server should work ;)

also, the command runlevel returns "unknown" right after boot. After I entered the telinit it says N 2.

---

### Post by cdenley on 2010-07-26
The services which don't start, what network interfaces do they bind to? If they require all network interfaces to be up, then that is probably your problem. With upstart, most services are configured to start when any network interface is brought up, which is usually 127.0.0.1. If the service is configured to listen on all interfaces, then this shouldn't be an issue.

---

### Post by Tupsi on 2010-07-27
Thanks for your reply.

No the network has to be fine, as me only way of going in is via ssh.

What strikes me as odd is the line

```

root       710  0.0  0.0   1828   588 ?        S    14:39   0:00 /bin/sh /etc/init.d/rc S

```

isnt that the starting script for the startup/boot process and shouldnt that be finished after a while by itself and move over to execute itself as /etc/init.d/rc 2 ? At least thats what i can see when I enter "telinit 2" and do a quick ps axu afterwards.

somehow the system stops/hangs there and I have no clue why. It must have something todo with the new startupsystem, its least thats my guess as the system was fine back in draper drake and after I upgraded it to 8. (upstart wasnt already in 8, was it?).


but to answer your question, I would say that everything is missing binds to "all" or at least the external ip4 address (proftpd, apache, openfire, postfix, courier). But the external interface has to be up, or else I wouldnt be able to ssh into the server, so what else could it be?

Is there a way I can log what /etc/init.d/rc S is doing? Maybe I can figure out why it stops and where at a certain point? dmesg, syslog and messages are not very detailed/interesting at atm to say anything about it.

---

### Post by cdenley on 2010-07-27
> **Tupsi said:**
> but to answer your question, I would say that everything is missing binds to "all" or at least the external ip4 address (proftpd, apache, openfire, postfix, courier). But the external interface has to be up, or else I wouldnt be able to ssh into the server, so what else could it be?

Yes, the external interface is up after your server is done booting, but it probably is not up when your network daemons are started. Most server upstart configurations will start BEFORE the external interface is brought up. If the server attempts to bind to the external interface at this time, it will fail. If it attempts to listen for connections on all interfaces, it will succeed.

---

### Post by Tupsi on 2010-07-29
ah ok, got ya. Can you also tell me how to fix it?

It sounds like I have to tell upstart to wait for the external ip to be up, but I have no clue how to do that.

---

### Post by cdenley on 2010-07-29
> **Tupsi said:**
> ah ok, got ya. Can you also tell me how to fix it?

It sounds like I have to tell upstart to wait for the external ip to be up, but I have no clue how to do that.

Post an upstart configuration file in /etc/init for a service which binds to external interfaces, and tell me which external interfaces it binds to.

---

### Post by Tupsi on 2010-07-29
i got it!

thanks to your pointers (/etc/init) I found rc-sysinit.conf in there which had lines making me suspicous, as it was just what I wanted, but didnt get:

```

    # Run the system initialisation scripts
    [ -n "${FROM_SINGLE_USER_MODE}" ] || /etc/init.d/rcS

    # Switch into the default runlevel
    telinit "${DEFAULT_RUNLEVEL}"

```

this seems to be the script which got stuck during boot, resulting in the last line never happening.

so I took a leap of faith and removed all old S* links from /etc/rc.S and voila, the computer now boots as it should.

```

S05initrd-tools.sh -> ../init.d/initrd-tools.sh
S05keymap.sh -> ../init.d/keymap.sh
S13pcmciautils -> ../init.d/pcmciautils
S27evms -> ../init.d/evms
S46libpam-foreground -> ../init.d/libpam-foreground
S47lm-sensors -> ../init.d/lm-sensors
S70screen-cleanup -> ../init.d/screen-cleanup
S70x11-common -> ../init.d/x11-common
S85urandom -> ../init.d/urandom
S90console-screen.sh -> ../init.d/console-screen.sh

```

I figure one of the above scripts made the whole rcS getting stuck and should not have been there in the first place after the upgrade.

Not sure what I am breaking by leaving these out, but for now it works, so thanks again!!!

:p

---

