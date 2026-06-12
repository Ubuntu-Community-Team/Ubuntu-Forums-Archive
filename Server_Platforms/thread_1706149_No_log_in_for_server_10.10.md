---
title: "No log in for server 10.10"
date: 2011-03-13
forum: Server Platforms
---

### Post by Robert the Kat on 2011-03-13
I have Ubuntu server 10.10 on an old desktop.  When you start the computer up, the server requires a log in.  Well, this is not so good if you set up a server correctly.  They should not have a monitor or a keyboard.  Set up that way, if there is a power outage, you have to hook up both to get the server running again.
  Is there a way to set up 10.10 server so that it does not require any input(log in) at start up?    This would be the same way my Windows  Home Server operates.
 
RK

---

### Post by SeijiSensei on 2011-03-13
> **Robert the Kat said:**
> I have Ubuntu server 10.10 on an old desktop.  When you start the computer up, the server requires a log in.

All the server processes have already started by the time you get a login prompt. They're started at boot via the startup scripts in /etc/init.d.  Reboot the server, don't log in, then go to another machine on the network and run "nmap 10.10.10.10" replacing 10.10.10.10 with the IP address of your server.  That will show which services are listening on which ports.

You only need to log in if you want to run commands from the shell.  It's no different than logging in over the network via SSH.

---

### Post by Robert the Kat on 2011-03-13
> **SeijiSensei said:**
>  
You only need to log in if you want to run commands from the shell. It's no different than logging in over the network via SSH.
 
I see.  Very interesting.  Server works fine from the internet without having to "log in" at the server after start up.
Thanks.
:)
RK
 
P.S.  Hope you have enjoyed all the bad storms this winter in Boston.
:(

---

### Post by jerome1232 on 2011-03-13
I just wanted to add that a server shouldn't be left unattended and logged in to. The screen should always be locked if you are not actively using it.

---

