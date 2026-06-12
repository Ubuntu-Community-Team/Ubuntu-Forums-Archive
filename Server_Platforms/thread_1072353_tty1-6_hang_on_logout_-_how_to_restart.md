---
title: "tty1-6 hang on logout - how to restart?"
date: 2009-02-17
forum: Server Platforms
---

### Post by leandromartinez98 on 2009-02-17
My tty screens hang on logout. That is, logout seems to be 
successful (as the "who" command indicates), but the screen
remains blank. This seems to be a bug, but, most importantly
at the moment, I would like to be able to restart these hanged
ttys from the other ttys.

Anyone has any hint?

I'm using Ubuntu Server 8.10.

Thanks.

---

### Post by leandromartinez98 on 2009-02-17
I found a parcial solution: The command:

inittcl start ttyN (where N is 1-6, the corresponding tty)

restarts the tty. However, I still get tty hangs on logout.

It seems that this is the same bug as: 

[https://bugzilla.redhat.com/show_bug.cgi?id=450488](https://bugzilla.redhat.com/show_bug.cgi?id=450488)

And maybe the patch is already available. However, I cannot restart this machine anytime soon (it the the master node of a large cluster where many people is running their applications). Anyone more experienced is able to understand the bug above and suggest how to proceed avoiding restarts?

Thanks again.

---

### Post by AndyMcCall on 2009-02-17
What does your /etc/event.d/tty* files have in them? Are they all intact?

XXXX:/etc # cd /etc/event.d/
XXXX:/etc/event.d # ls
control-alt-delete  logd  rc0  rc1  rc2  rc3  rc4  rc5  rc6  rc-default  rcS  rcS-sulogin  sulogin  tty1  tty2  tty3  tty4  tty5  tty6
XXXX:/etc/event.d # more tty6
# tty6 - getty
#
# This service maintains a getty on tty6 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3

stop on runlevel 0
stop on runlevel 1
stop on runlevel 4
stop on runlevel 5
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty6
XXXX:/etc/event.d #

Maybe that will help.

---

### Post by leandromartinez98 on 2009-02-17
Hi Andy, this is what the "tty1" contains:

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1

Note that it was already restarted with the "initctl start tty1". It is identical to the other ttyN files for which no problem occurred (because we didn't log into all ttys).

---

### Post by tubezninja on 2009-02-17
For what it's worth, I had this happen one time recently on one of my 8.10 servers as well (x86_64), so leandromartinez98 isn't the only one.  Unfortunately, I just shrugged it off and rebooted after ssh'ing in from another box, thus wiping out the event.d contents.  If it happens again I'll look here and see if anything pops up.  It's only happened to me once though (last week), and hasn't repeated since.

leandromartinez98, are you running the 64 bit kernel as well?

---

### Post by leandromartinez98 on 2009-02-18
Yes, I'm running the 64 bit kernel. As the bug report above suggests, this is an issue related to the update of the libc packages, that recently happened. A restart solves the problem, at least until a new update of libcs happens. My problem is that I cannot restart this machine, it is the master node of a cluster which is being used full time now, so restart will be only in case of "emergency".

I learnt from this experience that I should not update the cluster unless I can reboot it afterwards. Of course, this is highly undesirable. If this was a problem that forced me to reboot I would be now very unsatisfied (me and the other users of the cluster, of course). I think a better control of updates that could take care of checking whether the update will require reboot would be highly desirable for the server.

---

