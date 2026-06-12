---
title: "autostarting iptraf with rungetty"
date: 2007-04-22
forum: Server Platforms
---

### Post by kultex on 2007-04-22
Ubuntu 6.10 has no more inittab - it is replaced with upstart

I want to start iptraf in the background for eth0 - so I changed /etc/event.d/tty6

sudo nano /etc/event.d/tty6

# tty6 - getty
#
# This service maintains a getty on tty6 from the point the system is
# started until it is shut down again.

start on runlevel-2
start on runlevel-3
stop on runlevel-4
stop on runlevel-5

stop on shutdown

respawn /sbin/rungetty tty6 -u root -- iptraf -s eth0 -B

when I reboot I get:

init: tty6 process (3122) terminated with status 1
init: tty6 process endet, respawning
init: tty6 respawning too fast, stopped

and I cannot login on the console - I can login through ssh and iptraf is started correctly

but still it would be nice, if I could log in on the machine itself

I have no idea, if it is a bug in the new sytem  or I made a mistake, but I did not find anything googeling

best regards   kultex

---

