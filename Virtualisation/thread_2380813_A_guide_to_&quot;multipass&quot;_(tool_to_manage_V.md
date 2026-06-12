---
title: "A guide to &quot;multipass&quot; (tool to manage VMs, similar to LXD)"
date: 2017-12-22
forum: Virtualisation
---

### Post by simosx on 2017-12-22
multipass is a tool to manage VMs, similar to LXD that manages containers. 
multipass is a snap package, therefore, you can install on all distros that have snap support.

Here is a practical guide on how to use multipass,
[https://blog.simos.info/multipass-management-of-virtual-machines-running-ubuntu/](https://blog.simos.info/multipass-management-of-virtual-machines-running-ubuntu/)

---

### Post by TheFu on 2017-12-22
How is multipass different/better than virsh + libvirt? 

Options are good. Would love a "better" virsh.

---

### Post by simosx on 2018-01-01
> **TheFu said:**
> How is multipass different/better than virsh + libvirt? 

Options are good. Would love a "better" virsh.

A single command can get you boot a VM. It also comes with a repository of Ubuntu images ready to download and use.

For example, 

```
multipass launch -n myserver 16.04
```

is only required to launch a VM called "myserver", running Ubuntu 16.04 (default: 1GB RAM and 2GB disk space).

---

