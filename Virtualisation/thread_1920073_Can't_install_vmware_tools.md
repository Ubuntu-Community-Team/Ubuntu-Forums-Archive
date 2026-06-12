---
title: "Can't install vmware tools"
date: 2012-02-04
forum: Virtualisation
---

### Post by WongFuChu on 2012-02-04
I'm using VMware Player 4.0.2 build-591240 and when I click install virtual "Install VMware Tools..." I get an error that says "Could not find component on update server. Contact VMware Support or your System Administrator."

I'm completely new to VMware so I only installed the .bundle I found on their site. I tried Virtualbox and was able to install guest additions to it. Is there anything from virtualbox that could conflict with vmware? I installed open-vm-tools and linux-headers-virtual, but that didn't help.

I'm currently using Ubuntu 11.10

---

### Post by dcstar on 2012-02-04
> **WongFuChu said:**
> I'm using VMware Player 4.0.2 build-591240 and when I click install virtual "Install VMware Tools..." I get an error that says "Could not find component on update server. Contact VMware Support or your System Administrator."
.........

This is a bug in Player 4.0.2, if you uninstall it and then download and install Player 4.0.1 it should work ok.

---

### Post by WongFuChu on 2012-02-05
Thanks! That worked. :D

---

