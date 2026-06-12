---
title: "Apple's Latest Tool: Friendliness to the extreme or SCAM?"
date: 2005-11-28
forum: The Cafe
---

### Post by jdong on 2005-11-28
[http://www.apple.com/support/downloads/broadbandtuner10.html](http://www.apple.com/support/downloads/broadbandtuner10.html)

Apple released with front page digg fanfare its "broadband tuner"... A bit more reading, this merely sets the following SYSCTL values which could simply be added to /etc/sysctl.conf:

```

net.inet.tcp.sendspace: 131072
net.inet.tcp.recvspace: 358400
kern.ipc.maxsockbuf: 512000

```
**NOTE**: These changes are NOT compatible with Linux, don't try this on a Linux system... the variables go by different names (mostly net.ipv4.tcp.*)...


Does this really help with performance? From initial skepticism, probably not... I've used *BSD and Linux quite extensively in both dial-up link and Gigabit ethernet environments, and I've found that the defaults scale quite nicely for both...


Now, if Apple released a Wondershaper equivalent GUI that optimizes the packet queue to favor responsive interactive services over background tasks (i.e. that unlimited bittorrent seeding shouldn't affect web browsing speed for the rest of your network), I would be applauding their efforts. But for now, this belongs in the pile of Windows style MTU tweak applets...

---

