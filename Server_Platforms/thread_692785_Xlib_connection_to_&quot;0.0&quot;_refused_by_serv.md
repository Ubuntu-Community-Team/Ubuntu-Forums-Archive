---
title: "Xlib: connection to &quot;:0.0&quot; refused by server"
date: 2008-02-10
forum: Server Platforms
---

### Post by Adnarim on 2008-02-10
Hi,
I posted this in Security because I think that's an security issue. I wanna create a gdm-theme and need to do a screenshot of it. Therefor I found this script:
```

chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/screenshot.png

```

So If I'm on the gdm-front I change to tty1 and execute this script with root-rights. But I'm always getting this error:
> 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

import: unable to open X server `:0.0'.


I think this has to do with the Xauthority-file or? How can I temporarly allow these connections to the X-Server?

greets

---

### Post by Adnarim on 2008-02-10
Solution:
xhost -
executing the command
xhost +

---

