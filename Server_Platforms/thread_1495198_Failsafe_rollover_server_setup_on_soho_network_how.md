---
title: "Failsafe rollover server setup on soho network how?"
date: 2010-05-27
forum: Server Platforms
---

### Post by dave37 on 2010-05-27
Hi Group,

It's been a year since I set up an Ubuntu Hardy file server for my wife's accounting practice, and thanks to rsync and rsync.net when the secondary hard drive in the server decided to give up the ghost we were able to pull down all the data from rsync with only 1 day's data lost.

However, as the practice is growing I would like to set up a backup server.  A forum member posted to me about a year ago about using drdb heartbeat, and while I have looked in to it a bit it seems quite intimidating.

What we would like to do is set up another machine with Hardy (not server edition, desktop, as my CLI is not that great!) on a SOHO network to act as a failsafe server.  That is, if the primary server can't work, (child unplugged the cord while playing, etc) the current share of "server-files" is automatically available on the secondary server, which has stayed in sync with the primary server for data changes.

Tall order I know, but if anyone can help me with this I'm sure it would be valuable to the community and help Ubuntu penetrate even further.

I must say our Ubuntu file server has performed flawlessly, securely, and with a minimum of fuss.  But as replacing a hard drive and downloading the data took days we'd like to have that quick rollover allowing us to repair at our leisure.

Current network topology is 5 workstations using files served from an Ubuntu Hardy file server, a number of switches in between due to historical additions, with a high speed cable modem and Dlink router as the gateway.

Thanks in advance to all that can assist!

---

### Post by hictio on 2010-05-28
First of all, why Hardy, out of curiosity, I mean, specially now that there is Lucid Lynx available, and that it will give you years of updates on the Server.

For syncing the data between your primary server, and the fail over one, I would recommend using [rsnapshot](http://rsnapshot.org/), for instance.

---

