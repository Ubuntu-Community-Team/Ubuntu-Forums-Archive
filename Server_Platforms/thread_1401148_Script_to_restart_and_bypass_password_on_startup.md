---
title: "Script to restart and bypass password on startup"
date: 2010-02-07
forum: Server Platforms
---

### Post by fiveironfrnzy08 on 2010-02-07
Hello,

I'm running Ubuntu 9.10 as a web/ftp/etc server. I like to work on stuff from remote locations and have set it up to be accessed it with the external IP address by my laptop. 

The problem is that if I'm at a remote location and tell it to restart, when it boots up it won't log me on unless I enter the password, but I can't remote access it until I'm logged in.

So, is there a command or script that I can run that will tell it to restart and bypass entering a login password?

I'm only looking for something to bypass it ONCE per command/script, NOT to disable my password.

Thank you in advance!

---

### Post by joberly on 2010-02-07
Does the server have its interface up and ready before login? (ping it).

If yes, you just need access to specific services that aren't starting? Which services?

If no, start with fixing the first problem of fixing connectivity before login.

---

### Post by fiveironfrnzy08 on 2010-02-08
Thank you for your reply!

I can ping it just fine before it's logged in, the website it's hosting works as well before it's logged in.

I'm not really positive which services I need. I use VNC Viewer from my laptop to view it, and I use Ubuntu's built in Remote Desktop on the server side.

Any suggestions from there?

---

### Post by BobVila on 2010-02-08
You'll probably be better off just installing openssh server on the box so that you can ssh in. That won't require you to log in before remotely connecting, but will be waaaaaaaay more secure than attempting to bypass the initial login prompt.

---

### Post by fiveironfrnzy08 on 2010-02-08
Sweet, that works pretty well.
I was able to use Putty and access through ssh...

Now I didn't really specify before, but I'm actually using 9.10 Desktop edition running all my servers. From the openssh, is there a way that I can log in (to the desktop, not just the server, I already did that) remotely through openssh so that I can use VNC viewer to work with the GUI?

In other words, when the computer restarts, I'm able to login using open ssh and use the command line. From there, using ssh, is there a way to get the desktop actually logged on so that I can switch over from ssh, to a VNC Viewer?

---

### Post by joberly on 2010-02-08
You can allow X forwarding if you want to run specific apps, using the -X command when you connect to the server. eg, ssh -X user@host.

Then run the program you want from the command line. (make sure your sshd_config allows Xforwarding!)

You can also tunnel VNC over SSH to get a full blown desktop, by configuring your vnc server of choice (tightvnc, NX, ?) to only allow connections from the localhost.

To be extra safe, you can run tightvnc after you login to the host, and not have it run in daemon mode all the time.

There are many guides out there, google VNC over SSH or something of the like.

---

