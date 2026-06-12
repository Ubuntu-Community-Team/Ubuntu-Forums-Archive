---
title: "open  matlab gui that is running on remote server(centos) on my local machine( linux"
date: 2014-07-15
forum: Server Platforms
---

### Post by ajticlo on 2014-07-15
Hi there.
I am using a vpn connection and ssh -X to connect to a remote server on my place of work.
I have matlab running on the remote server, and I want to open that matlab window on my local machine.
If I just type matlab on a terminal that is connected via ssh -X to the remote server, it opens a new instance of matlab on my local machine, and that is not what I want.
How can I do that than? 
regards

---

### Post by TheFu on 2014-07-15
If MATLAB is already running on a different "display" then you cannot reconnect using X/Windows.  You need to use some other remote desktop method, like VNC or NX which have session resume capabilities - plus the programs you want to resume-session must have been started inside the remote desktop tool.

VNC is probably easier to use and since you have a VPN already, the lack of security in VNC won't be an issue.

---

