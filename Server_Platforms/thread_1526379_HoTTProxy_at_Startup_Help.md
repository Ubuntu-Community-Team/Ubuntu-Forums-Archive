---
title: "HoTTProxy at Startup Help"
date: 2010-07-08
forum: Server Platforms
---

### Post by ResentfulDoom on 2010-07-08
I am trying to get HoTTProxy to run at startup. I tried to follow what the person did in this thread. [http://ubuntuforums.org/showthread.php?t=1101159]("http://ubuntuforums.org/showthread.php?t=1101159")

But it still does not work.

This is the script I wrote. 

```
#!/bin/bash
cd /home/server/HoTTProxy
perl HoTTProxy.pl>&/home/server/HoTTProxy/startup.log
```

---

