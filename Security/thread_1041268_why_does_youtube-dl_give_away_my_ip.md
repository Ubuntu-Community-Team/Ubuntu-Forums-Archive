---
title: "why does youtube-dl give away my ip"
date: 2009-01-16
forum: Security
---

### Post by jakupl on 2009-01-16
I didn't really know where to put this, but I suppose it is a security question so here goes.

I use a program called youtube-dl to downoad youtube clips through the terminal. Today I downloaded a piece that we are playing at with my symphony orchestra, and I noticed this.

```
jakup@bobby:~$ youtube-dl http://www.youtube.com/watch?v=CTdbYaQIg-0
Retrieving video webpage... done.
Extracting URL "t" parameter... done.
Requesting video file... done.
Video data found at http://v3.cache.googlevideo.com/get_video?origin=sjc-v88.sjc.youtube.com&video_id=CTdbYaQIg-0&ip=MY-IP-ADDRESS&signature=C150A15AC314817445CCDE3C45A1833CF535B64D.69558855E36B6CD05986A46C6D756F7DD7953BC2&sver=2&expire=1232148876&key=yt1&ipbits=0
Retrieving video data: 100.0% (  20.80M of 20.80M) at   37.78k/s ETA 00:00 done.
Video data saved to CTdbYaQIg-0.flv
```

where the "MY-IP-ADDRESS" was my ip. 

Why does give away the ip at the http://

Ps. If you like classical music, check this one out. It's kinda boring at the beginning, but the last half is amazing, and we play it better :)
It's called "I vespri siciliani" Sinfonia. Written  by Verdi.
Just follow the http at the beginning of the code.

---

### Post by HermanAB on 2009-01-16
Your IP address is not a secret.  TCP/IP is a packet switched system.  Your IP address is contained in *every* packet of data.  This is required to get the data to you.

Cheers,

Herman

---

