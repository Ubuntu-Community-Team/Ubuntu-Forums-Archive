---
title: "ssh Client Times out, Leaves session active on Host."
date: 2009-08-13
forum: Server Platforms
---

### Post by VipX1 on 2009-08-13
Ubuntu 9.04 Server Edition with Gnome installed (host) 10MB Download 1MB Upload DSL
Ubuntu 9.04 64bit (Client) 20MB Download 2MB Upload DSL

If I leave my ssh client session idle for 20 minutes plus it times out. I have the flashing cursor but that's all it does, flash. I can't move it in any way.
When I reconnect to the host via ssh again and type users I have a new entry for each time the session has time out on me. The old ssh session is still active on the host.
```
vipx1@vipx1-svr:~$ users
vipx1 vipx1 vipx1

```
ssh config file from the host:
```

Host 192.168.1.33
Port 47000
PasswordAuthentication no
ForwardX11Trusted yes
CheckHostIP yes
Protocol 2
ConnectTimeout 0
```

---

