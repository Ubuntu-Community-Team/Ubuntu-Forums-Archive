---
title: "Remote Desktop For Linux?"
date: 2009-03-17
forum: The Cafe
---

### Post by kevin11951 on 2009-03-17
How hard would it be to setup a free service for Linux user, that is like "logmein"?

Something web based, and uses vnc for its protocol... it has to be secure, some what fast, and support getting to your files...  Maybe tunneling vnc though ssh?

What kind of server would you need for that?

I want to learn to program, so this may be a good start...  Do you think anyone would use it?  Would anyone help me with this either?  :)

-Kevin

---

### Post by smartboyathome on 2009-03-17
[RealVNC]("http://www.realvnc.com/index.html") already does what you want. I would personally go with Free/NX, though, as it is way faster (vnc is very clunky).

---

### Post by kevin11951 on 2009-03-17
> **smartboyathome said:**
> [RealVNC]("http://www.realvnc.com/index.html") already does what you want. I would personally go with Free/NX, though, as it is way faster (vnc is very clunky).

it dosent look web based... or am i missing something?  i was thinking something identical to "logmein" but for linux.

---

### Post by smartboyathome on 2009-03-17
> **kevin11951 said:**
> it dosent look web based... or am i missing something?  i was thinking something identical to "logmein" but for linux.

See [here]("http://www.realvnc.com/support/javavncviewer.html#1"). It tells you about it's web viewer.

---

### Post by JackieChan on 2009-03-18
How do I remote connect with my friends who use Windows?

---

### Post by smartboyathome on 2009-03-18
> **JackieChan said:**
> How do I remote connect with my friends who use Windows?

Are you trying to connect to Windows, or from Windows?

---

### Post by JackieChan on 2009-03-18
> **smartboyathome said:**
> Are you trying to connect to Windows, or from Windows?
I'm using Ubuntu, and I want to connect to my friend's Windows computer.

---

### Post by forcefullpower on 2009-03-27
I have been looking for something similar to logmein too.

I have tried NTRconnect which installed but when doing the remote session it would not display the screen but still did all the mouse keyboard movements onscreen the remote screen.

I have no interest in VNC or any of those. I need something that tunnels out through routers without configuring port forwarding.

---

### Post by Mehall on 2009-03-27
logmein are workig on Linux support.

---

### Post by Mooose? on 2009-03-27
Ubuntu does have a Remote Desktop viewer, and with the correct port settings there is no reason why you can't use it across the net to connect to a Windows machine from Linux, but I do not think it can act as server.

I'd advise against VNC as the performance is pretty horrible if you can use RDP instead.

Also, MS have disabled the ability to connect to a Vista machine with RDP unless it's running Pro or Ultimate.  I spent ages trying to find where they had hidden it on a machine I was admining.  It got XP'd shortly after.

For remote access to Linux (aside from the obvious ssh) you can use X remotely I think, but I know absolutely nothing about it so ymmv.

---

### Post by sideaway on 2009-04-01
Just to bump a thread. I'm wanting to remote desktop from my Vista machine to my Ubuntu machine. I've tried VNC, and the expereince was painfully slow (this is over a local network too!) Is there a way I can use Windows RDC from windows to connect to my Ubuntu box?

---

### Post by JackieChan on 2009-04-01
> **smartboyathome said:**
> [RealVNC]("http://www.realvnc.com/index.html") already does what you want. I would personally go with Free/NX, though, as it is way faster (vnc is very clunky).
Cool, thanks!

---

### Post by toupeiro on 2009-04-01
[xRDP]("http://xrdp.sourceforge.net/") FTW!

---

