---
title: "New to Virtualization: Where to Start?"
date: 2012-04-12
forum: Virtualisation
---

### Post by ptmuldoon on 2012-04-12
I'm setting up a new home server build and planning/hoping to virtualize things to run multiple OS at the same time.  But I really do not know where to start.

I'm reading up on VMWare, but am unsure of the pros and cons of the best setup.

I would like to be able to run Ubuntu Desktop, Ubuntu Server, Windows7, MacOS, and maybe test out some other distro's along the way.

Would it best to install VMware vSphere Hypervisor (ESXi) onto the bare metal machine, and than to virtualize each OS on its own?  

Or although its a paid version, to install Ubuntu Desktop or some other OS as the Host operating system, and than to install VMWorkstation, VirtualBox, or some other type of Virtual software?

I think installing Hyvervisor may provide better performance?

Any help or tips would be greatly appreciated as I plan for the new setup.

Thanks
PT

---

### Post by sanderj on 2012-04-12
FWIW:

I run Ubuntu 11.10 with VirtualBox installed via the Software Center, and in VirtualBox I run all kinds of guests: Ubuntu, other Linuxes and Windows.

I choose this because it's easy and free.

HTH

---

### Post by CharlesA on 2012-04-12
Note that ESXi is more of an enterprise solution and would need to be run on bare metal. The same can be said for Xen, but if you are going to use Xen, go with CentOS or Redhat.

If you just want to run a native hypervisor, go with those (Xen ftw).

If you just want to install the OS and then install a VM solution on top of the OS, you can go with KVM, Vbox and/or Vmware as there are all pretty much the same.

Sidenote: Installing OSX on anything other than a Mac breaks Apple's ToU and isn't something that is supported here.

---

### Post by ptmuldoon on 2012-04-12
Thanks for the tips guys.   Yes, I was aware that Hypervision is installed on the bare metal.  Thus, not sure if you get better performance that way vs installing Ubuntu first, and than a Vbox, Vmware, etc.

Also, thanks for the tip on OSX.  I will scratch that off my list of OS to test out. 

I'll probably go with VmWare's Hypervisor and than install the OS's after that.

---

### Post by CharlesA on 2012-04-12
Look at the pros and cons of each.

If you want to go baremetal, either ESXi or Xen would work well. I prefer Xen, but ESXi works fine too.

At home, I'm just running VBox headless because it's easy for me to deal with and gets the job done. ;)

---

### Post by ptmuldoon on 2012-04-13
> **CharlesA said:**
> Look at the pros and cons of each.
At home, I'm just running VBox headless because it's easy for me to deal with and gets the job done. ;)

Since your running Vbox headless, what are using then for the host
OS?  I assume ubuntu since where on there forums?

---

### Post by CharlesA on 2012-04-13
> **ptmuldoon said:**
> Since your running Vbox headless, what are using then for the host
OS?  I assume ubuntu since where on there forums?
I'm using Ubuntu 10.04 as the host, but it does a lot more than just VM host. ;)

---

