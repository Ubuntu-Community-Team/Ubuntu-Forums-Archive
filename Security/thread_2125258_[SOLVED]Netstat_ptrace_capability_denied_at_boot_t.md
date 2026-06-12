---
title: "[SOLVED]Netstat ptrace capability denied at boot time (new behaviour)"
date: 2013-03-13
forum: Security
---

### Post by sambhogi on 2013-03-13
I am getting these new apparmor messages at boot time on 12.04 server as of a few days ago:

> kernel: type=1400 audit(1363187474.753:96): apparmor="DENIED" operation="ptrace" parent=1263 profile="/bin/netstat" pid=1266 comm="netstat" target=601C

I don't know why this behaviour has changed, what process is calling netstat at boot time, why it would need ptrace, what the target process is, or whether I should be concerned.

---

### Post by sambhogi on 2013-03-13
I have verified on another instance that this is normal under the default apparmor profile when netstat is invoked with -p. The most likely explanation for the new behaviour is that the bin.ping apparmor profile was previously unenforced, although I don't have logs going back far enough to verify this hypothesis.

---

