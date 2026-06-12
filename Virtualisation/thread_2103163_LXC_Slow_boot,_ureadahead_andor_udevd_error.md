---
title: "LXC Slow boot, ureadahead and/or udevd error"
date: 2013-01-09
forum: Virtualisation
---

### Post by jod on 2013-01-09
I have 3 physical servers running lxc on ubuntu amd64 minimal.

host1, Ubuntu 12.04.1 LTS
host2, Ubuntu 12.04.1 LTS
host3, Ubuntu 12.10 (just installed)

I have multiple containers running, on hosts 1 and 2 which operates perfect. Host3 is newly installed, and I followed my notes from the previous hosts installations.

- I execute lxc-create to create the lxc container, which works.
- Then I edit the network details, to have network connectivity.
- Then I startup the container using lxc-start -n container1, where I get this info.

```
# lxc-start -n container1
<4>init: ureadahead main process (5) terminated with status 5
<4>init: udev-fallback-graphics main process (50) terminated with status 1
<4>init: console-font main process (65) terminated with status 1
<4>init: setvtrgb main process (80) terminated with status 1
<4>init: console-setup main process (97) terminated with status 1
<30>udevd[132]: starting version 175

Ubuntu 12.10 container1 console

container1 login: <4>init: setvtrgb main process (740) terminated with status 1
```

This takes somewhere between 3-5 minutes, hence my complaining, as the startup process is less than 30 secs on all other lxc hosts/containers.

When testing the functionality of the container, everything works. I can get out from the container to the network, and also from the "outside" into the container. The operation speed is good, once the container is started.

Any good ideas how to resolve this is greatly appreciated.


--
JOD

---

### Post by jefferai on 2013-03-03
I just ran into this same problem. Did you ever figure it out?

Thanks,
Jeff

---

### Post by jefferai on 2013-03-03
Oh, figured it out. By default the container will try to DHCP, and timing out takes a very long time. A modification to set the /etc/network/interfaces file in the rootfs to declare eth0 as "manual" rather than dhcp fixes the problem.

---

