---
title: "file descriptor 'n' left open, possible LVM / Chroot bug ?"
date: 2008-07-31
forum: Server Platforms
---

### Post by djamu on 2008-07-31
Since a couple of days I'm seeing 
```
File descriptor 3 left open
File descriptor 4 left open
File descriptor 6 left open
File descriptor 7 left open

```
Whenever I create / delete a snapshot.

Found some old RHEL topic related posts + 1 recent debian one ( Tue, 17 Jun 2008 ) . > [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486696](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486696)

Can someone shed some light on this Issue / severity ?
Before submitting it to launchpad.



thx

---

### Post by djamu on 2008-08-01
K bug fixed, consider as solved. Just another bad LTS ubuntu porting bug unrelated to the debian issue. Severity > none

**RANT:**
Another as in the bad ported / broken fail2ban_0.8.2-2_all.deb package, that just stays in the repos.... geee 
For the people who find this post via a search > current fail2ban_0.8.2-2_all.deb installs just fine but refuses to start on reboot because of missing folder / pid, this doesn't show up so users have the impression that their system is protected...
The debian one is perfectly good, so is the intrepid fail2ban_0.8.2-3_all.deb one.

:mad:

---

