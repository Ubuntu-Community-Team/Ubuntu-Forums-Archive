---
title: "Kannel Issue with var/run/kannel"
date: 2008-12-10
forum: Server Platforms
---

### Post by stock1232 on 2008-12-10
I installed Kannel from the repositories. When I try and start the boxes, it says /var/run/kannel no such file or directory. When i check the directory var/run/ there is no kannel directory. Therefore I created a folder and tried to start the boxes. it worked with no errors. However when I reboot my server the kannel directory disappears. I read on another site:

Some Linux distributions are configured with /var/run as a RAM disk
(tmpfs). As a result, any directory created inside of /var/run
will not persist between reboots.

You will need to modify your startup script to create the /var/run/kannel
directory if it does not already exist.

Is there an easy fix out there to make the directory permanent?

Thanks,
Drew

---

