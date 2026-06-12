---
title: "SSH and Server applications"
date: 2011-02-25
forum: Server Platforms
---

### Post by Cloud Wolf on 2011-02-25
Hey,

I recently install ubuntu server 10.10 on an old pentium 4 PC to run as a minecraft server for my friends and I. The setup of the minecraft server went without hitch, however I have come across a problem.

I am using SSH to log into my server using my laptop on the same network. But once I start the server application through the SSH session, I can not log out of the SSH session without logging out of the machine and closing the minecraft server.

Is there any way of being able to run the application remotely, leave it to run and "check up" on it occasionally - all remotely?

Cheers. Tell me if I am not explaining myself correctly.

---

### Post by koenn on 2011-02-25
if minecraft can run as a service or a daemon, you should start it from a startup script, so it isn't attached to your session and runs on its own.

if you have to start it interactively, run screen first, the start minecraft. Screen will let you detach en reattach, and wil serve as a controlling terminal to minecraft so it'll keep running.
so that's ssh -> screen -> minecraft

---

