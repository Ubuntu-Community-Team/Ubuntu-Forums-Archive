---
title: "preconfigure busybox"
date: 2012-05-10
forum: Server Platforms
---

### Post by joe_lovick on 2012-05-10
Hi,
    I have a server that is going into a remote location where physical access is going to be severely constrained. I would like to set up BusyBox so that if in the event of a problem with booting ubuntu proper, such that busybox loads instead, i will be able to connect to it over the network and do remote diagnostics. this is in the spirit of covering all my bases ( deprecating sods law and such )

    As i understand it busybox has atleast a telnetd and a sshd, but for these to work, the network has to be brought up, and in my case dhcp address retrieved.

 Can anyone point me to/ or provide me with instructions as to how to preconfigure the network and embed these settings within my startup scripts.

 Thanks in advance, i really appreciate it.

 Joe

---

