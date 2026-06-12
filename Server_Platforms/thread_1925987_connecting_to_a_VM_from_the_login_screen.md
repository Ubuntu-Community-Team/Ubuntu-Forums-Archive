---
title: "connecting to a VM from the login screen"
date: 2012-02-15
forum: Server Platforms
---

### Post by jeliocranch on 2012-02-15
I've built a server to host several Virtual Machines and share files among them (and others on the network).

Most of the VM's are gui based, and I'd like to log into them directly from the login screen.  I've got *xdm* installed, along with *openbox* to give me a WM for a browser.

Eventually I'll have at least one thin-client logging in as well, and thought I could use the same techniques to accomplish this task, but I'm not familiar enough.

Any advice or guides anyone knows about?
Thanks,

---

### Post by josephmills on 2012-02-15
you want to use VNC ? [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
for remote support ? there is clients like [http://remmina.sourceforge.net/screenshots.shtml](http://remmina.sourceforge.net/screenshots.shtml)
for that 
as far as the thin client not sure. have a good one

---

### Post by jeliocranch on 2012-02-15
> **josephmills said:**
> you want to use VNC ? [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
for remote support ? there is clients like [http://remmina.sourceforge.net/screenshots.shtml](http://remmina.sourceforge.net/screenshots.shtml)
for that 
as far as the thin client not sure. have a good one

I thought about vnc: I would think I'd have to have the user account in the host server, then write "startup-scripts" per se to vnc into the guest.  Is that the way?

can I vnc from a client w/o a desktop (the host) to a server (the guest os with a gui)?

---

