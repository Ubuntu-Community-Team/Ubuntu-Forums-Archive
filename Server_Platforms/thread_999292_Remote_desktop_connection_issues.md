---
title: "Remote desktop connection issues"
date: 2008-12-01
forum: Server Platforms
---

### Post by quikone8 on 2008-12-01
I have been trying to connect my Ubuntu 8.10 laptop to my Ubuntu 8.10 server.  I can connect via terminal and ssh or through putty and through sftp.  My problem is I cannot figure out how to get remote desktop to work.  Any suggestions would be appreciated.

---

### Post by hictio on 2008-12-01
You are going from the lappie to the server? Is that so?
The (default install of a) server has no GUI at all.

---

### Post by quikone8 on 2008-12-01
That's true, I have installed gnome.

---

### Post by doas777 on 2008-12-01
well, if you have ssh on the server try:
```

vncviewer -via user@server localhost:0

```

you may have to install vncviewer. i usually use tightvnc.

have fun

---

### Post by quikone8 on 2008-12-01
> **doas777 said:**
> well, if you have ssh on the server try:
```

vncviewer -via user@server localhost:0

```

you may have to install vncviewer. i usually use tightvnc.

have fun

How would I specify a port?

---

### Post by doas777 on 2008-12-02
well, if your using an alternative port for ssh it would follow the ```
user@server:prt
```

if the VNC server is on an alternative port, use ```
localhost:prt
``` for the last parameter. 

```
localhost:0 
``` is the default for the built-in remote desktop tools in gnome. you can confirm the value by opening up system-> administration -> remote desktop, and look at the link in the bottom center of the page.

---

### Post by HermanAB on 2008-12-02
Hmm, this comes up all the time.  VNC is almost always the wrong solution for use on Linux.  VNC is good for training - where the remote user needs to see what you are doing on his behalf.  For a headless server situation, it is best and far simpler and faster to use SSH:

$ ssh -C -c blowfish -X user@server gnome-panel

Cheers,

Herman

---

### Post by doas777 on 2008-12-02
your command just corrupted my local desktop. what pray tell, is it supposed to do? can't use my local desktop, or administer the server until i kill the connection.

---

### Post by quikone8 on 2008-12-03
> **doas777 said:**
> well, if your using an alternative port for ssh it would follow the ```
user@server:prt
```

if the VNC server is on an alternative port, use ```
localhost:prt
``` for the last parameter. 

```
localhost:0 
``` is the default for the built-in remote desktop tools in gnome. you can confirm the value by opening up system-> administration -> remote desktop, and look at the link in the bottom center of the page.

I have tried most of this, maybe I am just too much of a noob at this.  I can get in with vncviewer or ssh but no desktop.  There has got to be a way to get this accomplished.  I am getting through my router on 443 with either vnc or ssh or putty but once I get to that point the connection for remote desktop gets refused.  I have got to say that working with that crappy @@**?? with terminal services has been easier.  If someone has some further ideas, I don't want to give up.

Thanks

---

### Post by quikone8 on 2008-12-03
> **quikone8 said:**
> I have tried most of this, maybe I am just too much of a noob at this.  I can get in with vncviewer or ssh but no desktop.  There has got to be a way to get this accomplished.  I am getting through my router on 443 with either vnc or ssh or putty but once I get to that point the connection for remote desktop gets refused.  I have got to say that working with that crappy @@**?? with terminal services has been easier.  If someone has some further ideas, I don't want to give up.

Thanks

One interesting note;  I can go to Places/Connect to Server;  Connecting this way again is no problem.  Is there a way to get to a remote desktop from here?

---

### Post by tjandracom on 2008-12-03
i would rather use xrdp than vnc.

[http://xrdp.sourceforge.net](http://xrdp.sourceforge.net)

with xrdp, u can "RDP"ing your Linux like Windows Terminal Server, using other Linux client or even Windows client using the already included mstsc.exe. it could be used as a thinclient solution in Linux.

---

### Post by madverb on 2008-12-03
So all you want to do is use VNC ("Remote Desktop") to get to your servers GUI from you desktop?
VNC listens on port 5900 by default.
I don't understand what you mean by getting to it all through port 443

---

### Post by quikone8 on 2008-12-03
> **tjandracom said:**
> i would rather use xrdp than vnc.

[http://xrdp.sourceforge.net](http://xrdp.sourceforge.net)

with xrdp, u can "RDP"ing your Linux like Windows Terminal Server, using other Linux client or even Windows client using the already included mstsc.exe. it could be used as a thinclient solution in Linux.

Hi,  I have tried to install XRDP, but so far it installs but misses two pid file, the sesman.pid and the xrdp.pid.  The documentation is a bit vague.  Any ideas

---

### Post by tjandracom on 2008-12-05
the term "Remote Desktop" is different in Windows and Linux world.
in Linux "Remote Desktop" means viewing a GUI session already establish on server, that's what VNC does. in Windows world this is called "Remote Control", while "Remote Desktop" in Windows is starting a completely new GUI session (could be multiple session) running on server but controlled from workstation, kinda "XDMCP" does in Linux. but, XDMCP is not secure, and can only be connected from other Linux machine. there are other alternative of course, like NoMachine NX  [http://www.nomachine.com/](http://www.nomachine.com/) and Cygwin [http://www.cygwin.com/](http://www.cygwin.com/)

[QUOTE="quikone8"]Hi, I have tried to install XRDP, but so far it installs but misses two pid file, the sesman.pid and the xrdp.pid. The documentation is a bit vague.[/QUOTE]

yes you're right, the documentation is not complete. they didn't mention that we should connect using the X11rdp module and that we need X11rdp binary file, and this file is not included in the xrdp package. so the hardest part is to compile X11rdp binary from the source, because this is the only way to get the binary. the file is around 3.5MB and must be copied into usr/bin. if u are using Ubuntu Hardy 8.04 and i386 machine, i could mail to you the already compiled binary file.

this is how to compile:
[http://www.linuxquestions.org/questions/linux-server-73/xrdp-authenticates-but-does-not-load-x-server-rdp-592138/](http://www.linuxquestions.org/questions/linux-server-73/xrdp-authenticates-but-does-not-load-x-server-rdp-592138/)

---

