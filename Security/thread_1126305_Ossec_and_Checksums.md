---
title: "Ossec and Checksums"
date: 2009-04-15
forum: Security
---

### Post by physeetcosmo on 2009-04-15
All,

I am running 8.10 with the latest release of Ossec-HIDs running on my tower at home. I get Ossec rules firing every once in a while about the "integrity checksum" changing for several folders or /etc packages.

I have Ossec setup to email me with notifications and/or errors. Here's the latest email I received this morning right after I turned on my tower:
```
OSSEC HIDS Notification.
2009 Apr 15 06:34:02

Received From: computer->syscheck
Rule: 551 fired (level 7) -> "Integrity checksum changed again (2nd time)."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/group'[/COLOR]
Size changed from '942' to '1016'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:02

Received From: computer->syscheck
Rule: 551 fired (level 7) -> "Integrity checksum changed again (2nd time)."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/group-'[/COLOR]
Size changed from '921' to '1012'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:04

Received From: computer->syscheck
Rule: 551 fired (level 7) -> "Integrity checksum changed again (2nd time)."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/gshadow'[/COLOR]
Size changed from '784' to '854'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:04

Received From: computer->syscheck
Rule: 551 fired (level 7) -> "Integrity checksum changed again (2nd time)."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/gshadow-'[/COLOR]
Size changed from '766' to '850'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:06

Received From: computer->syscheck
Rule: 550 fired (level 7) -> "Integrity checksum changed."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/login.defs'[/COLOR]
Size changed from '9681' to '9676'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:08

Received From: computer->syscheck
Rule: 550 fired (level 7) -> "Integrity checksum changed."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/motd'[/COLOR]

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:10

Received From: computer->syscheck
Rule: 550 fired (level 7) -> "Integrity checksum changed."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/passwd'[/COLOR]
Size changed from '1759' to '1806'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:10

Received From: computer->syscheck
Rule: 550 fired (level 7) -> "Integrity checksum changed."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/passwd-'[/COLOR]
Size changed from '1717' to '1806'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:12

Received From: computer->syscheck
Rule: 550 fired (level 7) -> "Integrity checksum changed."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/shadow'[/COLOR]
Size changed from '1050' to '1106'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:12

Received From: computer->syscheck
Rule: 550 fired (level 7) -> "Integrity checksum changed."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/shadow-'[/COLOR]
Size changed from '1022' to '1106'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:12

Received From: computer->syscheck
Rule: 550 fired (level 7) -> "Integrity checksum changed."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/shells'[/COLOR]
Size changed from '181' to '192'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:14

Received From: computer->syscheck
Rule: 551 fired (level 7) -> "Integrity checksum changed again (2nd time)."
Portion of the log(s):

[COLOR="Red"]Integrity checksum changed for: '/etc/blkid.tab'[/COLOR]
Size changed from '732' to '879'

 --END OF NOTIFICATION

OSSEC HIDS Notification.
2009 Apr 15 06:34:14

Received From: computer->syscheck
Rule: 551 fired (level 7) -> "Integrity checksum changed again (2nd time)."
Portion of the log(s):
[COLOR="Red"]
Integrity checksum changed for: '/etc/blkid.tab.old'[/COLOR]
Size changed from '809' to '879'

 --END OF NOTIFICATION
```
Sorry about the long log, but I'd rather post it now than have someone ask me to post it later.

Note that I removed the actual checksum values (it will list the old and new checksums, both a SHA1 and MD5) for better readability.

Are these notifications something I should be worried about? I know that things such as motd and blkid update periodically and thus would justify the checksum change, just checking overall.

Thanks!:-\"

---

### Post by bodhi.zazen on 2009-04-15
Your check sums will change obviously when you change your system files.

So if you did not add a new user or group to the system, then you have a problem.

If you added a new user or group you are OK as that will obviously change the sums of the relevant files.

---

### Post by physeetcosmo on 2009-04-27
> **bodhi.zazen said:**
> Your check sums will change obviously when you change your system files.

So if you did not add a new user or group to the system, then you have a problem.

If you added a new user or group you are OK as that will obviously change the sums of the relevant files.

Maybe you can answer this: I found in my /etc/passwd file that there are three "extra" users that cannot login but are listed.

ossec
ossecm
ossecr

What are these for? I know they are attached to the Ossec HIDs software but can anyone explain what these users are for? I think they might be the reason I keep getting checksum rule fires from Ossec itself. This might be a question for the Ossec website.

Thanks!:rolleyes:

---

