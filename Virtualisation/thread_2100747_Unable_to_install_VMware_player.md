---
title: "Unable to install VMware player"
date: 2013-01-02
forum: Virtualisation
---

### Post by asb3 on 2013-01-02
I can't install VMware-player.  I downloaded the bundle and ran

> sudo ./VMware-Player-2.5.5-328052.x86_64.bundle

When I clicked through the gui the installation failed and reported the error message:

You cannot install on a system with KVM installed.

I don't have kvm installed, although I do have virtualbox.

Do I have to remove virtualbox?

---

### Post by asb3 on 2013-01-03
I found the solution:
[http://communities.vmware.com/thread/188359](http://communities.vmware.com/thread/188359)

---

### Post by dcstar on 2013-01-07
> **asb3 said:**
> I can't install VMware-player. 
..........
I don't have kvm installed, although I do have virtualbox.

Do I have to remove virtualbox?

VM environments tie themselves deep into the host OS and having more than one VM installed just won't work.

If you want to play with different VMs then clone your Ubuntu installation (changing the partition UUID) and boot off the different installs with different VMs installed.

---

