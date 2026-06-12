---
title: "Can't login to console after crash"
date: 2010-05-25
forum: Server Platforms
---

### Post by lordxale on 2010-05-25
One of our VMs crashed after it ran out of memory (I only had 256mb allocated to it, silly me).  Since then, I can't log in either from the console or over ssh.  

This is an Ubuntu 9.10 AMD64 server installation; no GUI installed.

All other services (apache/mysql/munin-node) on this box seem to be working fine.  In fact, ssh is running and I can connect to it, but after I see the MOTD, it just hangs - like so:

```
login as: root
root@server's password:
Linux server 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Tue May 25 13:54:10 CDT 2010

  System load: 2.0               Memory usage: 32%   Processes:       112
  Usage of /:  7.0% of 28.85GB   Swap usage:   0%    Users logged in: 1

  Graph this data and manage this system at https://landscape.canonical.com/

You have new mail.
Last login: Tue May 25 13:38:01 2010

```

...It'll hang right there forever.  It doesn't matter if I use root or a normal user. I seem to recall having a problem like this when the host couldn't properly resolve its own hostname, but that doesn't appear to be the case here.  /etc/passwd looks fine, I can run /bin/login successfully in recovery mode, and I can also start /bin/bash in recovery mode.  Permissions on home directories are good...anything else I can check?  Thanks in advance!

---

### Post by clrg on 2010-05-25
Well, it seems that for some reason, your shell is not started / is stuck. I guess all you can do is

-> Double-check for a valid shell
-> Check whether the memory is full (does not appear to be the case)
-> Check whether you reached the maximum number of processes
-> Check whether some kind of login script (like .profile, .bashrc, /etc/profile) is stuck, for example in a loop
-> Check /etc/hosts
-> Say nice things to your machine

---

### Post by lordxale on 2010-05-25
> **clrg said:**
> Well, it seems that for some reason, your shell is not started / is stuck. I guess all you can do is

-> Double-check for a valid shell
-> Check whether the memory is full (does not appear to be the case)
-> Check whether you reached the maximum number of processes
-> Check whether some kind of login script (like .profile, .bashrc, /etc/profile) is stuck, for example in a loop
-> Check /etc/hosts
-> Say nice things to your machine

Well, I tried whispering sweet nothings in to the intake fans, but I'm not sure ESX properly relayed it for me. :)

If I start up in recovery mode, I can run /bin/login, log in as whatever user I want, get past the MOTD and go on about my business.  This seems like it would be a good hint for what the problem could be in normal startup, but so far it has eluded me.

---

### Post by lordxale on 2010-05-28
Well, I fixed it.  My original thread title isn't necessarily accurate; I found out that I could log in, but the shell would only appear after 15+ minutes, after which I had normally long given up. Once I got in, I quickly noticed that winbindd had gone berzerk; it was using anywhere from 20-100% of the CPU constantly. 

I'm not sure why it didn't start earlier (CPU has been off the charts the whole time according to munin), but late last night it started filling up the disk with logs.  Its a 30GB disk image and it filled up the whole thing starting from about 8-10% normal usage.  I stopped winbindd, deleted the logs, and it's responding snappily again.  I'd have gone on to troubleshoot winbindd, but this box doesn't really need it and unfortunately I've spent enough time on it already.  I had just applied the same ol' package config I applied to our other servers since this box was a strange one-off setup; it's not actually joined to our domain.

I hope this helps someone else with crazy winbindd issues!

---

