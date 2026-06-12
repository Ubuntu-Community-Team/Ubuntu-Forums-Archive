---
title: "VNC for thin client like"
date: 2012-02-20
forum: Server Platforms
---

### Post by roelforg on 2012-02-20
Right,
i just got myself a new home server.
I've been playing with this idea for a long time (however i calculated that my old server wasn't up to the job, my new one is).

I know you can build a thinclient system with ubuntu, but i want something different.
I'd like it if i could run a VNC server on the thing so me and my friend could be on school-pc's and use linux, he has an account on the thing.
I need a vnc-server-setup that allows multiple connections over 1 port and give each a new desktop.
But the extra-port option is limited to the amount of entry's in the config. I'd like it so it's gives each connection a new session.

Is this possible?
There aren't a lot of documents available about this.

---

### Post by volkswagner on 2012-02-20
Sorry not to answer you question, but VNC is not a joyful protocol.

I'd try to stay with SSH with X forwarding.  You can run any app in this manor, you just won't get a desktop environment.

```
ssh -X user@server
```

Then from inside the session you can launch any app.

---

### Post by roelforg on 2012-02-20
say i wanna access this from Winslow pc's
(from my school to be exact, only win pc's (with vnc installed))

I agree it's not ideal, but the pc's i wanna use don't have ssh or X-windows.
So it's a compromise.

I've been playing with the xvfb idea but it doesn't support picking a screen on it's own (nor does any vncserver i know support calling it)

---

### Post by roelforg on 2012-02-21
I'm really wondering where everyone is...

---

### Post by roelforg on 2012-02-21
I wonder....

ECHO!!!
echo...
echo..
ech..
ec.
e.

That's how quiet this thread is.

---

### Post by roelforg on 2012-02-21
bump

---

### Post by volkswagner on 2012-02-21
Excessive bumping is not polite.

Have you installed VNC yet?

I'm not aware of any limitation of one session per port.  I don't use VNC but I'm pretty sure you can run multiple clients over one port.  This should be true with one user or multiple users?

---

### Post by roelforg on 2012-02-21
> **volkswagner said:**
> Excessive bumping is not polite.

Have you installed VNC yet?

I'm not aware of any limitation of one session per port.  I don't use VNC but I'm pretty sure you can run multiple clients over one port.  This should be true with one user or multiple users?

Woops, i thought i deleted those... Sorry about that.

I do have vnc,
i know vnc-servers can accept multiple connections, so i thought they might be able to give each one a new session as well.

---

