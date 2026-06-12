---
title: "No Seccomp for most Ubuntu 24 processes?"
date: 2024-06-15
forum: Security
---

### Post by currentshaft on 2024-06-15
4d

---

### Post by 0f4d0335 on 2024-06-27
The good news is that many of your applications are likely managed with a snap seccomp profile. [https://ubuntu.com/core/docs/security-and-sandboxing#heading--appArmor-seccomp-and-device-permissions](https://ubuntu.com/core/docs/security-and-sandboxing#heading--appArmor-seccomp-and-device-permissions)

You can check which seccomp profiles are located on your local computer from this directory in 24.04 LTS - /var/lib/snapd/seccomp/bpf/

It appears these processes do not have seccomp profiles. [https://lwn.net/Articles/857228/](https://lwn.net/Articles/857228/)

They can be created with a tool like easyseccomp. [https://github.com/giuseppe/easyseccomp](https://github.com/giuseppe/easyseccomp)

I wanted to see if simply having a seccomp profile for snap would solve your issues, but it appears that it's only used to notify you when snaps are due to reset. [https://askubuntu.com/questions/1443676/snapd-desktop-integration-syslog-spam](https://askubuntu.com/questions/1443676/snapd-desktop-integration-syslog-spam)

---

