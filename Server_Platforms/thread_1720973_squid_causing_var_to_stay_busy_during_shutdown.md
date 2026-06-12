---
title: "squid causing /var to stay busy during shutdown"
date: 2011-04-03
forum: Server Platforms
---

### Post by ryokenau on 2011-04-03
i just wanted to check if its something silly ive overseen and if anyone else is having this problem...

im running Ubuntu 10.04.2 LTS with latest version of squid 2.7.STABLE7-1ubuntu12.2. now when i shutdown or reboot the system, it says something along this lines of umount: /var is busy (check using lsof...). this is followed by text in red: [[COLOR="Red"]fail[/COLOR]].

when the system starts up again, i can see /var journal is recovering, so the /var partition was not cleanly unmounted during shutdown. obviously, there is a risk of filesystem corruption here. FYI, i have /var and other important mountpoints as separate partitions (LVM; ext4).

to confirm my suspicions of squid still running during shutdown, i checked /var/log/squid/cache.log and there is no indication that it received the signal to terminate. if i manually run "stop squid", then cache.log would show that squid has stopped successfully (or words to that effect).

to confirm that /var is locked by squid during shutdown, ive added a script to run "lsof | grep var" before filesystems are unmounted. and voila! it indicates that various files used by squid in /var such as swap.state are still open. hence, the next system startup would result in /var recovering journal again.

finally, i tried running "stop squid" before issuing the shutdown command and it successfully unmounts /var and i do not get /var recovering journal on the next system startup.

something fishy is going no here (excuse the pun ;)), comments/suggestions welcome.

---

### Post by BkkBonanza on 2011-04-03
It seems like you've taken care to research this well, so maybe you should report it as a bug in the ubuntu launchpad page. I see they have another issue or two related to switching runlevels so maybe these things are related to a problem with startup/shutdown scripting? 

[https://launchpad.net/ubuntu/+source/squid/+bugs](https://launchpad.net/ubuntu/+source/squid/+bugs)

See this comment on another bug there - which hints that it's worth looking at upstart init config related to squid.

> a problem in the upstart script that only exists in the Ubuntu package, and so there's no other upstream for it. This was one of the first services ported to upstart and so we're learning a lot through fixing the bugs in its upstart job and surrounding maintainer scripts.

---

### Post by ryokenau on 2011-04-04
Thanks for your suggestions BkkBonanza.

I have reported this bug, along with more details at:
[https://bugs.launchpad.net/ubuntu/+source/squid/+bug/750371](https://bugs.launchpad.net/ubuntu/+source/squid/+bug/750371)

I hope this gets fixed :)

---

### Post by KingChango on 2011-08-22
Hi ryokenau!
> **ryokenau said:**
> I have reported this bug, along with more details at: [https://bugs.launchpad.net/ubuntu/+source/squid/+bug/750371](https://bugs.launchpad.net/ubuntu/+source/squid/+bug/750371)

I hope this gets fixed :)
I posted a comment on that bug you reported. I don't think its a duplicate for the mysql bug that seems to be similar. Check my comments and let me know if that fixes it for you.

---

