---
title: "Ubuntu One stuck in sync"
date: 2010-06-01
forum: Ubuntu One (CLOSED)
---

### Post by Killer Cop on 2010-06-01
Hi.

I've installed 10.04 yesterday and I'm quite amazed how far Ubuntu has gotten, especially on the graphics. But Ubuntu One is also really cool and useful, but mine won't work yet.

I tried to sync a small folder inside my pictures folder, and it says that it should be in sync (I can make it stop with the sync). But nothing has uploaded at all automatically, with the exemption of the folder, but not the content. I can only upload through the web UI, one file at the time.

In the preferences window it says "Synchronization in progress..." but it stays there forever and it shows 00.00 KB stored even when I have some 64 KB. It can identify my computer and account, but it's stuck on the sync.

I can't sync files in the Ubuntu One folder either.

Any help is appriciated. :-s

---

### Post by feaband on 2010-06-01
Please somebody answer. I have the exact same problem.

Thank you!

---

### Post by piedro on 2010-06-02
Exacltly the same here: 

As suggested elsewhere I used the following command: 

```
u1sdtool -s
```

and I get that output

> State: AUTHENTICATE
    connection: With User With Network
    description: doing auth dance
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH


... "is online: False" what's this?

plz, help, 
p.

---

### Post by piedro on 2010-06-04
KK! 

Now something seems to be working, very slowly, but since today I'm synced! :-) 

Happy for the moment (feels so cozy to connected ...), 
thx for reading, 
piedro

---

### Post by duanedesign on 2010-06-04
With the last release a record number of users started using the service. The U1 devs have been working hard bringing new servers online and optimizing code speed up syncing. Last I heard they were testing some new changes on staging. So that should be helping soon. Give it a few days, there is a large backlog, and post back if you do, or dont, see an improvement.

@piedro
your u1ssdtool -s
> State: AUTHENTICATE
connection: With User With Network
description: doing auth dance
is_connected: True
is_error: False
is_online: False
queues: WORKING_ON_BOTH 

is_online is FALSE because their is a certain amount of work that must be done locally before the service connects. It says 'is_conneted: True' that is good. As is 'With User With Network' if you needed to push connect it would say Not User Not Network. Check the u1sdtool -s occasionally and you will start to get used to the different states.

---

### Post by inreflection7 on 2010-07-07
I just got Ubuntu 10.04 a few days ago and still waiting for it to sync. It says "Synchronization in Progress" w/o any progress. I have a folder marked to sync with some HTML files and pictures and some other files around 10 MB total in Ubuntu One just to test the service. Not quite sure why it is stuck at 0.0%.

Thought I'd just report in...

I don't necessarily require the One service, but am very interested in using it once its more stable.

---

