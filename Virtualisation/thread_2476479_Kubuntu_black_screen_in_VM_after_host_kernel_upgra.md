---
title: "Kubuntu black screen in VM after host kernel upgrade"
date: 2022-06-27
forum: Virtualisation
---

### Post by philld2 on 2022-06-27
This problem began after upgrading the kernel of the host machine to 5.17.13 (and seems to still exist with 5.18.x kernels).

My environment - Host is running Pclinuxos with Virtual Box as the VM hypervisor.  I have several VMs - WinXP (1), Kubuntu (2), Win10 (1).  Seldom run the Win10 VM so not sure if the problem exists there.  The problem does not exist with the WinXP VM.  The problem with the Kubuntu VMs (20.04) is that when booting the VM, I can see that the VM is booting but when it comes to the login screen it either 1) presents the login screen but does not accept the entry of the password (i.e. remains blank) and then after a few seconds the screen will go blank or 2) it goes directly to a blank screen.  In either case, it is not possible to do an ACPI shutdown only possible to close the machine.  The VMs have been running for over a year without a problem and the only update that was done when the problem started was the kernel on the host.

I currently boot the host machine with kernel 5.17.11 and all is fine but would like to resolve this problem.

---

