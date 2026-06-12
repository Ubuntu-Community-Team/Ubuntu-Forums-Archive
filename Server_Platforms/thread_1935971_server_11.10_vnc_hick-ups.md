---
title: "server 11.10 vnc hick-ups"
date: 2012-03-05
forum: Server Platforms
---

### Post by pinjan on 2012-03-05
After 11.10 server was installed I installed/set VNC up and tried to access headless server. Everything is otherwise ok but menu to the left is missing and in top menu items are also missing from right-hand side.

Tried to delete ```
/tmp/unity_support_test.0
``` file that is created by Ubuntu unity support  tool script. After that menu on left-hand side is visible via vnc:

[[IMG]http://img821.imageshack.us/img821/5039/leftmenu.jpg[/IMG]](http://imageshack.us/photo/my-images/821/leftmenu.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

 but nothing is visible in top menu !
That file gets also created automatically time to time so it is not good workaround. 

Any ideas how to fix this ?

---

### Post by pinjan on 2012-03-06
I found workaround for this behaviour, added StartVNC script that is always launched at start up and which creates two VNC sessions:

#!/bin/sh
echo "JOB RUN AT $(date)"
echo "============================"
echo ""
/usr/bin/vncserver -geometry 1920x1200 -depth 24
/usr/bin/vncserver -geometry 1920x1200 -depth 24
 At least then I get UI with left menu and I can live with that. Otherwice I get UI without left menu and only some topmenu items are available. Just do not understand why this works like this :confused:

---

