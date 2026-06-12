---
title: "[SOLVED] VNC not working"
date: 2008-08-20
forum: Server Platforms
---

### Post by Jamina1 on 2008-08-20
Hi guys.

I recently turned an old windows machine into a LAMP box using Ubuntu Server 8.04.

Both computers are on the same local LAN and I can access the webpage on the server just fine from my main computer.

Problem is I don't have a monitor to dedicate to this server all the time so I was hoping to get VNC up and running so I could remotely connect to it. So I installed ubuntu-desktop on my server so I'd have an X environment.

Problem is, I've installed tightvncserver (apt-get install tightvncserver) and I've installed the viewer on my Windows XP box and I cannot connect to the Linux box. Started the vnc server (vncserver) and set a password.

I've tried via hostname, IP address, nothing. I even tried installing RealVNC viewer on my XP box to see if it was maybe a glitch with the software, but no go.

What am I doing wrong?

---

### Post by Ximbiot on 2008-08-20
Do you have a firewall running on the server?  A firewall could be letting port 80 through and not others (the output of `sudo iptables -L' should answer this question).

Also, I have had an issue before where the default listen port for my VNC server was different than the default port my VNC client wanted to connect to.  If both client and server are TightVNC this seems unlikely, but you might as well check.

Have you looked at the logs on the server?  I'm not sure where TightVNC logs to, but it might log failed connection attempts in /var/log/syslog, /var/log/auth, or the like.

Finally, what is the exact error message your client is giving you?

---

### Post by timcredible on 2008-08-20
try xdm instead of vnc.  xdm is on all linux and unix  machines by default, click on my signature link for a how to

---

### Post by Jamina1 on 2008-08-20
Ok, well the desktop environment is bogging my computer down considerably.

Is there a way to get a VNC server working from an Ubuntu Server install?

I installed xorg, started the vncserver, but I still cannot connect.

I know in the desktop version you can "turn on" remote connections in a menu -- how do you do that in the server version?

---

