---
title: "Ubuntu server 12.04 unitmely freezes"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sulliwane on 2012-04-15
Hi everybody :p,

I set-up a fresh Ubuntu 12.04 install on my home-server. At the beginning it would freeze on SSH access after 10 min of inactivity.
Then I configured the "keep-alive" instruction and "apt-get dist-upgrade" the system. For on reason or another, I thought that the freezing issue was solved, but actually it was only becoming less frequent, but didn't vanished ! And now, I don't think it's due to an SSH session anymore...

For example, yesterday it crashed...Here is the syslog of yesterday  

/var/log/syslog.1  (of 14/04) attached

Now before any SSH access, I pry to have my server accessible...it's depressing :mad:

Does someone has an idea ? 

ps : I also have this log I find strange

/var/log/auth.log  (attached)

Thanks a lot, and cheers from france !

---

### Post by darkod on 2012-04-15
Are you doing this just for testing purposes?

12.04 LTS is not released yet, it is still in development. There still might be issues that will be resolved by the release date.

---

### Post by Jonathan L on 2012-04-15
Hi sulliwane

.. et bienvenue a notre ami de france!

> this log I find strange

I took a look at the auth log and you might want to just check your crontabs to see that they're legit, and of course ask yourself if the ssh login (as victor) was legitimate and you really did sudo su.  I saw nothing unusual in the system log, so long as openvpn was yours.

If you want a server for home purposes you might consider 10.04 LTS which won't have any surprises, alternatively wait until 12.04 is properly released.  For workhorses it's usual best to be very conservative, and remember 10.04 LTS is still supported to 2015.

Just a perspective.

Kind regards,
Jonathan.

---

### Post by sulliwane on 2012-04-15
Hey, thanks for your answers :p

I know 12.04LTS is still in beta stage, but as the release is out in less than a month...i was tempted :o)

So if you don't find any "suspicious" things in the log, it might be a "development issue" and i understand well that in this case, it's better to wait the stable release !

i found the auth.log strange because the repetitive cron task...otherwise, the openvpn is mine, and victor it's me so nothing to be worried about ? :p

thanks anyway, I will definitely wait the 12.04 stable release and withstand this bug until then...

à très bientôt !

---

### Post by Bucky Ball on 2012-04-15
> **Jonathan L said:**
> 

If you want a server for home purposes you might consider 10.04 LTS which won't have any surprises, alternatively wait until 12.04 is properly released.  For workhorses it's usual best to be very conservative, and remember 10.04 LTS is still supported to 2015.

Just a perspective.

Kind regards,
Jonathan.

+1. LTS for production, stability, reliabilty and long term support, of course. ;)

---

### Post by Doug S on 2012-04-15
It is getting very late in the 12.04 release cycle. The system installed is getting very close to what will be released. There could be value added to the final release in trying to understand the root issue with this case. That being said, I looked through the log files and didn't notice anything odd.
My suggestion is for a moderator to move this thread over to the Ubuntu + 1 (precise) forum, where it might get better exposure and suggestions.

---

### Post by uRock on 2012-04-15
Moved to Ubuntu+1.

Please keep posts on topic.

---

### Post by sulliwane on 2012-04-15
It crashed again :mad: ! Maybe during one of the last 5 hours...and I really don't know why

---

### Post by sulliwane on 2012-04-23
hi everyone,

come back to say that since the last update, everything seems working just fine.

I didn't experienced any more freezes or crash and I enjoy it :p

Long live Ubuntu, long live Linux !

---

