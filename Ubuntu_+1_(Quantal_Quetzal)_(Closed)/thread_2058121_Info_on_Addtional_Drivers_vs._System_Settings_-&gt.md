---
title: "Info on Addtional Drivers vs. System Settings -&gt; Details"
date: 2012-09-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kyleabaker on 2012-09-15
Has anyone else noticed that the Graphics details in System Settings -> Details is not available, while its easily available from the Additional Drivers window?

[[IMG]http://imageshack.us/a/img692/4588/softwaresourcesvsgraphi.png[/IMG]]("http://imageshack.us/a/img145/4588/softwaresourcesvsgraphi.png")

As far as I know, the System Settings -> Details application is controlled by Gnome. I haven't checked this screen with open source drivers enabled, but I assume it works for them. It'd be nice to see Ubuntu patch this so that the proprietary drivers are "recognized" as well since its clearly possible as seen in Additional Drivers.

---

### Post by RaZoRbelarus on 2012-09-15
Try installing mesa-utils. It works for me with my Intel SandyBrigde.

---

### Post by coffeecat on 2012-09-15
> **kyleabaker said:**
> I haven't checked this screen with open source drivers enabled, but I assume it works for them.

Unfortunately not, at least not with my Radeon HD6450 card using the open source driver. I get the same details window as in your screenshot.

---

### Post by thotz on 2012-09-15
Thank you for me it works with Intel Ivy Bridge.

---

### Post by kyleabaker on 2012-09-15
> **thotz said:**
> Thank you for me it works with Intel Ivy Bridge.

Can you post a screenshot? I'm curious to see what it looks like when its working.

---

### Post by effenberg0x0 on 2012-09-16
I'm have manually installed nvidia drivers, so nothing new here:

[ATTACH]224216[/ATTACH]

Regards,
Effenberg

---

### Post by thotz on 2012-09-16
> **kyleabaker said:**
> Can you post a screenshot? I'm curious to see what it looks like when its working.

Tried to post a screenshot, but it's not working.
But you won't see more as that there is written Intel IvyBridge ok?

---

### Post by cariboo on 2012-09-16
> **thotz said:**
> Tried to post a screenshot, but it's not working.
But you won't see more as that there is written Intel IvyBridge ok?

To post a screenshot, you need to use the advanced editor, then scroll down to Manage Attachments, or use one of the many picture hosting web sites, and use the link that they provide.

---

### Post by VinDSL on 2012-09-16
> **effenberg0x0 said:**
> I'm have manually installed nvidia drivers, so nothing new here:

[ATTACH]224216[/ATTACH]

Regards,
Effenberg
Dittos...

(Please excuse the dust -- I'm debugging Conky)

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-16-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-16-sep-2012-2.png")[/INDENT]

---

### Post by sammiev on 2012-09-16
> **RaZoRbelarus said:**
> Try installing mesa-utils. It works for me with my Intel SandyBrigde.

I tried mesa-utils and it now displays my Graphics details. TY

---

