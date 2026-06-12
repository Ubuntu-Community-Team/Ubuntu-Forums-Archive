---
title: "Virtual Box &quot;VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)&quot; and setup ignoring me"
date: 2009-06-21
forum: Virtualisation
---

### Post by amylase on 2009-06-21
Hi.

I'm trying to install Virtualbox onto Ubuntu 8.10 (to play Sims 3 on XP). I installed Virtualbox via Synaptic Package Manager and set up a virtual drive etc. and I have my WinXP disc in the DVD drive.
I click on the green arrow labelled "start".
I get these error messages when I try to start up the virtualbox:

> 
Failed to open a session for virtual machine WinXP.

Virtual machine 'WinXP' has terminated unexpectedly during startup.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}




> VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

Funny thing is when I then try to do
sudo /etc/init.d/vboxdrv setup
nothing happens apart from this feedback:
>  * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

I went around reading tutorials. Uninstalled, reinstalled virtualbox. Re-installed DKMS also. Went into system -> admin -> users & groups -> unlock and selected virtualbox. Still the same, nothing seems to help. I get the same results as outlined above.

Am I missing something? Please help. Thanks.

---

### Post by Gen2ly on 2009-06-21
```
modprobe vboxdrv
```

As-root.  I'm thinking that the vboxdrv isn't loaded.

---

### Post by hypernihl on 2009-07-01
Having the same problem in 9.04. The above didn't work. Any solutions??? Thanx

---

### Post by Seithe on 2009-08-30
[IMG]http://ap-trqa.forum0.net/users/19/86/69/smiles/587571.gif[/IMG]

---

### Post by LepeKaname on 2009-12-14
I had the same problem and "/etc/init.d/vboxdrv" was not even present in my installation (v. 2.1.4_OSE)

I solved removing any virtualbox-ose installed package and reinstalling it again. Still I don't have the /etc/init.d/vboxdrv file in my system but it works now without a problem.;)

---

