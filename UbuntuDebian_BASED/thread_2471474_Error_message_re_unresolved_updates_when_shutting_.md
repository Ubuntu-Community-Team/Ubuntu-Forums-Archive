---
title: "Error message re unresolved updates when shutting down"
date: 2022-01-31
forum: Ubuntu/Debian BASED
---

### Post by webheadjunky2 on 2022-01-31
Hi
Have been running latest Ubuntu DDE for couple of weeks now and love it! Super slick!!
I have one issue though, for over a week now
Had hoped it might resolve itself
Whenever I shut down, I get a warning that some updates have not concluded, yet I run my updates via terminal and no indicators through that process
Grateful for your advice re attached screenshot
Cheers
R

---

### Post by ajgreeny on 2022-01-31
Your image is not very clear but it looks as if unattended-upgrades is running and telling you not to shutdown until it has finished.

I have no experience of this as I remove the unattended-upgrades package from my system, preferring to manage everything manually when I startup each day. I even stop the update-notifier from running automatically, again because I check every day so do not need that to run.

How long have you waited before trying to shutdown again?  If it is unattended-upgrades that is your problem you should be able to safely stop it

If this was my machine I think I would try running ```
sudo apt update && sudo apt -full-upgrade
``` and then try shutting down.
If unattended-upgrades really is running you may see an error message telling you that the command can not run as something else is already running, eg
***Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 47384 <process name>***

You can then try killing that process with command ```
kill 47384
```

---

### Post by webheadjunky2 on 2022-02-01
Hey many thanks for coming back to me so quickly; much appreciated
Got a syntax error initially so removed the dash before f in "full"
It removed linux headers that were no longer needed
However, I still get the same issue when I reboot which is very odd

No package lock so nothing to kill

I left it unattended for a good half hour and nothing happened

What does this bit mean and how can I apply it on my machine please:
[COLOR=#000000]"I have no experience of this as I remove the unattended-upgrades package from my system, "

[/COLOR]Thanks again
R

---

### Post by ajgreeny on 2022-02-01
By default since 18.04 i think but can't remember when it started, Ubuntu now uses a system of automatically upgrading security packages with no input from the user.  To do this it automatically runs the unattended-upgrades application.  If that happens to be running, and I do not remember when or how often it runs, you will not be able to shutdown the system without getting a message similar to the one you see.

As I prefer full control of my OS I remove that package completely from my systems and run the upgrade commands at a convenient time to me.

It is possible to simply disable unattended-upgrades and leave it installed but as I will never use it I remove it.

---

### Post by webheadjunky2 on 2022-02-18
Apologies for delay. Have disabled automatic updates as like you, I run them manually as a matter of routine. Thanks again for the advice

---

