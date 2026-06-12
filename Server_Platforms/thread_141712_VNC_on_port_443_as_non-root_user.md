---
title: "VNC on port 443 as non-root user"
date: 2006-03-08
forum: Server Platforms
---

### Post by btdown on 2006-03-08
Unfortunately I can only run my VNC session on port 443 because of firewall issues. I can manually start the session (as root only) with:
vncserver -rfbport 443 -geometry 1280x1000 -depth 24
 
But because the port is 443 (or anything less than 1024, I think) it needs to be run as root else it wont have the perms to listen on that socket...so therefore it connects me to a VNC root session.
 
Is there a way to execute this command and use the VNC session of a non-root user? I'd like to get access to my "normal" desktop but it seems because of the port, it requires it to be run as root...
 
Any idea on how I might get around this?
 
Thanks,
BT

---

### Post by Glut on 2006-03-08
There's no way around it. On linux, root must own any process that requests a port < 1024. Run on a non-privaledged port and you're fine. Have you tried 8080?

---

### Post by btdown on 2006-03-08
I thought of that, but my router is on 8080. Now that Im thinking i might be able to change that to something else as once I was able to vnc in, I could just connect to the router from the inside.

---

