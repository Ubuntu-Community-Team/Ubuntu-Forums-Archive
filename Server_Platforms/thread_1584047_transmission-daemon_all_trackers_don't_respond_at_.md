---
title: "transmission-daemon: all trackers don't respond at startup"
date: 2010-09-28
forum: Server Platforms
---

### Post by papibe on 2010-09-28
Hi all, I'm running transmission-daemon 1.93 on Ubuntu Server 10.04. Every time I turn on the server, transmission-daemon starts automatically (standard installation).

However, when I go to check the web interface to see how things are doing, all trackers from all torrents (both completed and downloading) have this error:
```
Announce error: tracker did not respond - Today 01:04:18 AM
Next announce in 26 min 41 seconds
Last Scrape: Today 01:06:33 AM
```

I have to wait the next announce (26mins!) to finally start getting peers. PEX amd DHT are set, but they don't get peers fast enough. It is only when the announce event is successful, that I start getting acceptable download speeds.

After doing some experiments, I learned that if I paused all the torrents and then resume them back, the error is gone. I wonder if there's a bug on the start up process of transmission-daemon.

Is there anything I can do, so the wait for the next announce, or the manual intervention can be avoided?

I appreciate any comments and suggestions.
Thanks in advance.

---

### Post by papibe on 2010-09-28
bump

---

### Post by Charles Kerr on 2010-09-29
Several popular trackers have been experiencing outages the past few days.

When a tracker is down, Transmission can't connect to it... :)

---

### Post by papibe on 2010-09-29
Yes, I'm aware of that.

But that's not the problem since Transmission is able to connect to the trackers (the ones that are up) either if:
[LIST]
[*]I stop and restart the transmission-daemon service, or
[*]I pause all torrents and resume them again.
[/LIST]

My suspicion is that the service is initiated too soon, and it can't access the network properly.

Any idea how to fix that?
Thanks in advance.

---

### Post by papibe on 2010-09-30
Anyone knows how services are setup to start, order and stuff like that?

Regards.

---

### Post by WinstonChurchill on 2010-10-25
You're not using the most recent version - upgrade to 2.11

---

