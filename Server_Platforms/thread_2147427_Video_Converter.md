---
title: "Video Converter"
date: 2013-05-21
forum: Server Platforms
---

### Post by motermouth15 on 2013-05-21
I'm currently running a little headless ubuntu server that does nothing more than run plex. That way all of the media I have on it can be streamed to any of my dlna enabled devices throughout my house. Does anyone know of an easier to use video converter that would work on my server? I would preferably like one that has a webui if that is at all possible. That way some of my roommates can use it and won't have to spend a lot of time learning how.

---

### Post by ian dobson on 2013-05-22
Hi,

It doesn't have a web interface but I use handbrake to transcode Videos.

Maybe just create a simple cron Job that checks for Video files in a specific Directory and just call handbrake to transcode it.

Regards
Ian Dobson

---

### Post by rubylaser on 2013-05-22
> **ian dobson said:**
> Hi,

It doesn't have a web interface but I use handbrake to transcode Videos.

Maybe just create a simple cron Job that checks for Video files in a specific Directory and just call handbrake to transcode it.

Regards
Ian Dobson
+1 for Handbrake.  It's cli interface is easy to understand and not too difficult to script.  If bash scripting is too tricky, setup a simple Samba share on the server and use Handbrake to queue jobs on a separate encoding machine that uses the share as it's destination.

---

