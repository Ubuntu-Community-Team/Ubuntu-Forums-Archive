---
title: "Documentation about Ubuntu -server kernel as dom0/domU confusion"
date: 2010-03-12
forum: Virtualisation
---

### Post by halfgaar on 2010-03-12
I'm confused about which kernels to use for the dom0 and domU. [This section]("https://help.ubuntu.com/community/Xen#Karmic%20Notes") has two statements about the -server kernel of ubuntu that appear to be in conflict with each other:

> Recent kernels in Ubuntu are compressed with newer compression techniques lzma and bzip2. Xen 3.2 does not understand how to uncompress these kernels. If you want to use these kernels in your dom0, you need a more recent version of Xen. **Xen 3.3 has worked on kernels up to 2.6.31-19-server.**

and

> Newer Ubuntu kernels include the pv_ops extensions, which means the Ubuntu kernels come all ready to run as domUs. These kernels are included in Ubuntu distributions as the "-server" kernels. You can fetch a complete kernel, include the /lib/modules and other stuff needed to boot it as the linux-virtual package. *These kernels are **not** suitable for dom0 kernels.*

The first statement says that 2.6.31-19-server works on Xen 3.3. Since the previous sentence mentions dom0, it's safe to assume they mean that it runs on Xen 3.3 as dom0.

The second statement, however, states the -server kernels are not suitable for dom0's.

Because the pv_ops are for running the kernel on a hypervisor, and not for allowing it to function as dom0 kernel (the dom0 kernel is given special management privileges and some direct access to the physical hardware via the hypervisor, which pv_opt doesn't do), how can 2.6.31-19-server run as dom0?

So, does the first statement actually mean domU?

---

