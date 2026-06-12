---
title: "VNC Server issue"
date: 2008-09-20
forum: Server Platforms
---

### Post by GuiGuy on 2008-09-20
Hi,
I have set up a box as a simple file server, using xubuntu. I want to operate the box remotely and not have a monitor or other peripherals connected.

I am using x11vnc as a VNC server, which is loaded when the PC boots up. 


After a reboot I can remotely log in ok. 

However, after I log out any subsequent attempt to log in results in a "host not found" error, although the file server itself is working OK. 

Can I get some help or hints on troubleshooting the issue? Or perhaps there is a better way to remotely access the PC?

Thanks

---

### Post by krunge on 2008-09-21
> **GuiGuy said:**
> Hi,
However, after I log out any subsequent attempt to log in results in a "host not found" error, although the file server itself is working OK. 


Could you give more details about this error message?  Where do you see it?  Which app is telling it to you? (and on which machine).

---

### Post by GuiGuy on 2008-09-21
> **krunge said:**
> Could you give more details about this error message?  Where do you see it?  Which app is telling it to you? (and on which machine).

On the client when I try a subsequent remote login.

ADDED: Just tried xtightvncviewer: 
> 
xtightvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
 

So this message is different to the other client I was using. 

For trouble shooting I have left the server connected to peripherals. As best as I can work out x11vnc continues to run after the first remote session logs out.

Thanks

---

### Post by quinnten83 on 2008-11-07
I've had this issue ever since Xubuntu 7.10.
I don't know what causes it either.
I have it again with Xubuntu 8.10.

---

### Post by GuiGuy on 2008-11-07
> **quinnten83 said:**
> I've had this issue ever since Xubuntu 7.10.
I don't know what causes it either.
I have it again with Xubuntu 8.10.

Hi,
I gave up on this on the basis that it is just another idiosyncratic linux feature put in there to frustrate us. There is a dev somewhere quietly chuckling to himself about our collective plight.

Anyway, I finished up using mythbuntu as my server OS. Why? Because it is configured to work, including remote access. It hasn't missed a beat. The desktop is xfce, btw.

---

### Post by eppo on 2008-11-07
I dont think you are supposed to "log out" of a vnc session.
i use tightvnc, when i am done i click on the red X.

---

