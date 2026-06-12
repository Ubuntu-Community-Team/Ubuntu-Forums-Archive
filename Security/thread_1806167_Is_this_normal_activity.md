---
title: "Is this normal activity?"
date: 2011-07-17
forum: Security
---

### Post by babakott on 2011-07-17
I recently installed Moblock on Xubuntu, and have been dinking around with it. Today, I open Mobloquer and notice my log file is streaming by at a fast pace. Most of it seems to be from china. Here is a screenshot.
[IMG]http://i55.tinypic.com/b4x4l1.png[/IMG]

At the time I took this screenshot, I had nothing with an active connection to the internet. I am just wondering if this is normal? Honestly I have never looked at incoming traffic before, and am not sure what I should expect.

Thanks.

---

### Post by bodhi.zazen on 2011-07-17
Nothing like reading to logs to instill security.

If you want to monitor such things, use snort, snort will tell you what traffic is potentially problematic.

---

### Post by babakott on 2011-07-17
> **bodhi.zazen said:**
> Nothing like reading to logs to instill security.

If you want to monitor such things, use snort, snort will tell you what traffic is potentially problematic.

Yeah, that spooked me a bit. I will check out snort. Thanks!

---

### Post by jre on 2011-07-24
If you had e.g. a torrent shortly (a few hours) running before, people might still try to connect to you. [Follow this link]("https://help.ubuntu.com/community/MoBlock#How%20do%20I%20find%20out%20which%20IP%20or%20port%20was%20blocked?") to learn how to check the port of the blocked traffic. If it is e.g. your torrent application's port you don't need to examine the packets in depth.

---

