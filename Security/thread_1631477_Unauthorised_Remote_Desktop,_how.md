---
title: "Unauthorised Remote Desktop, how?"
date: 2010-11-26
forum: Security
---

### Post by pbryd on 2010-11-26
I just had a window pop up on my desktop saying my pc was being remotely controlled. Ubuntu 10.10

The pc shutdown by itself, and I disconnected it from the net.

I rebooted and uninstalled the remote desktop app.

How did this happen?

Are there any logs I can look at to find out where the remote user was?

p

---

### Post by lovinglinux on 2010-11-26
Remote desktop is one of the most insecure applications in your Ubuntu installation. I don't know why the Ubuntu developers include it by default.

If you really need to use it, then set it up with a ssh tunnel. 

I would advice to re-install Ubuntu. You can't be sure about what the attacker did on your system.

---

### Post by matt_symes on 2010-11-26
Hi

> If you really need to use it, then set it up with a ssh tunnel. +1 lovinglinux. Or use No machine

[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

Kind regards.

---

### Post by CharlesA on 2010-11-27
> **lovinglinux said:**
> Remote desktop is one of the most insecure applications in your Ubuntu installation. I don't know why the Ubuntu developers include it by default.

It isn't enabled by default, though. You'd have to enable it for it to be a problem.

I just wish that if it was enabled, that it would not accept a blank password/no password, or at least warn that there is no password set.

---

### Post by HermanAB on 2010-11-27
Congratulations.  You are the umpteenth Ubuntu user that has been burned by VNC.  You really need to re-install if you want to be sure that the system is secure again.  

If you need remote access, use SSH.  It can do everything VNC does and more, securely.

---

### Post by movieman on 2010-11-27
> **HermanAB said:**
> If you need remote access, use SSH.  It can do everything VNC does and more, securely.

X-forwarding over ssh is a pain when you're on a high latency link: in that case you really need to use something like vnc or xpra.

But if you do use vnc, it should always be configured to only listen to locahost and to use ssh to forward to a remote address.

---

### Post by HermanAB on 2010-11-28
If you have a slow link, improve ssh speed with:
-C -c blowfish

---

### Post by pbryd on 2010-11-28
Thanks for your help guys.

I had enabled remote desktop earlier and forgot about it tbh.

I'll go ahead a complete fresh install and remove remote desktop altogether straight away.

Cheers

Phil

---

