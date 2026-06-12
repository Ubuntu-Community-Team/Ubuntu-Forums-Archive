---
title: "&quot;The permission of the setuid helper is not correct&quot;"
date: 2009-04-15
forum: Security
---

### Post by whitteng on 2009-04-15
I'm getting "The permission of the setuid helper is not correct" error which seems to break all graphical system management tools, even for root. Does anyone know how to fix this?

Thanks,
Gary Whitten

---

### Post by nikhil760 on 2009-12-25
Bit late, but may help someone. I also got the same error recently and it seems like a problem with dbus.
Here's how I fixed it :
log in tty1 console as root
stop gdm
startx
Now if you are able to see the desktop, connect to the internet and reinstall dbus related stuff from synaptic.

---

