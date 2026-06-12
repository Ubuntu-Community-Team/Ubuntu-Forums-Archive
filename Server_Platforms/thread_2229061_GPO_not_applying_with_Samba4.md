---
title: "GPO not applying with Samba4"
date: 2014-06-11
forum: Server Platforms
---

### Post by RomanuX on 2014-06-11
Hello fellow Ubuntu users!
This is my first post on u-forums, been a silent reader so far :p.
I am testing Samba version 4.1.8 on a physical Ubuntu Server 12.04.4 LTS to act like an AD DC.
All looked good with installing, provisioning, added a virtual machine running Windows XP Pro with RSAT to the domain for DC management.
But I am trying to apply a GPO located in forest->Domain Controllers->OU without luck (like Control Panel restrictions and such).
When I log as an normal user the GPO doesn't kick in.
The GPO is effective if I put it under forest directly, right next to Default Domain Policy.
Any idea on what I am doing wrong?
Any help is appreciated.
Thank you

---

### Post by lingpanda on 2014-06-11
> **RomanuX said:**
> Hello fellow Ubuntu users!
This is my first post on u-forums, been a silent reader so far :p.
I am testing Samba version 4.1.8 on a physical Ubuntu Server 12.04.4 LTS to act like an AD DC.
All looked good with installing, provisioning, added a virtual machine running Windows XP Pro with RSAT to the domain for DC management.
But I am trying to apply a GPO located in forest->Domain Controllers->OU without luck (like Control Panel restrictions and such).
When I log as an normal user the GPO doesn't kick in.
The GPO is effective if I put it under forest directly, right next to Default Domain Policy.
Any idea on what I am doing wrong?
Any help is appreciated.
Thank you
Is this a computer or user GPO? Did you place it in the correct OU?

---

### Post by RomanuX on 2014-06-12
It is an User GPO, I've placed it in an OU unde Domain Controller but it doesnt come in effect, only if I move it up on the same level with Default Domain Policy it is effective.

---

### Post by lingpanda on 2014-06-12
> **RomanuX said:**
> It is an User GPO, I've placed it in an OU unde Domain Controller but it doesnt come in effect, only if I move it up on the same level with Default Domain Policy it is effective.

Is the user you are logging in with located in the OU?

---

### Post by RomanuX on 2014-06-13
Yes it is.

---

