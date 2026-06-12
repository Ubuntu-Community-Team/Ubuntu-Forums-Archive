---
title: "Ubuntu solution to monitor and control our office's Virtual Machines"
date: 2009-11-09
forum: Virtualisation
---

### Post by greavette on 2009-11-09
Hello,

We have in our small office a collection of Servers and workstations.  We have 3 servers...one that run's ubuntu and 2 that run Windows 2003.  Each of these three servers have VMWare running for variuos reasons (Citadel Mail server, AjaxPlore file server, Intranet webserver, Accounting image, FOG imaging server...etc).  I'm wondering if there is a tool out there that can monitor all our virtual machines and control them automatically when required.  For example...if we have a power failure and our UPS kicks in...I'd like to control the shutdown of the VM's from one location rather than have each Server shutdown their VM's.  

To clarify our environment...we run VMWare Server 1.09 or 2.0.  We do not run ESXi for any of our Virtual Machines.

Anyone heard of such a tool or product that will run on Ubuntu?

Thanks!

---

### Post by dcstar on 2009-11-11
> **greavette said:**
> Hello,

We have in our small office a collection of Servers and workstations.  We have 3 servers...one that run's ubuntu and 2 that run Windows 2003.  Each of these three servers have VMWare running for variuos reasons (Citadel Mail server, AjaxPlore file server, Intranet webserver, Accounting image, FOG imaging server...etc).  I'm wondering if there is a tool out there that can monitor all our virtual machines and control them automatically when required.  For example...if we have a power failure and our UPS kicks in...I'd like to control the shutdown of the VM's from one location rather than have each Server shutdown their VM's.  

To clarify our environment...we run VMWare Server 1.09 or 2.0.  We do not run ESXi for any of our Virtual Machines.

Anyone heard of such a tool or product that will run on Ubuntu?

Thanks!

The VMware Console can attach and control VMs running on any host on your network.

The console comes with VMware Server 1.0.10 or (AFAIK) is also a separate download from the VMware site.

---

