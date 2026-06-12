---
title: "can't install VMware player on 10.04"
date: 2010-05-02
forum: Virtualisation
---

### Post by aeon.flux on 2010-05-02
hi there, 
I can't install VMware player 3.0.0 on ubuntu 10.04 (gnome). 

I had VMware player on 9.10 and I used this [https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player) / part with "Installing VMware Player on Ubuntu 9.04" and it worked fine. 
I've installed 10.04 2 days ago and I would like to work with vmware player, but I can't install it using the same "howto". Can somebody find any other way do install it or can somebody tell me where am I wrong?

After instalation the shortcut in gnome menu is created, after opening system writes this:
1. "Before you can run VMware, several modules must be compiled and loaded into the running kernel."
2. I press "_Install" button
3. system asks for password (I type it in lol)
4. a little window writes this: 
- stopping vmware services
- compiling:
virtual machine monitor (ok icon)
virtual network device (! icon)
vmware blocking filesystem (ok icon)
virtual machine communication interface (ok icon)
VMCI sockets (ok icon)
- starting vmware services (error icon)
4. tiny windows tells me: "Unable to start services. See log file /tmp/vmware-root/setup-22042.log for details." 
5. i try to find and open that log file, but i can't access it what ever i do :(

---

### Post by marco.orazi on 2010-05-04
Hi aeon.flux,

I had the same problem, resolved installing the new version (3.0.1) of vmware player from vmware.com.

1. Download and install the 3.0.1 player (this uninstall the previous version 3.0.0);

2. Launch the new player and open the existing virtual machine on your filesystem

First of all, make a backup of your virtual machine!

HTH,
Marco

---

### Post by winchendonsprings on 2010-05-05
Any idea how to get past the compiling errors with Workstation7?

---

### Post by dcstar on 2010-05-05
> **marco.orazi said:**
> 
.......
First of all, make a backup of your virtual machine!


There is no need to backup VMs when doing things like upgrading to a (slightly) newer version of the same VM software.

And it is Player 3.1, which has just gone out of beta (my beta install upgraded automatically the other day).

---

### Post by aeon.flux on 2010-05-06
> **marco.orazi said:**
> Hi aeon.flux,

I had the same problem, resolved installing the new version (3.0.1) of vmware player from vmware.com.

1. Download and install the 3.0.1 player (this uninstall the previous version 3.0.0);

2. Launch the new player and open the existing virtual machine on your filesystem

First of all, make a backup of your virtual machine!

HTH,
Marco

tnx a lot, its working : )

---

### Post by aimaz on 2010-05-18
> **marco.orazi said:**
> Hi aeon.flux,

I had the same problem, resolved installing the new version (3.0.1) of vmware player from vmware.com.

1. Download and install the 3.0.1 player (this uninstall the previous version 3.0.0);

2. Launch the new player and open the existing virtual machine on your filesystem

First of all, make a backup of your virtual machine!

HTH,
Marco
This worked for me. Thanks.

---

