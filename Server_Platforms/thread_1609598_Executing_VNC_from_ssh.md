---
title: "Executing VNC from ssh"
date: 2010-10-30
forum: Server Platforms
---

### Post by jcab on 2010-10-30
Hi everyone!

I successfully logged in to my computer through ssh, but I want to know if there is a way to execute krfb or any other VNC server while I am currently logged in to my computer from ssh. 

If it is not possible, then what is the best way to VNC through ssh?

---

### Post by issih on 2010-10-30
Its certainly achievable, although I admit I'm not sure how you would achieve it using vinagre (which is ubuntu's default vnc software)

Personally I have only done this using vncserver or tightvnc:

The basic procedure is as follows:

1) ssh into the machine
2) run vncserver to create a new server instance, e.g.
```
vncserver -depth 24 -geometry 1280x800
```
N.B. the exact command needed will depend on what vnc server software you are using.
3) note the output of starting that server to decipher what port the system will be available on, note that if it tells you it is starting desktop 5 or something similar it will be on port 5900 + the number reported, so 5905 in this case.
4) exit the ssh session and log back in tunnelling the apporpriate port (e.g. 5905) back to your current machine using ssh:
```
ssh -L 5900:localhost:5905 me@remotemachine
```
N.B the -L and the bits tunnel port 5905 on the remote machine to port 5900 on your local machine.
5) connect a vnc client to localhost port 5900 and voila

Hope that makes sense

---

### Post by CharlesA on 2010-10-30
You'd need to be physically logged in to the console for vino (the default VNC software in Ubuntu) to launch.

I've used TightVNC before, but if you want a secure way to access the machine, check out [FreeNX.]("http://www.nomachine.com/select-package.php?os=linux&id=1")

EDIT: I know Vino is in Gnome, but I don't know if there is a VNC server built into KDE.

---

### Post by issih on 2010-10-30
Good spot on the Kubuntu bit, I often forget to look up in the top left corner *bad issih*

---

### Post by CharlesA on 2010-10-30
I didn't notice it until after I posted.

FreeNX works with Gnome and KDE. :)

---

### Post by jcab on 2010-10-30
issih, thanks a lot for your response!

I followed your steps, but in the end of it all, it doesn't work. TightVNC connects, but then it closes all of a sudden, and I never see my remote desktop either.

I think it has to do with TightVNC Sever's configurations, I'm not sure. Any ideas?

---

### Post by HermanAB on 2010-10-30
Howdy,

Since you already have SSH working, why bother with VNC?

$ ssh -X -C -c blowfish user@server gnome-panel

Now you can go click happy on the remote machine.

The above works from Windows too - install Cygwin.

---

### Post by hantechbl on 2010-10-31
Did u watch one of the recent episodes of Hak5, they discussed getting gui apps over ssh, cross platform too.

---

### Post by vikjon0 on 2010-10-31
I also vote for NX server. I gave vnc a try but it is a lot of work to get automatic multiple background sessionss to work. (which is what I need and expect)

---

### Post by issih on 2010-10-31
Not really sure what to suggest, that basic procedure is something I have used countless times.

Most likely is that the ssh tunnel isn't working correctly, look into that bit,

Hope that helps

---

