---
title: "OpenSSH server Connects to Remote VNC"
date: 2008-02-06
forum: Server Platforms
---

### Post by zzzBrett on 2008-02-06
Here is the situation:

Computer A: Runs OpenSSH Server
Computer B: Runs VNC Server

This is what I want to do:
Computer B connects to computer A's SSH server. Computer A connects to Computer B's VNC server, and controls computer.

How would I go about setting this up?  Computer B is running windows, putty to connect, but my main question what should I put as my "source" and what as my "destination" on the client side?

Or, is there a way to just open up all ports to the remote user while connected via SSH?


Thanks,
Brett

---

### Post by HermanAB on 2008-02-07
Well, if you have SSH, then VNC is redundant, since everything you can do with VNC, you can do with SSH and SSH is secure too.

So, I always tell people to read the snail book and forget about VNC.

Cheers,

Herman

---

### Post by faulkes on 2008-02-07
> **zzzBrett said:**
> Here is the situation:

Computer A: Runs OpenSSH Server
Computer B: Runs VNC Server

This is what I want to do:
Computer B connects to computer A's SSH server. Computer A connects to Computer B's VNC server, and controls computer.


ok.

> 
How would I go about setting this up?  Computer B is running windows, putty to connect, but my main question what should I put as my "source" and what as my "destination" on the client side?


If I recall correctly, you basicly want to forward a remote port.

With putty, you will have to go into the config options and set this up (I don't have putty in front of me or near me so I cant offer more help there).  The format though is usually (based upon the ssh -L & -R cli args).

```

localport:host:remoteport

```

> 
Or, is there a way to just open up all ports to the remote user while connected via SSH?


the unix / linux ssh client does support dynamic port forwarding of unprivileged  ports (the -D argument), I'm unsure how or if putty supports this.

faulkes

---

### Post by zzzBrett on 2008-02-07
> **HermanAB said:**
> Well, if you have SSH, then VNC is redundant, since everything you can do with VNC, you can do with SSH and SSH is secure too.

So, I always tell people to read the snail book and forget about VNC.

Cheers,

Herman

I need remote access to a windows computer behind a firewall. I was hoping to use SSH to bypass the firewall.

---

### Post by zzzBrett on 2008-02-07
> **faulkes said:**
> ok.



If I recall correctly, you basicly want to forward a remote port.

With putty, you will have to go into the config options and set this up (I don't have putty in front of me or near me so I cant offer more help there).  The format though is usually (based upon the ssh -L & -R cli args).

```

localport:host:remoteport

```



the unix / linux ssh client does support dynamic port forwarding of unprivileged  ports (the -D argument), I'm unsure how or if putty supports this.

faulkes

Thanks, I will try this!

Brett

---

