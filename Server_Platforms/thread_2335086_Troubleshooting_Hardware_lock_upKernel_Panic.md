---
title: "Troubleshooting Hardware lock up/Kernel Panic"
date: 2016-08-25
forum: Server Platforms
---

### Post by darius-maximus on 2016-08-25
Hi Everyone!

I'm having a few problems with a new PC I've put together to run as a game server. I suspect I'm having some kind of driver issue, but I'm not sure where to start troubleshooting.

It's a bare-metal Ubuntu Server 16.04 with an ssh server, steamcmd, and ARK: Survival evolved server installed.

The symptoms I've been having are both a complete lockup each day within a space of a few hours (early afternoon) each day. 
Sometimes the Caps lock key will flash (which I understand indicates a Kernel panic) and sometimes the system is just unresponsive while still powered on (which I understand indicates some kind of hardware or driver failure).

I've tried following the instructions indicated in this post here: [http://askubuntu.com/questions/104771/where-are-kernel-panic-logs](http://askubuntu.com/questions/104771/where-are-kernel-panic-logs)
I removed the '-' in the [COLOR=#111111][FONT=Consolas]/etc/rsyslog.d/50-default.conf[/FONT][/COLOR] file since I was seeing a few lines of "@^@^@^@^@" where the kernel panic occurred, but unfortunatly I haven't had a kernel panic in the two days since making that change - only hardware lockups that don't give me any indication in the /var/log/syslog file.

I like to think I'm able to understand everything going on, but I'm not sure what to look at next unless something useful shows up in the log from a kernel panic. Would anyone be able to help point me in the right direction - even something as simple as relevant literature on this kind of thing would be great :)

---

