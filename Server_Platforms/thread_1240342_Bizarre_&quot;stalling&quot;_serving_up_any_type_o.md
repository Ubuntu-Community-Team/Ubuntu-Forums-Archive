---
title: "Bizarre &quot;stalling&quot; serving up any type of video (mp4, 3gp) over HTTP [reproducible]"
date: 2009-08-14
forum: Server Platforms
---

### Post by uramadman on 2009-08-14
I have a collection of MP4s and 3GP files being served over http. The videos are embedded within a page using html/javascript and play fine when accessed within LAN.

 Yet any time when accessed externally, videos begin to load but never play. On closer examination the entire server appears to have stalled. The page will not refresh at all. After ~15 minutes the server again becomes responsive as if nothing happened.

In short:
**Attempting to access a "video" file makes the server become temporarily unresponsive**.


 I can't understand why it becomes unresponsive trying to access any video file. How is it even aware of what type of file it is ? It might as well stall trying to serve up a jpeg. No difference trying to load them with this style: [www.site.com/vid.mp4](www.site.com/vid.mp4)

 Everything is vanilla, I have no modules. The exact same stalling occurs on all http servers I have tried, no difference serving up the videos on linux/win32. I first thought it was only an apache problem. Error/Access logs show nothing of interest.


Worth mentioning:

While stalled, if I terminate one of the two httpd.exe's it will become responsive again or shut down apache depending on which I terminated (they are both identical).

The size of the video makes a difference in how long it is stalled (a 1MB video will stall the server for ~3 minutes and a 10MB video for ~15 minutes).


EDIT: I found a http server that works correctly, nginx

---

