---
title: "SSH Port Forwarding"
date: 2010-12-11
forum: Security
---

### Post by sefs on 2010-12-11
Consider the scenario.

1/
HomePC -> Router -> Internet -> Router -> [OpenSSH][WorkPC_1][WorkPC_2][WorkPC_X]

2/
the friendly internal name of [WorkPC_2] is wkpc2.myworkplace.lan
the external name for the [OpenSSH] is myopenssh.com
[OpenSSH] is a Linux machine
[WorkPC_2] is a windows machine

3/ 
I fire up putty on HomePC and connect to myopenssh.com with port forwarding set up as  source port=5555, Destination=wkpc2.myworkplace.lan:5555

then i fire up vncviewer and connect to  localhost:5555 

all vncviewer between HomePC and OpenSSH is encrypted in the SSH Tunnel, but what about between OpenSSH and WorkPC_2?

Is that encrypted or in the clear?

If it is in the clear then is the only way to solve this problem is to install an ssh server directly on the WorkPC_2?

Thanks.

---

### Post by HermanAB on 2010-12-11
Yes.

However, if you have SSH working, why bother with VNC at all?

$ ssh -X -C -c blowfish user@server gnome-panel
and go click happy.

---

### Post by sefs on 2010-12-11
> **HermanAB said:**
> Yes.
When you say yes.  What do you mean exactly. Yes its encrypted, or yes its in the clear between OpenSSH and WorkPC_2.

> **HermanAB said:**
> 
However, if you have SSH working, why bother with VNC at all?

$ ssh -X -C -c blowfish user@server gnome-panel
and go click happy.

When you say have ssh working... do you mean on the WorkPC_2 machine?

I tried the command above and got this error...
I should have said WorkPC_2 is a windows 7 machine.

```

$ ssh -p xxxx -i rsa_key -X -C -c blowfish myuser@remotehost gnome-panel
sh: /usr/X11R6/bin/xauth: not found
sh: gnome-panel: not found

```

---

### Post by SeijiSensei on 2010-12-11
> **sefs said:**
> When you say yes.  What do you mean exactly. Yes its encrypted, or yes its in the clear between OpenSSH and WorkPC_2.

Unless you have some form of encryption between the OpenSSH host and WorkPC_2, it's in the clear.  To have end-to-end encryption would require running an SSH server on WorkPC_2 as Herman suggests.  I would imagine you can find an SSH server to run in Windows, but I can't help with that.

What about commercial solutions like GoToMyPC?  I think that's encrypted from end to end.

---

### Post by bodhi.zazen on 2010-12-11
cygwin provides an openssh server on Windows.

---

### Post by sefs on 2010-12-11
If I put an ssh server on the windows machine it means I would have to give it a static ip.  I could use copssh for windows. 

I was really just trying to be sure that that "last mile" was indeed unencrypted before I utilized RDP to take care of encryption in that segment, without the cost of another ssh server & static IP in the mix.  

The reason i was playing with the vnc is that it feels much faster than RDP.

Thank you for clearing that up.

The X11 forwarding over ssh that was pointed out above by Herman is amazing. Never knew  you could do it like that. Thank you for that.

---

### Post by HermanAB on 2010-12-11
Howdy,

The work PC is a Windows machine running Remote Desktop?

Connect to it with rdesktop from Linux.  The Windows remote desktop protocol is secure - it uses RC4.  You don't need to run it over SSH.

If you want UNIX tools on Windows (X, OpenSSH...), install Cygwin.

---

