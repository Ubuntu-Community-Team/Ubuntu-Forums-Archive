---
title: "GNUMP3D - starting and stopping"
date: 2005-12-11
forum: Server Platforms
---

### Post by Granduke on 2005-12-11
When trying to start GNUMP3D I get this error message
"Couldn't create the listening socket"
I've set the port to 8888 and 7878 with no avail.

I'm wondering maybe the app is already running. I did "sudo gnump3d" to start.  Is this correct? If so how do I stop the server?

---

### Post by Zelut on 2005-12-11
try the following:

sudo /etc/init.d/gnump3d stop
sudo /etc/init.d/gnump3d restart

the gnump3d script located in /etc/init.d/ house the startup/restart/stop scripts.  Hope that works for you..

---

### Post by Granduke on 2005-12-11
Thanks for your help kuyaedz.
That's what I needed.

---

