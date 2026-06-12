---
title: "Syncing ?"
date: 2011-10-18
forum: Ubuntu One (CLOSED)
---

### Post by EowynCarter on 2011-10-18
I've been giving ubuntu one a try, i like some stings there a lot.

But syncing, on windows as on linux, seams totally un-reliable.
It seams not to work more often than it works... No way to force sync, no status...

Only the android client jumps when you say jump. Windows and linux seams to sync when they fells like it.

And having to use the command line to see that the hell is happening....

Also, i tried to get a file with android with no 3g or wi-fi active. Obviously, that failed. But i can't see the file on the android client anymore.

if anyone can point me some clues on how to get this working ?

---

### Post by Kjell on 2011-10-18
I cant get it sync/connect at all, Ubuntu One clients just does not work.

- Laptop with 10.04 LTS
- Stationary PC with ubuntu 11.10
- Win XP at work
- Android 

There is nothing happening 

I can only access through my browser

---

### Post by nutznboltz on 2011-10-19
@Kjell and @EowynCarter

In your 

~/.cache/ubuntuone/log/syncdaemon.log

file do you see messages like:

2011-10-19 08:26:21,325 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: [('SSL routines', 'SSL23_READ', 'ssl handshake failure')]

You can run this command to test:

```

grep 'ssl handshake failure' ~/.cache/ubuntuone/log/syncdaemon.log*

```
Start the terminal and copy-paste that command into it and run it.  If there are output lines with 'ssl handshake failure' then you have this issue.

If so, open the "Ubuntu One Control Panel" which is:

/usr/bin/python /usr/bin/ubuntuone-control-panel-gtk

but you can click on the U1 logo in the launcher sidebar on the left with Unity to run it.

Then press the "disconnect" control, wait a bit and press "connect" this will often establish a connection where previously there wasn't really a connection even if the control panel said there was plus syncing was not working.

---

