---
title: "ubuntu server 8.04: BUG Message when starting"
date: 2008-04-25
forum: Server Platforms
---

### Post by Fuse314 on 2008-04-25
Yesterday I upgraded my trusted virtual ubuntu server (using Microsoft Virtual Server) from Ubuntu Server 7.10 to 8.04. The upgrade with do-release-upgrade went seemingly ok, but after the restart it hung with the following message (after "Loading GRUB...":

```
BUG: Int 6: CR2 00000000
     EDI 00000080  ESI 00000000  EBP 00001000  ESP c0437f4c
     EBX c04f9440  EDX 00000006  ECX 00000000  EAX c040f080
     err 00000000  EIP c0452eb9   CS 00000060  flg 00000082
```
Plus a stack dump (see Image)
[[IMG]http://img177.imageshack.us/img177/9730/ubsrv804erruw4.th.gif[/IMG]](http://img177.imageshack.us/my.php?image=ubsrv804erruw4.gif)

Today I tried to re-install the system using the downloaded 8.04 Server, after the setup process finished and restarted the system I have the same error message.

Does anyone else have troubles with booting into 8.04 server?

Any help appreciated.
  Thanks

---

### Post by Fuse314 on 2008-04-25
I just tried pressing [esc] when "Loading Grub" is displayed, the menu appears, but starting the server using (recovery mode), it throws the same error (see OP)

---

### Post by noyzy on 2008-07-12
Hey I have this exact error when my virtual Ubuntu 8.04 Server boots after install. Did you ever find a fix for this?

---

