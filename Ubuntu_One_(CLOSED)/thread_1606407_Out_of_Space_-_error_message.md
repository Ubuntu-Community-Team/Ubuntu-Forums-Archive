---
title: "Out of Space - error message"
date: 2010-10-26
forum: Ubuntu One (CLOSED)
---

### Post by lazylew on 2010-10-26
When Ubuntu kicks in after starting up, there's this  "Out of space" message that says: "Your Ubuntu One storage is full. Follow the link below to upgrade your subscription."

Truth is, I have exactly one file of 22 kb in there!

So what gives?

As extra info, I might add that this behaviour started after some Ubuntu-hopping from Lu to Xu and finally regular Ubuntu.

---

### Post by rtg on 2010-10-27
Hello,

It looks like this is a bug [LP:650671]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/650671"). Please check that ubuntuone has at least once connected to the service, this will update the outdated metadata info and prevent these messages from appearing.

Could you please provide the output of u1sdtool --status ?

---

### Post by lazylew on 2010-10-27
> **rtg said:**
> Hello,

It looks like this is a bug [LP:650671]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/650671"). Please check that ubuntuone has at least once connected to the service, this will update the outdated metadata info and prevent these messages from appearing.

Could you please provide the output of u1sdtool --status ?
```
u1sdtool --status
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_CONTENT


``` (note I did not create the empty line at the end of the output; it was actually there in the terminal)

---

### Post by lazylew on 2010-10-29
Don't know what happened; maybe the bug got fixed?
The error doesn't appear anymore :)

---

### Post by xedi on 2010-11-20
It still appears for me unfortunately. I have connected to ubuntu one and still have about 1 gig free space, but the error message is keeping to pop up and gets really annoying.

Don't know what it is but since rtg asked lazylew for it:

```
u1sdtool --status
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

```

---

### Post by williamdemeo on 2011-01-01
In case it helps you guys to know of other users with the same problem, I have it too.  When I first log in to the Gnome desktop, a box pops up to tell me that my Ubuntu One is full, and asking me to click on a link to get more space.  I have only one folder and one 31Kb file in my Ubuntu One directory.

Here is the output of u1sdtool --status:

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

-William

---

### Post by williamdemeo on 2011-01-01
Apparently, this problem has been reported multiple times.  A more adequate response appears in this thread:

[http://ubuntuforums.org/showthread.php?t=1597626](http://ubuntuforums.org/showthread.php?t=1597626)

-William

---

