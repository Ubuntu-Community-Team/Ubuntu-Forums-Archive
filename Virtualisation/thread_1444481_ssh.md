---
title: "ssh"
date: 2010-04-01
forum: Virtualisation
---

### Post by Nick188 on 2010-04-01
Hi,
 how can I use ssh in order to send commands to a virtual machine?

Regards

Nick-

---

### Post by n0dix on 2010-04-01
I don't know if this is possible. You can connect remotely via ssh and then execute the commands.

```
$ ssh <username>@<machine_to_connect>
```

---

### Post by rliegh on 2010-04-02
The same way you'd use ssh to connect any other machine. 

The only difference I can think of is that when I do that, I  use bridged networking instead of NAT (because my connection hangs when i try to connect to a NAT machine).

I always use ssh <login>@<ip number> to connect to my virtual machines, and then do whatever and log out.

---

### Post by benderisgreat on 2010-04-02
the guest has to be running an ssh daemon.

if the guest is ubuntu this single command run on the guest should do the trick:
```
sudo apt-get install openssh-server
```

---

