---
title: "Alter DNS on 18.04.1 LTS compiled image cloud server after adding IPv6"
date: 2018-11-09
forum: Server Platforms
---

### Post by learning-curve on 2018-11-09
We added an IPv6 address to our 18.04.1 LTS cloud server and it all worked just fine, or so we thought... One  slight minus 'effect' that we immediatley noticed when testing was that the DNS that was used (when the 18.04.1 LTS image was initially compiled / supplied with on our cloud server) didn't work  perfectly any more <Edit> This was corrected by altering /run/systemd/resolve/stub-resolv.conf via a crontask <Edit>

---

