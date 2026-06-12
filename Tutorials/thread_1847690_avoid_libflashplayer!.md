---
title: "avoid libflashplayer!"
date: 2011-09-21
forum: Tutorials
---

### Post by ykanello on 2011-09-21
if you are one of those people like me, really annoyed by the libflashplayer (AKA the flash plugin), there is an alternative (second one, apart from not using sites with flash which is  the best solution really).

You can actually remove all forms of flash plugin, and install the Google Chrome browser. (Not the opensource chromium hasn't really worked on my systems)
Sometimes it will still bitch that you dont have the plugin installed to see all the features of flash (ads and spam mostly) but guess what, everything that you need to watch, works! 

I made sure there is no libflashplayer running, only a thread of chrome:
```
ykanello  7315  7259 41 13:33 ?        00:00:09 /opt/google/chrome/chrome --type=plugin --plugin-path=/opt/google/chrome/libgcflashplayer.so --lang=en-US --channel=7259.0xb895b420.1687901362
```

I am not big on flash videos, so I haven't tried 2000 tabs with crappy youtube videos but one or two I tried, works like a champ.

```
cpu load is 'normal' for flash   7315 ykanello  20   0  272m  59m  16m S 28.8 12.0   1:43.55  chrome   
```                       

I am not sure if this will overcome all the problems with flash, but for me so far works, and I thought of sharing it with y'all :)

---

