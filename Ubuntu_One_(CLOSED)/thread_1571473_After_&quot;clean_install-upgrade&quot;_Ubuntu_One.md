---
title: "After &quot;clean install-upgrade&quot; Ubuntu One won't sync"
date: 2010-09-09
forum: Ubuntu One (CLOSED)
---

### Post by JoeGoalie on 2010-09-09
I was having some issues with my laptop and decided to do a "clean install upgrade" on it. I formated everything but the /home partition and everything is working great... Except, Ubuntu One will no longer sync.  I tried removing the laptop and re-adding it, I tried deleting the "token", I've tried reinstalling it, I'm not sure what to do from here.  Other people must have done this same thing and figured it out before.  Thanks

---

### Post by duanedesign on 2010-09-09
Joe,
what version of Ubuntu are you running? Additionally can you look in the following file and see if their is anything in it?

/home/<USERNAME>/.cache/ubuntuone/log/syncdaemon-exceptions.log

Replace <USERNAME> with your username. You might also have to hit CTRL + h (View > Show Hidden Files) to see the .cache folder

Lastly run the following command:

```
u1sdtool -c
```

wait about 30 seconds and run:

```
u1sdtool -s
```

and post those results as well.
Hopefully that will give us a clue as to what is going on.
thank you,
duanedesign

---

### Post by JoeGoalie on 2010-09-10
> **duanedesign said:**
> Joe,
what version of Ubuntu are you running? Additionally can you look in the following file and see if their is anything in it?

/home/<USERNAME>/.cache/ubuntuone/log/syncdaemon-exceptions.log
I'm running Ubuntu 10.04 x32 (also happened in Ubuntu 10.04 x64 on my PC but, I had to do a clean format on that though and now it's working fine).
syncdaemon-exceptions.log:
```
2010-09-09 23:16:31,573 - ubuntuone.SyncDaemon.sync - ERROR - T:LOCAL:T 996313e2-3f8e-4636-9a1c-766112b681f8 ['root'::'b2281abe-d16f-4db1-bc7c-9479b8074a19'] ''/home/joseph/Ubuntu One'' | cant find current state: {'is_directory': 'T', 'changed': 'LOCAL', 'has_metadata': 'T'}
2010-09-09 23:16:31,573 - ubuntuone.SyncDaemon.sync - ERROR - unhandled exception
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/sync.py", line 310, in on_event
    **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/fsm/fsm.py", line 116, in on_event
    raise KeyError("Incorrect In State")
KeyError: 'Incorrect In State'
```

> Lastly run the following command:

```
u1sdtool -c
```

wait about 30 seconds and run:

```
u1sdtool -s
```

and post those results as well.
Hopefully that will give us a clue as to what is going on.
thank you,
duanedesign

```
joseph@joseph-laptop:~$ u1sdtool -c
joseph@joseph-laptop:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

```

---

