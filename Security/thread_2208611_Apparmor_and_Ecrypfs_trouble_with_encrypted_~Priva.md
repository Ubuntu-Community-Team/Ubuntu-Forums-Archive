---
title: "Apparmor and Ecrypfs trouble with encrypted ~/Private directory"
date: 2014-03-01
forum: Security
---

### Post by henryx on 2014-03-01
Hi,
In my system I made an encrypted ~/Private directory by ecryptfs-utils package. It work good but I have a problem with apparmor.
Into the Private folder I moved some home directory like .local, .mozilla, .config, ecc... and obviously I link these to my home root. 
Everything works except some apparmor profile (like telepathy) because it does not recognize the new path as a valid path, the message are similar to this:

```
[19753.442963] type=1400 audit(1393681049.447:322): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/home/-my-home-troot-/Private/.config/dconf/user" pid=23758 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
```

of course changing the single profile made apparmor recognize new folders but I wanted to try a more general solution, I tried to change /etc/apparmor.d/tunables/alias but without results.
My question is this: is possible to adapt all apparmor profile in a general way in order to adapt apparmor to a new changes ?

Many thanks in advance

Henry

---

