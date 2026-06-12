---
title: "How to create a lxd VM with a fixed amount of memory?"
date: 2020-09-14
forum: Virtualisation
---

### Post by andrew102 on 2020-09-14
When creating a virtual machine with LXC, all I get is a VM with 1GB memory.

For example
```
 [FONT=Liberation Mono][SIZE=2]lxc launch images:centos/7/cloud vm1 --vm[/SIZE][/FONT]


```

```
$ lxc exec vm1 -- sh -c 'free -m'
              total        used        free      shared  buff/cache   available
Mem:            987          68         820           6          97         796
Swap:             0           0           0
```

I have specific applications that look for the available memory on the host for shirt sizing reasons, and so these applications fail to launch or install. How to set a specific amount of memory to be presented to the VM OS?

---

### Post by Tadaen_Sylvermane on 2020-09-14
[https://stgraber.org/2016/03/26/lxd-2-0-resource-control-412/](https://stgraber.org/2016/03/26/lxd-2-0-resource-control-412/)

---

### Post by andrew102 on 2020-09-15
Thankyou, great cheatsheet. I'd realised now I was adding ```
limits.memory
``` to the device section rather than the config section of the profile before. The command to set the profile config fixes that.

---

