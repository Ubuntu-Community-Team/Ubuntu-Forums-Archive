---
title: "DSS: New Playlist: Available Content Empty"
date: 2010-01-24
forum: Server Platforms
---

### Post by ICEB3AR on 2010-01-24
Hi 
I've installed DarwinStreamingServer 5.5.5 with User qtss:qtss (setted up manually). Everything fine.
I changed the permission of the config-file 
```
sudo chmod 755 /etc/streaming/streamingserver.xml 
```
And Configured the webinterfaces. So far so good.

Streaming like: rtsp://<Server-IP>/sample_100kbit.mp4 worx.

But i can not set up Playlist and the List where you should find your files is empty, although there are files in my default directory.

I Expect that any file permissions are wrong, but which.

It would be very nice, if you have a guess or a hint.

---

### Post by ICEB3AR on 2010-01-28
Bump

---

### Post by ICEB3AR on 2010-01-29
It was a problem with the Browser i used. The ajax code of DSS didn't work in that. So everything is fine.

---

