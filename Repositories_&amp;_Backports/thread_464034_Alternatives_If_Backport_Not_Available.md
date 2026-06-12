---
title: "Alternatives If Backport Not Available"
date: 2007-06-04
forum: Repositories &amp; Backports
---

### Post by jemroc on 2007-06-04
Hi, I'm wondering what are the alternatives if a backport isn't available for my system (Dapper)? The software in question is Trac 10.3. I found this backport request that was rejected: [https://bugs.launchpad.net/ubuntu/+source/trac/+bug/75895](https://bugs.launchpad.net/ubuntu/+source/trac/+bug/75895)

Is my only option to install from source now? I'm not sure what the implications of that are.

[LIST][*]Will it destabilize my system (seems like that's why the backport request was rejected)?
[*]Will I miss out on custom Ubuntu fixes to the codebase?[/LIST]

Thanks for any advice.

---

### Post by uberushaximus on 2007-06-06
> **jemroc said:**
> Hi, I'm wondering what are the alternatives if a backport isn't available for my system (Dapper)? The software in question is Trac 10.3. I found this backport request that was rejected: [https://bugs.launchpad.net/ubuntu/+source/trac/+bug/75895](https://bugs.launchpad.net/ubuntu/+source/trac/+bug/75895)

Is my only option to install from source now? I'm not sure what the implications of that are.

[LIST][*]Will it destabilize my system (seems like that's why the backport request was rejected)?
[*]Will I miss out on custom Ubuntu fixes to the codebase?[/LIST]

Thanks for any advice.
[LIST]
[*]Personally I'd just update the system to 7.04 or higher to get a newer codebase.
[*]Seeing that 7.04 is considered stable you shouldn't find any problem with it.
[/LIST]
To update to 7.04 (graphically) type this at the command line
```
sudo update-manager -c
```

---

