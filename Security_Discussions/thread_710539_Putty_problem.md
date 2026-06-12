---
title: "Putty problem"
date: 2008-02-28
forum: Security Discussions
---

### Post by brudinie on 2008-02-28
Putty will only go as far as authenticating on my ubuntu PC. It does not show me the prompt. It will report bad passwords though. It works fine on my windows PC which is on the same network. Is this something security related? I've even tried a win32 version of putty via wine and it gets stuck at the same place- eventually it reports 'Connection Timed Out'

---

### Post by bodhi.zazen on 2008-02-28
Hard to say. Could be any number of problems from firewall to incorrect putty / server settings, to sshd_config settings on the server.

Can you try ssh in a terminal ? use the -vv to show details :

```
ssh -vv user@server
```

---

### Post by brudinie on 2008-03-02
Thanks bodhi.zazen!

I'm going to do some reading up on using ssh from the command prompt. It got as for as:

debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

---

