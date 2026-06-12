---
title: "Managing IP Cams through single interface (including Pan/Tilt/Zoom controls)"
date: 2012-05-06
forum: The Cafe
---

### Post by effenberg0x0 on 2012-05-06
I need to have a single secure webserver/URL receiving video streams from some wireless IP Cams, installed in different places. This is not hard to do and there are many tutorials out there.

However, my situation is a little more specific:  these cameras have pan/tilt/zoom controls in their embedded web interfaces (which are insecure and I'd like to disable, thus controlling them exclusively through this unified interface).

I could code something to send the control commands to each camera IP/Port, and set each one to only accept connections from the server MAC or IP. But it would take me too much time to do something professional and reliable in the interface.

There are many Windows and paid solutions for it. I'm not finding a good option in Open Source. Has anyone ever implemented something like that, or is aware of a good software to manage this sort of cams?

Regards,
Effenberg

---

