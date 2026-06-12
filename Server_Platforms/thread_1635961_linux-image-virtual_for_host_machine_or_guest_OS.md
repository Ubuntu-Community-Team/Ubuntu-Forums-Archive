---
title: "linux-image-virtual: for host machine or guest OS?"
date: 2010-12-02
forum: Server Platforms
---

### Post by Gtaylor on 2010-12-02
I couldn't find a clear answer to this, but is the linux-image-virtual package for host machines that will contain VMs, or a VM-oriented kernel for guest OS (ubuntu)? 

I have some guest VMs running on Microsoft's Hyper-V, and was looking for some further optimizations.

---

### Post by CharlesA on 2010-12-02
That would be used for a virtual machine install of Ubuntu Server, so it's part of the guest, not host.

---

### Post by Gtaylor on 2010-12-02
> **CharlesA said:**
> That would be used for a virtual machine install of Ubuntu Server, so it's part of the guest, not host.
Excellent, thanks. Any idea what specifically has been optimized within this?

I feel bad asking something so trivial, maybe my Google-fu is getting worse with age.

---

### Post by CharlesA on 2010-12-02
I don't really know, tbh. I've tried using the virtual kernel before and didn't really notice all that much difference between it and the regular kernel.

The only thing I know that's different (for sure) is that it was made to be run as a virtual appliance.

---

### Post by wdaniels on 2012-06-06
> **CharlesA said:**
> I don't really know, tbh. I've tried using the virtual kernel before and didn't really notice all that much difference between it and the regular kernel.

The only thing I know that's different (for sure) is that it was made to be run as a virtual appliance.

The difference is that the virtual kernel only bundles drivers needed for the common virtual hardware devices instead of all the modules for real-world hardware.

So it is considerably smaller in terms of disk space. I'm not aware of any tuning for performance or any functional difference that way, I think it's just for smaller images.

---

### Post by Slezhuk on 2012-10-09
[https://help.ubuntu.com/community/ServerFaq#What_are_the_differences_between_the_server_and_virtual_kernels.3F](https://help.ubuntu.com/community/ServerFaq#What_are_the_differences_between_the_server_and_virtual_kernels.3F)

---

