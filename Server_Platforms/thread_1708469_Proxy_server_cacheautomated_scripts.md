---
title: "Proxy server cache/automated scripts"
date: 2011-03-16
forum: Server Platforms
---

### Post by steaksauce on 2011-03-16
This is a theoretical question I thought about during my studies for a network exam:
If you use a caching feature on a proxy server running Ubuntu Server, could you create an automated script that would update the pages in the cache at certain times during the day?

Say I'm a network admin, and I use web page caching to increase the performance of the network since many of the client workstations access the same web pages. The cached pages aren't always updated, but could an automated script be created to say, update the pages during the lunch hour, and an hour before the office opens?

Sorry about my wording, it's a neat little idea the popped in my head when I was learning about them, I just want to know if it's possible, not how (unless you really want to tell haha)

---

### Post by BkkBonanza on 2011-03-16
All you would need to do is make a list of urls to hit and then run a script on it that opens each page so that the cache updates. Here's an example, though you may need something different (and I haven't tested this, it's just off the top of my head)...

Put your url list in urls.txt, one per line.
```

#!/bin/bash

while read X;
do
wget $X -O /dev/null
done < urls.txt


```

For more info on wget's many options, type **man wget**
This script can be run anywhere that it would use the proxy.
Add a cronjob for when you want to schedule an update.

---

### Post by steaksauce on 2011-03-16
> **BkkBonanza said:**
> All you would need to do is make a list of urls to hit and then run a script on it that opens each page so that the cache updates. Here's an example, though you may need something different (and I haven't tested this, it's just off the top of my head)...

Put your url list in urls.txt, one per line.
```

#!/bin/bash

while read X;
do
wget $X -O /dev/null
done < urls.txt


```For more info on wget's many options, type **man wget**
This script can be run anywhere that it would use the proxy.
Add a cronjob for when you want to schedule an update.

Thanks! Will take note :)

---

