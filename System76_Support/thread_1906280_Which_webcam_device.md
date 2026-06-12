---
title: "Which webcam device?"
date: 2012-01-08
forum: System76 Support
---

### Post by daniel.cotter on 2012-01-08
PanP7, one year old, Ubuntu 11.10, equipped with an integrated webcam.

I would like to discover the exact device (manufacturer, model) of my webcam, so I may download the appropriate driver for it. 

The problem I am hoping to address is that the video freezes when holding a video chat in Skype.  I have not been able to reproduce the issue using cheese, so it may be a problem with Skype itself.  My plan is to install a driver to see if that addresses the problem.  I can be dissuaded from that course if I get advice to the contrary, though.  Skype recognizes the webcam as a "BisonCam, NB Pro" at /dev/video0, but I don't even know if that is the correct device, or whether Skype is simply emulating that device.

Thanks for whatever advice you can offer...
Daniel

---

### Post by isantop on 2012-01-09
That's the correct device, and all of our webcam drivers are currently provided by Ubuntu. Installing a different driver would be unwise since it could break other areas of the system. The issue is definitely a Skype issue. Are you using the latest version of the client?

---

