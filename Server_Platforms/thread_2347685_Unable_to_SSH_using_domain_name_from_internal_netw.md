---
title: "Unable to SSH using domain name from internal network"
date: 2016-12-27
forum: Server Platforms
---

### Post by zfreak7c5 on 2016-12-27
Hello,

I have a Ubuntu Server system setup to allow SSH login with SSH keys.  The setup works fine when I login remotely and use my domain name that forwards a port, say 2222, to port 22 on the internal system.  I can also login from an internal connection using the internal IP just fine.  I would like to be able to login using the domain name from any location so I don't have to change saved sessions and scripts all the time, but when I try to use the domain name to connect from inside the network I get the following error.

```

debug1: identity file /Users/user/.ssh/id_edxxxxx-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.3
ssh_exchange_identification: read: Operation timed out
```

Looking at the auth.log on the server shows this.

```
Did not receive identification string from "my public IP"
```

I suspect it has something to do with how my router is routing the request back to the internal network, but not completely sure.

---

### Post by howefield on 2016-12-27
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by untrustytahr on 2016-12-27
I think you are correct.  You either need to use a router that supports hairpinning (aka NAT Loopback) or you need to setup a "split-brain" DNS.  Others here are far more versed than I to explain it.  They will probably chime in.

---

