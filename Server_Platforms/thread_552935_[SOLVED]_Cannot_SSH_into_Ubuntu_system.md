---
title: "[SOLVED] Cannot SSH into Ubuntu system"
date: 2007-09-17
forum: Server Platforms
---

### Post by dwhitney67 on 2007-09-17
I have a peculiar problem that I believe surfaced in the last day or so.  When I am logged on my Ubuntu system, I can SSH into my Fedora Core 5 system on the same internal network.

Once I am on my FC5 system, I can ping my printer, my router,the "outside world", but not my Ubuntu system.  Furthermore (as if it were not already apparent), I cannot SSH back to my Ubuntu system.

When I ping the Ubuntu system from FC5, I receive notifications that the destination host is unreachable.  When attempt to SSH, I get "ssh: connect to host ubuntu port 22: No route to host".

My Ubuntu system is indeed running the SSH-daemon (server).

Btw, the only thing I did in the last few days with my Ubuntu system that may be relevant is to remove proftpd using this directive:

[FONT="Courier New"]$ sudo apt-get remove gproftpd proftpd[/FONT]

Could that action have removed any critical file(s) on my system?  I almost get the impression that my Ubuntu system is firewalled and preventing connections.  If it is, that is not my intent.  My Linksys router serves as my firewall.

Anyhow, could somebody give me a hint where I need to look to resolve this issue?  Should I uninstall SSHD and then reinstall it?

---

### Post by dwhitney67 on 2007-09-17
I rebooted my Ubuntu system and apparently that solved the problem I was having.  I wonder if this had anything to do with the action I took to remove proftpd?  I suspect I will never know.

---

