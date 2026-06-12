---
title: "How to automatically sleep/suspend/hibernate/power down server,"
date: 2008-08-05
forum: Server Platforms
---

### Post by _SiM on 2008-08-05
Hi guys,

I have my samba file server with 8.04 all up and running now :)

I am just wondering if there is a way to turn it off or go to a low power state after a certain amount of idle time.

Which package do I need to install? ACPI? and how do I set it up?

If anyone can point me in the correct direction, that would be great :)

Cheers

---

### Post by ajgreeny on 2008-08-05
You could simply halt it with ```
sudo shutdown -h <time_in_24_hr_clock>
``` though this will only poweroff.  I don't know if it's possible to hibernate or suspend.

Here is the info from **man:shutdown** in gnome-help:-

shutdown
arranges for the system to be brought down in a safe way.  All logged-in
users are notified that the system is going down and, within the last
five minutes of
TIME,
new logins are prevented.

TIME
may have different formats, the most common is simply the word
'now'
which will bring the system down immediately.  Other valid formats are
+m, where m is the number of minutes to wait until shutting down and hh:mm which specifies the time on the 24hr clock.

Once TIME has elapsed, shutdown sends a request to the init (8) daemon to ring the system down into the appropriate runlevel.

OPTIONS
-r
    Requests that the system be rebooted after it has been brought down.
-h
    Requests that the system be either halted or powered off after it has been
    brought down, with the choice as to which left up to the system.
-H
    Requests that the system be halted after it has been brought down.
-P
    Requests that the system be powered off after it has been brought down.
-c
    Cancels a running shutdown.
    TIME
    is not specified with this option, the first argument is
    MESSAGE.
-k
    Only send out the warning messages and disable logins, do not actually
    bring the system down.

---

### Post by _SiM on 2008-08-05
Thanks for the suggestion ajgreeny but I need a solution that will not require me to log on. Something that will automatically do it without a user logged on...

At the moment, I use wake-on-lan to automatically switch the PC on when the HTPC (XP) goes on (sends command using a batch file Start>Startup folder)

If there is a remote shutdown command that I can be automatically run when the HTPC goes off (without having to log in using putty) then that would be perfect, (I should be able to schedule the task on shutdown). Otherwise, just a bog standard, hibernate/sleep/shutdown when idle is what I need!

I did see this: [http://ubuntuforums.org/showthread.php?t=530973](http://ubuntuforums.org/showthread.php?t=530973)
but for that to work you need to have an active account, I access the samba shares without logging into any account so that solution is no good.

---

### Post by _SiM on 2008-08-06
Can anyone help?

---

### Post by sprouty on 2008-08-09
If i was you i would look into using cron and a script for example as root create a script with the following itint
```

#!/bin/bash
poweroff

```

save it has /root/poweroff.shl
```
chmod 777 /root/poweroff.shl
```
and then useing crontab -e 

```
01 1 * * * /root/poweroff.shl >>/root/Poweroff.log 2>&1
```
This wil runn at a minute past 1AM i think it should work.

You would need to do this all has root!

---

### Post by windependence on 2008-08-09
I know this doesn't answer your question, but in my experience powering down and starting up is hard on hardware. You are not saving much electricity either as today's hardware is pretty efficient. Personally I think this will end up costing you in the long run. When you power off and on, the components radically change temperature and expand and contract on the board. This causes them to eventually loosen over time and can cause motherboard failure. Also, spinning up disks is a quite destructive operation. It's much easier in them to be running all the time. What you save in electricity, you will lose in hardware. In all the large corporate environments I have worked in, we have always had better luck leaving everything on rather than powering down.

-Tim

---

### Post by _SiM on 2008-08-18
Thanks guys... Well I might only need it on a 3 or 4 times a week, so I will need it off...

Thanks sprouty I might have to implement something like that until I get it working properly...

---

