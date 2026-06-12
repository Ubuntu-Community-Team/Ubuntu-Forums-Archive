---
title: "Must disable apparmor otherwise dhcp server does not work"
date: 2016-02-03
forum: Ubuntu Development Version
---

### Post by Doug S on 2016-02-03
I am building a 16.04 server, including a dhcp server. I could not get the dhcp server stuff to work, always getting some "can not open the leases file for append" type of error. With apparmor either disabled completely (via linux command line in grub), or set to complain mode for /usr/sbin/dhcpd, the dhcp server appears to work fine.

Anybody else observed this behavior?
If yes (or no, I suppose), please reply both herein and on [the bug report]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1540672").

---

### Post by Doug S on 2016-02-16
Bump.

Is there anybody that has tried a dhcp server with 16.04 yet?

(The workaround is doing fine though. I am just wanting to get the bug report confirmed, so it can get fixed.)

EDIT: I have also asked on the [server e-mail list]("https://lists.ubuntu.com/archives/ubuntu-server/2016-February/007182.html").

---

### Post by mc4man on 2016-02-17
No clue, never used a server but 'complain' mode seems to be 'learning' mode.  Have you looked into that? 
(I gather to use the logs & a tool to create a new profile

---

### Post by Doug S on 2016-02-17
> **mc4man said:**
> No clue, never used a server but 'complain' mode seems to be 'learning' mode.  Have you looked into that? 
(I gather to use the logs & a tool to create a new profileYes, I am using complain mode so as to both not enforce the policy (which I what I need so that is works) and to have some additional information in the log files (which I posted in the bug report).

---

### Post by mc4man on 2016-02-17
I was thinking a little more pro-active like - 
man aa-logprof
or more verbosely - [https://doc.opensuse.org/documentation/html/openSUSE_121/opensuse-security/cha.apparmor.commandline.html#sec.apparmor.commandline.profiling.summary.logprof](https://doc.opensuse.org/documentation/html/openSUSE_121/opensuse-security/cha.apparmor.commandline.html#sec.apparmor.commandline.profiling.summary.logprof)

---

### Post by Doug S on 2016-02-17
> **Doug S said:**
> Yes, I am using complain mode so as to both not enforce the policy (which I what I need so that is works) and to have some additional information in the log files (which I posted in the bug report).Yes, Thanks (I think). That does work and does give a new profile that allows apparmour to be changed back to enforce mode for /usr/sbin/dhcpd. But my point is why doesn't the default profile work? O.K. we know the why, but why doesn't the default profile include the extra two required lines,  and if someone else can confirm (or deny) the issue, maybe I can get the bug report confirmed.

The program aa-logprof doesn't make any backup file before it messes with the profile, but I think it added these lines:```
  capability chown,
  [COLOR="#FF0000"]capability dac_override[/COLOR],
  [COLOR="#FF0000"]capability fowner,[/COLOR]
  capability net_bind_service,
  capability net_raw,
  capability setgid,
  capability setuid,
```

---

### Post by mc4man on 2016-02-17
Glancing thru some ubuntu wikis it would then seem to file a bug requesting the profile to be added (or amended   to?) or something like that. Your case seems to be the later
(- gets beyond my understanding as whether there is a difference between a current profile that's lacking or an app specific profile that doesn't exist + terms like 'confined' , ect.

 One - [https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor) - seems to say file bug against package *providing the profile*

I would confirm but don't have a server install, on Desktop only sbin.dhclient profile is installed & I assume you're referring to a different profile
(I would trust you so if you wish...

---

### Post by Doug S on 2016-02-17
> **mc4man said:**
> Glancing thru some ubuntu wikis it would then seem to file a bug requesting the profile to be added (or amended   to?) or something like that. Your case seems to be the later
(- gets beyond my understanding as whether there is a difference between a current profile that's lacking or an app specific profile that doesn't exist + terms like 'confined' , ect.

 One - [https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor) - seems to say file bug against package *providing the profile*

I would confirm but don't have a server install, on Desktop only sbin.dhclient profile is installed & I assume you're referring to a different profile
(I would trust you so if you wish...Thanks for your help with this. I added the isc-dhcp package to the bug report.
And yes, the profile involved is for a dhcp server, or /etc/apparmor.d/usr.sbin.dhcpd

Edit: see also: [https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1543794](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1543794)

---

### Post by Doug S on 2016-02-18
There was an update to the dhcp server package that fixes the issue, such that the original apparmour profile now works. I must have missed the update the night before last by not much time at all.

---

### Post by Doug S on 2016-02-26
> **Doug S said:**
> There was an update to the dhcp server package that fixes the issue, such that the original apparmor profile now works. I must have missed the update the night before last by not much time at all.This issue has returned, setting back to unsolved.

EDIT: Actually, now there seems to be a few problems:```
Feb 26 14:15:36 DOUG-64 kernel: [   18.262506] audit: type=1400 audit(1456524936.588:10): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/etc/ssl/openssl.cnf" pid=467 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Feb 26 14:15:39 DOUG-64 kernel: [   21.298787] audit: type=1400 audit(1456524939.624:11): apparmor="ALLOWED" operation="capable" profile="/usr/sbin/dhcpd" pid=1232 comm="dhcpd" capability=1  capname="dac_override"
Feb 26 14:15:39 DOUG-64 kernel: [   21.323369] audit: type=1400 audit(1456524939.648:12): apparmor="DENIED" operation="open" profile="/usr/sbin/named" name="/proc/sys/net/ipv4/ip_local_port_range" pid=1336 comm="named" requested_mask="r" denied_mask="r" fsuid=109 ouid=0
Feb 26 14:15:39 DOUG-64 kernel: [   21.323602] audit: type=1400 audit(1456524939.648:13): apparmor="DENIED" operation="open" profile="/usr/sbin/named" name="/proc/sys/net/ipv4/ip_local_port_range" pid=1336 comm="named" requested_mask="r" denied_mask="r" fsuid=109 ouid=0
Feb 26 14:15:39 DOUG-64 kernel: [   21.349947] audit: type=1400 audit(1456524939.676:14): apparmor="ALLOWED" operation="capable" profile="/usr/sbin/dhcpd" pid=1232 comm="dhcpd" capability=3  capname="fowner"
doug@DOUG-64:~$

```

---

### Post by Doug S on 2016-03-08
Fixed again. Back to SOLVED.

---

