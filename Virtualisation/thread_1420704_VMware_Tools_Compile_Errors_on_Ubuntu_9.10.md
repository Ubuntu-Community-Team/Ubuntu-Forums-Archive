---
title: "VMware Tools Compile Errors on Ubuntu 9.10"
date: 2010-03-03
forum: Virtualisation
---

### Post by neilneil2000 on 2010-03-03
Hi all, 

I have successfully installed VMWare on Ubuntu 9.10 server edition  (64 bit) and have created a virtual machine running Ubuntu 9.10 server edition (32 bit).

However I am unable to successfully configure vmware tools, I get errors during the compile stages, starting with having conflicting types for "poll_initwait".

I have attached the log file from the "vmware-config-tools.pl" output.

The bottom of the file also confirms the installation of relevant headers and build tools, as well as stating the uname.

Any hints appreciated

---

### Post by dcstar on 2010-03-06
> **neilneil2000 said:**
> Hi all, 

I have successfully installed VMWare on Ubuntu 9.10 server edition  (64 bit) and have created a virtual machine running Ubuntu 9.10 server edition (32 bit).

However I am unable to successfully configure vmware tools, I get errors during the compile stages, starting with having conflicting types for "poll_initwait".

I have attached the log file from the "vmware-config-tools.pl" output.

The bottom of the file also confirms the installation of relevant headers and build tools, as well as stating the uname.

Any hints appreciated

Regardless of the compile errors, does vmware-toolbox launch?

---

