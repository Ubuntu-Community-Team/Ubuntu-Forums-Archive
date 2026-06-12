---
title: "Running Chrome/Chromium from BASH"
date: 2012-05-20
forum: Server Platforms
---

### Post by ubunturero on 2012-05-20
Hi, first at all, sorry for my poor english.

I'm trying to make a bash script to run chrome/chromium from a terminal with the --proxy-server="ip:port" parameter, it read the ip:port from a txt file, and restart every 15sec, something like that:

```
#!/bin/bash
while read proxy ; do
        /opt/google/chrome/chrome --proxy-server=\"$proxy\";
        sleep 15
        pkill chrome
        sleep 1
done< proxy.txt
```

Chrome/Chromium runs with the error 

```
Error 336 (net::ERR_NO_SUPPORTED_PROXIES): Unknown error." 
```

If i put manually /opt/google/chrome/chrome --proxy-server="ip:port; it works perfectly.

Any solution for that?

---

