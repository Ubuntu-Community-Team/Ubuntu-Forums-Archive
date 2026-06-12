---
title: "linux-server or linux-virtual for VMware cloud?"
date: 2011-02-07
forum: Server Platforms
---

### Post by pepoluan on 2011-02-07
Hello,

I am going to deploy some Ubuntu-based servers on our cloud provider.

The cloud provider is using VMware, and I plan to deploy using the MinimalCD.

Post-installation, should I deploy "linux-server" or "linux-virtual" ?

Thank you beforehand.

---

### Post by pepoluan on 2011-02-08
I think I found the answer:

[http://askubuntu.com/questions/18593/which-kernel-to-use-for-server-vm-running-on-esx](http://askubuntu.com/questions/18593/which-kernel-to-use-for-server-vm-running-on-esx)

> **linux-virtual**: This is the ***server kernel***, with most drivers stripped. It only has the drivers needed to run as a guest in the most popular virtual machines like KVM, Xen, and VMWare.

So, based on that info, I think I'll go with the **linux-virtual** kernel.

Any thoughts?

---

