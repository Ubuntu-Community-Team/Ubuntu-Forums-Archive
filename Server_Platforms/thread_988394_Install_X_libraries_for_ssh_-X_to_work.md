---
title: "Install X libraries for ssh -X to work"
date: 2008-11-20
forum: Server Platforms
---

### Post by nexist on 2008-11-20
I have Ubuntu Server 8.10. 

I would like to install the X libraries so that i can shell in with ssh -X and start up (e.g.) Firefox to configure CUPS.

I do not want to have the X-Window system start on boot, so I am pretty sure I do not need something like GDM. How do I install X/GTK2 without making it start by default?

---

### Post by lykwydchykyn on 2008-11-20
I'm not 100% sure on this, but I don't think you need X11 installed on the server to forward programs from the server.  The programs would connect to the local X server on your system, so they wouldn't need an X server running on the server computer's end.  

BTW, why not just hit the cups interface through your workstation's browser?  Or create an ssh tunnel?

---

### Post by nexist on 2008-11-20
I need X to install the app on the remote server.

When I tried to connect to the CUPS port with firefox running on my local machine, it refused. On a prior installation, I had to install links on the remote system and connect via that to the admin port.

What do you mean by create an ssh tunnel

---

### Post by lykwydchykyn on 2008-11-20
This explains it pretty well:
[http://www.engadget.com/2006/03/21/how-to-ssh-tunnels-for-secure-network-access/](http://www.engadget.com/2006/03/21/how-to-ssh-tunnels-for-secure-network-access/)

If you just need to install X, the command is:
```

sudo aptitude install xorg

```

---

