---
title: "clamav should be included in main/security?"
date: 2005-01-27
forum: Server Platforms
---

### Post by sevenm on 2005-01-27
as it is, the only usable open-source antivirus for linux is only in 'universe' and is noticeably outdated, this can be considered a security issue i guess..

> WARNING: Your ClamAV installation is OUTDATED - please update immediately !
> WARNING: Current functionality level = 2, required = 4

---

### Post by Jad on 2005-01-27
[QUOTE=sevenm]as it is, the only usable open-source antivirus for linux is only in 'universe' and is noticeably outdated, this can be considered a security issue i guess..

> WARNING: Your ClamAV installation is OUTDATED - please update immediately !
> WARNING: Current functionality level = 2, required = 4[/QUOTE]
 Why you need anti virus?
are you connected to Windows machines?

---

### Post by sevenm on 2005-01-27
if you are using mailserver, you definitelly need antivirus. either way, it could be used to scan html with the squid, etc.
i mostly need it for server uses.

---

### Post by az on 2005-01-27
Debian is setting up a volatile archive for this sort of thing.  Packages for Stable with regular updates.

The problem now is that released packages can not be upgraded, just updated.  What we are descibing is a antivirus package that would need upgrades, and not just updates.  (changing version numbers...)

---

### Post by sevenm on 2005-01-27
yes, debian in this respect has solid strategy, but i feel that some software should be threated differently - like antiviruses.

maybe there should be decided list of software which will be reviewed and upgraded in a way that does not break things when theres important upstream update - like increase in functionality level of clamav - without which the antivirus database updates arent that useful if they cannot be used correctly.

these packages could be even put to separate package branch like 'warty/upgraded' to have a choice to use them or not.

actually there are some personal package repositories i have seen where people put backported packages from testing/unstable to stable in the way i have described.

of course all this means some additional work etc, and could potentially break some things anyway... and there possibly are other ways things could be done.

personally, i prefer to stop maximum count of viruses and the only reasonable ways now is either to use clamav from unstable when its upgraded or to custom compile it, which breaks some things or principles anyway. 

all this comes down from my experience of using debian from 2.0 times. now my typical server setup consists of debian stable with 50% updated to testing and sometimes some unstable packages, with cron-apt autoupdating everything and monit monitoring all the services which could be affected by autoupdate.
this setup is quite viable and things break rarely, but i'd prefer to have a stable up to date setup which is the ubuntu aim too i believe.

that said, i see some really nice iniciatives here at ubuntu -  and i guess some issues i had with debian could be brought for the discussion and could lead to general improvements ;)

---

### Post by jdodson on 2005-01-27
[QUOTE=sevenm]
these packages could be even put to separate package branch like 'warty/upgraded' to have a choice to use them or not.
[/QUOTE]

this is a really great idea.  i hope a developer takes notice of this thread.  if not, head into the developer irc channel and propose your plan.

---

