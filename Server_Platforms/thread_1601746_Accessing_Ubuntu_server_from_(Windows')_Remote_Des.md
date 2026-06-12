---
title: "Accessing Ubuntu server from (Windows') Remote Desktop Connection"
date: 2010-10-20
forum: Server Platforms
---

### Post by Apolyonn on 2010-10-20
Set up Ubuntu server with openSSH, and I can access it in Linux with Remote Desktop Viewer and Windows with PuTTY.  Just wondering if I can also access it with the default Windows program, Remote Desktop Connection.  It'd be beneficial for when I'm at work.

Thanks

---

### Post by cariboo on 2010-10-20
You need one of the free vnc version in order for windows to view the Ubuntu desktop. Give xvn4viewer and vnc4server a try, they are in the repositories.

---

### Post by CharlesA on 2010-10-20
If you have a GUI on the server machine, and enabled "Remote Desktop" any VNC client will work. I use UltraVNC and TightVNC.

---

### Post by Apolyonn on 2010-10-20
I'm not having trouble accessing the server; I want to know if I can use the default Windows Remote Desktop Connection program (it's in accessories) to access my Ubuntu server.  Also, the server distros are all console-based, so no GUI here.

I would accept a simple 'no' if there's no answer.

---

### Post by CharlesA on 2010-10-20
That would be a no then.

You'd have to use Putty or a similar SSH client.

---

### Post by Apolyonn on 2010-10-20
That kind of sucks :\  PuTTY works great and all, but I can't install programs on my work PC.  Oh well, thanks for the info :D

---

### Post by CharlesA on 2010-10-20
> **Apolyonn said:**
> That kind of sucks :\  PuTTY works great and all, but I can't install programs on my work PC.  Oh well, thanks for the info :D

You can run portable putty, which doesn't install anything on the host machine.

I run it off a USB key.

[http://portableapps.com/apps/internet/putty_portable](http://portableapps.com/apps/internet/putty_portable)

---

