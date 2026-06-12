---
title: "VPN connected to Windows 11 host does it automatically cover Ubuntu as the guest"
date: 2024-01-14
forum: Virtualisation
---

### Post by wildmanne39 on 2024-01-14
Hi, I do not think I need to do anything to make my IP address hidden in Ubuntu guest since I installed a VPN in my host windows 11 but I want to make sure and see if there is anything I can do to make my connection more secure in Ubuntu.

Thanks for all help.

---

### Post by SeijiSensei on 2024-01-15
If the VM is using NAT, your VM's address is never visible. It will be masqueraded as the public-facing address of the Windows host machine. All traffic will then follow whatever routing rules the Win11 machine has.

---

### Post by wildmanne39 on 2024-01-15
Thank you I appreciate your help very much, that is what I thought but all the research I found before posting was about much older versions of Ubuntu.

---

### Post by SeijiSensei on 2024-01-16
It really doesn't have much to do with Ubuntu. It's a function of how the virtual machine is defined. The VMs running on my Windows platforms behave the same as the ones running on Ubuntu hosts.

---

