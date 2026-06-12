---
title: "Lost permissions Server"
date: 2009-11-14
forum: Server Platforms
---

### Post by NJC on 2009-11-14
I continue to lose Ubuntu 9.10 server permissions and have to use ssh password instead of passphrase. I am logging in from Ubuntu 9.10 terminal on a LAN. These are permissions before chmod (ls -la indicated this was only change after chmod):

**drwxrwxrwx 14 user  4096 2009-10-03 20:21 .**

Run the following as sudo:
```

chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```And after chmod:

[B]drwxr-xr-x 14 user   4096 2009-10-03 20:21 .
[/B] 
Why do I continually lose Server permissions? Attempting to run an unscheduled cron rsync and need to have passphrase working.

---

### Post by NJC on 2009-11-24
No one? Maybe I've posted in the wrong part of town. :mrgreen:

---

### Post by karlson on 2009-11-24
> **NJC said:**
> I continue to lose Ubuntu 9.10 server permissions and have to use ssh password instead of passphrase. I am logging in from Ubuntu 9.10 terminal on a LAN. These are permissions before chmod (ls -la indicated this was only change after chmod):

**drwxrwxrwx 14 user  4096 2009-10-03 20:21 .**

Run the following as sudo:
```

chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```And after chmod:

[B]drwxr-xr-x 14 user   4096 2009-10-03 20:21 .
[/B] 
Why do I continually lose Server permissions? Attempting to run an unscheduled cron rsync and need to have passphrase working.

You will need to be a little clearer on what it is that you're doing.

ssh client sets up permissions on .ssh directory for the user to whatever it is that it wants.  Permissions of 600 on authorized_keys are not necessary.

The question is what happens between the time you change permissions and the time the permissions revert.

---

### Post by NJC on 2009-11-24
I haven't been about to find out the cause ... it might be even after the server is turned off from my workstation (sudo poweroff). I'll investigate further.

---

