---
title: "Ubuntu shares in nautilus every host returns to local host"
date: 2014-06-24
forum: Server Platforms
---

### Post by Seb_Boffen on 2014-06-24
Ubuntu shares in Nautilus every host returns to local host:

I open up pc1 in Nautilus network groups and open up pc2, pc2 shows the shares of pc1 this happens with all hosts, they all return to pc1 instead of showing the correct shares from the host.
I'm running Ubuntu server 14.04 with config files taken from 12.04 and older ones from 10.04, this issue is regarding Samba version 4.1.6-Ubuntu in combination with Nautilus.

I have reinstalled samba and came to realize unwell configured windows shares make Ubuntu do this, issue has been resolved by correcting the rights on the windows shares.

---

