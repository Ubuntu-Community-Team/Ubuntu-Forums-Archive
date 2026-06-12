---
title: "Portslave startup"
date: 2008-10-02
forum: Server Platforms
---

### Post by new2hoary on 2008-10-02
Hi,

I've used portslave package in the past and utilized inittab to start it with an entry such as;

S0:23:respawn:/usr/sbin/portslave 0

Now I've come to set up another installations and can't get portslave to start. With no inittab I copied /etc/event.d/tty1 and created a ttyS0 with the following;

# ttyS0 - portslave
#

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /usr/sbin/portslave 0

This tries to start portslave but it seg faults and respawns too fast.

Any ideas how to start portslave using upstart?

Thanks for any help.

---

