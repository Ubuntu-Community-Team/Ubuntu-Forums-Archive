---
title: "Best Vitualization for Server"
date: 2008-12-07
forum: Virtualisation
---

### Post by quikone8 on 2008-12-07
I posted a question about 30 minutes ago and now decided to ask this one.

Is there a better way to go about running a virtual server?  I am trying to install VMware vitual server, but is there a better way?

---

### Post by jmoorse on 2008-12-07
After having worked with quite a few of the Virtualization Platforms, here is my two cents.

1. VMWare ESXi is phenomenal for a enterprise grade server (e.g.: Dell Poweredge 2950, HP Proliant 380, etc).  Super fast, No USB, requires specialized hardware
2. VMWare Workstation is GREAT for the home workstation turned server.  Does support USB > Guest emulation
3. VMWare server is ok, not a fan of the web based interface.  Supports USB
4. Windows Server 2008 Hyper-V is great for a real server, no USB, licensing costs are a pain though
5. VirtualBox is getting rave reviews throughout the OSS community

Assuming you are operating on a workstation I would recommend VirtualBox or VMWare workstation (if you don't mind the cost)

---

### Post by PilotJLR on 2008-12-07
It really depends on what your needs are...

1. Do you want a want to dedicate a physical server to this task exclusively?
2. Do you want or need to run Linux on the bare metal?
3. If the answer to #1 is yes, is your server on the HCL from VMware ESXi?


ESXi is the best hypervisor, IMO... but it requires dedicated hardware on the HCL. If you want to run Vm's to coexist with an Ubuntu desktop, then the big choices are VMware Server, Workstation, Virtualbox, or KVM.

---

### Post by quikone8 on 2008-12-08
> **PilotJLR said:**
> It really depends on what your needs are...

1. Do you want a want to dedicate a physical server to this task exclusively?
2. Do you want or need to run Linux on the bare metal?
3. If the answer to #1 is yes, is your server on the HCL from VMware ESXi?


ESXi is the best hypervisor, IMO... but it requires dedicated hardware on the HCL. If you want to run Vm's to coexist with an Ubuntu desktop, then the big choices are VMware Server, Workstation, Virtualbox, or KVM.

1.  No, physical server to run email server (Citadel)
2.  Linux will run on bare metal as well as virtual.
3.  Knowing more, does that change your answer?

4.  KVM looks interesting, is it finished enough to effectively use and are there decent directions?

Does Ubuntu ahve anything out of the box that works well?

---

### Post by bodhi.zazen on 2008-12-08
I think it depends on your needs. You are going to bet a better fit if once you generate a list of what you need / want search for a solution.

If you are new to Virtualization, take a look at VMWare or VirtualBox.

If you want a "bare metal" solution, take a look at OpenVZ or KVM.

---

