---
title: "samba MYOB slow report processing"
date: 2011-10-07
forum: Server Platforms
---

### Post by mlinux on 2011-10-07
Tested two winxp pc running MYOB with data store in samba share folder (Ubuntu 10.04LTS). It takes very long time to generating report as compare to store share data file on xp machine.

During processing, network traffic on xp constantly shows 29% on 100Mbps connection for 5 minutes and the progress bar hardly move, winxp seems hang/not responding but eventually report appear.

When the same data file move to one of the xp machine, processing from the other xp machine take only less than 30 secs and the network traffic only shows a few spike of usage of less than 50%. 

Any clue of the samba or winxp network setting problem?

---

