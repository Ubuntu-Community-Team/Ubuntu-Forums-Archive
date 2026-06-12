---
title: "Ubuntu One won't upload/sync. queues: WORKING but current uploads: 0"
date: 2012-04-04
forum: Ubuntu One (CLOSED)
---

### Post by luglug on 2012-04-04
Hi Everybody. 

So here I am, using Ubuntu 11.10 and after giving up on U1 years ago, I thought I'd return to see the state of play, but sadly having issues. 

First off, ```
~$ uname -r
3.1.0-997-generic
```

Now my problem is that U1 doesn't seem to be doing much of anything. I have my Documents folder synced, but nothing is happening. For example, here's what I get with the u1sdtool

```
~$ u1sdtool --current-transfers
Current uploads: 0
Current downloads: 0

~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING
```

It's been like that for a few hours. I'm hoping this is maybe something silly on my part, but any help of insight is greatly appreciated!

Could it be possibly some kind of firewall issue blocking U1?

Cheers,
LL

---

### Post by duanedesign on 2012-04-06
Could you please run the following command to see how many items are in the sync queue:

```
u1sdtool --waiting | wc -l
```

If it returns 0 and your newly added UDF is not being seen try restarting the syncdaemon. 

```
U1sdtool -q

u1sdtool -c
```

It will take a couple minutes for U1 to rescan everything and add your files to the queue. If the --waiting command is stuck and does not get smaller further troubleshooting will be required.

---

