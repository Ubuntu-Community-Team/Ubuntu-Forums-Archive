---
title: "Virt-manager tries to connect to ip6, then ip4 and THEN socket"
date: 2015-06-19
forum: Virtualisation
---

### Post by smeerbartje on 2015-06-19
When I try to run virt-manager, it first tries to connect to KVM through ip6. When this times out, it tries to connect through ip4. Until this times-out, it will try to connect to the socket and the startup continues. My question is: how can I force virt-manager to first try to connect to the socket?

---

### Post by TheFu on 2015-06-19
A socket connection **Is** a network connection. Did you want a local connection, non-network?

Also, the connection type to the VM host can be local or remote - do you have the remote connection checkbox selected?

As a last resort - what about disabling ipv6?  I'm not ready for ipv6, so we disable it on all the machine here.

---

### Post by smeerbartje on 2015-06-22
Thank you for your suggestions; KVM is running on localhost and virt-manager should connect to localhost. How do I force this? What checkbox are you talking about? Also keep in mind that eventually virt-manager appears. When I start it with this: "strace -ff virt-manager --debug", it waits for a couple of minutes on this line:

```
connect(4, {sa_family=AF_INET6, sin6_port=htons(6010), inet_pton(AF_INET6, "::1", &sin6_addr), sin6_flowinfo=0, sin6_scope_id=0}, 28
```

After a couple of minutes the process waits again, now for this:

```
[pid 32599] connect(3, {sa_family=AF_INET6, sin6_port=htons(6010), inet_pton(AF_INET6, "::1", &sin6_addr), sin6_flowinfo=0, sin6_scope_id=0}, 28
```

This also takes a couple of minutes. Then it waits for this:

```
socket(PF_INET6, SOCK_STREAM|SOCK_CLOEXEC, IPPROTO_TCP) = 3
[pid 32620] setsockopt(3, SOL_TCP, TCP_NODELAY, [1], 4) = 0
[pid 32620] setsockopt(3, SOL_SOCKET, SO_KEEPALIVE, [1], 4) = 0
[pid 32620] connect(3, {sa_family=AF_INET6, sin6_port=htons(6010), inet_pton(AF_INET6, "::1", &sin6_addr), sin6_flowinfo=0, sin6_scope_id=0}, 28 <unfinished ...>
[pid 32618] <... poll resumed> )        = 0 (Timeout)
[pid 32618] read(5, 0x7ffcb68b23f0, 16) = -1 EAGAIN (Resource temporarily unavailable)
[pid 32618] poll([?] 0x165f610, 3, 59970
```

This also takes a minute or so, before virt-manager appears and everything works fine.

---

