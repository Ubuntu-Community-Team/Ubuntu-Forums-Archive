---
title: "Apache never restarts automatically after apache update, on one system"
date: 2017-07-27
forum: Server Platforms
---

### Post by tt8811 on 2017-07-27
Among a cluster of servers all running 16.04 and apache, on one system apache never restarts automatically after it has been upgraded via apt. It restarts fine manually, and at boot. All of the other systems at the same OS and app levels don't have this problem -- apache always restarts automatically on them after an apt update of apache.
The error log on the troublesome system just shows:
[Thu Jul 27 16:53:42.157053 2017] [mpm_prefork:notice] [pid 10804] AH00163: Apache/2.4.18 (Ubuntu) configured -- resuming normal operations [Thu Jul 27 16:53:42.157150 2017] [core:notice] [pid 10804] AH00094: Command line: '/usr/sbin/apache2'
Any clues? Thanks!

---

### Post by wildmanne39 on 2017-07-27
*Thread moved to **Server Platforms**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by tt8811 on 2017-07-27
I didn't set any non-default properties. Message was copied in as plain text and showed no unusual properties in preview.

---

