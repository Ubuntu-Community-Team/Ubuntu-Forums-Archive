---
title: "Unexplained port listening"
date: 2007-02-06
forum: Server Platforms
---

### Post by jtc on 2007-02-06
I'm a system administrator for a small computer lab at my university.

Just noticed a port listening I can't explain. I'm sure it has a natural explanation, but since I can't find one, it makes me a bit nervous.

Below is the result of netstat -tlp. The port I'm wondering about is the one marked bold.

```

**tcp        0      0 *:36098                   *:*                     LISTEN     -**
tcp            0      0 localhost:54700         *:*                     LISTEN     3878/hpiod
tcp            0      0 *:kerberos-adm        *:*                     LISTEN     4383/rpc.statd
tcp            0      0 *:sunrpc                   *:*                     LISTEN     3371/portmap
tcp            0      0 localhost:41362         *:*                     LISTEN     3881/python
tcp            0      0 localhost:ipp              *:*                     LISTEN     3943/cupsd
tcp6          0      0 *:ssh                         *:*                     LISTEN     4327/sshd

```

If you restart the computer the portnumber in question changes, but it is still a high portnumber which isn't associated with any pid/program. When I continued to look I noticed the same behaviour on all the ubuntu-computer.

Taking the ubuntu-machines down to runlevel one stops all the port-listenings, except the one I'm worried about.

Trying to connect/telnet to the port from another computer establishes a connection, but with no more response.

It is a mixture of (k)ubuntu 6.06 and 6.10.

Anyone who can shed some light on this behavior?

---

### Post by MJN on 2007-02-06
When you say it's not associated with any pid/program, have you tried **sudo lsof -i :36098 **?
 
Mathew

---

### Post by jtc on 2007-02-06
Lsof don't show anything.

Anyhow, now I've talked to one of the older and wiser systemadministrators here and the university and gotten my explanation. It is nlockmgr, running as a kernel module. Didn't think to look for it, since these computers are only nfs-clients and not servers.

---

