---
title: "Making Virtual Console do Other Things"
date: 2015-04-17
forum: Server Platforms
---

### Post by Sudrien on 2015-04-17
*I figured out my problem. Google wasn't helping. Therefore, I post.*

The server I'm setting up does not have a keyboard attached normally - mostly because the 'server' is a viliv s5 with a single usb port, that I want to be useful after years of disuse. Though, this could also be an old laptop for this scenario.

So its running Ubuntu server - no graphical environment, and the most minimal of interactions outside SSH. But it still has a working screen, a screen that's always stuck on tty1. The login itself is doing me no good - My first thought was *top*.

Since server is currently using upstart, the configuration for tty1 isn't in */etc/inittab* - in my case, it's in */etc/init/tty1.conf* - so I replace the call to *getty* with a call directly to */usr/bin/top*.

Nope. Blinking cursor.

It turns out you need a variation of getty from here. Thankfully there's one in apt.

```
sudo apt-get install rungetty
```

Now that's installed, I can update */etc/init/tty1.conf* to somthing that works:

```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)

stop on runlevel [!2345]

respawn
exec /sbin/rungetty tty1 -- /usr/bin/top -s
```

The *-s* on *top* is for "secure mode" - if someone breaks in with a keyboard, no processes can be altered.

Now if I had a keyboard on that server, I still could set up tty1 to use top. But theoretically, I could put it on tty9 too. /*etc/default/console-setup* has an *ACTIVE_CONSOLES* variable that could be helpful there.

There might be other single-screen status options that are more useful than *top*. If so, I'd love to hear about them.

---

