---
title: "Server Unresponsive Troubleshooting"
date: 2013-11-10
forum: Server Platforms
---

### Post by mastermindg on 2013-11-10
I have a headless server running 13.04. Occasionally the server becomes unresponsive. The only way to get it back up is a hard reset. My question is: how do I best troubleshoot the cause of the unresponsive, be it network,load, etc?

---

### Post by houstonbofh on 2013-11-10
First, define unresponsive?  No console?  No desktop?  No ssh?  No ping?  Note that it will need a head for troubleshooting.

Also, look at the logs and see what last happened before it took a nap.

---

### Post by mastermindg on 2013-11-10
Unresponsive meaning SSH and Apache down. I didn't attempt a ping but the box was physically running. Again, this is a headless server, there is no desktop.

---

### Post by tgalati4 on 2013-11-10
Headless servers require reliability (for obvious reasons), but in this case, you need to put a display on it and log into a console and look at what is going on.  Run *htop* in a root session.  Run *screen* if you need multiple console panes to watch different things like network traffic and log files.  Hard shutdowns are tough on the file system and need to be used sparingly.  Use the Magic SysRQ keys instead.

[http://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop](http://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop)

[http://askubuntu.com/questions/367680/hotkey-to-start-sync-or-flushing-memory](http://askubuntu.com/questions/367680/hotkey-to-start-sync-or-flushing-memory)

---

### Post by Lars Noodén on 2013-11-10
Can you log in at the console when it is "down"?  

When you go back and check, do the system logs indicate anything at the times the system is not working?

---

### Post by mastermindg on 2013-11-22
I'm not able to connect to it at all, even locally. My monitor isn't loading a display and just shows "No Signal".  My problem is that my logs are being overwritten on reboot. I'm not able to see ANY logs under /var/logs with entries during the time that my system goes down.

FYI: The system is powered up when it's "down". This isn't my first computer :)

---

### Post by Lars Noodén on 2013-11-22
Can you boot to a live DVD / CD and examine the logs on the HD that way?  That could keep them from being overwritten while you try.

You mentioned headless, do you have a serial console?

---

### Post by houstonbofh on 2013-11-22
So, it is hard locking...  I would start by booting memtest and running it overnight for several passes.  Making sure you have a stable platform is a good first step.  It is very frustrating to do days of work over a bad stick of ram. :)

---

### Post by mastermindg on 2013-12-05
It ended up being an issue with Power Management sleeping my system. I only found out because there was an old power log file in /var/log. I uninstalled pm-utils and haven't had a problem sense.

---

