---
title: "slow host with Win7 guest"
date: 2012-06-22
forum: Virtualisation
---

### Post by RikoW on 2012-06-22
Hi all,

I have compiz with various effects enabled on 12.04 with unity shell. it's a 64 bit installation running VM WS 8.0.4 and VMplayer 4.

Starting a Win7-64bit guest in VMware slows down the host considerably, so that it is almost impossible to work productively, even if I'm not actually logged in to the guest but it's just sitting with the login screen.

Running a WinXP-32bit guest is very snappy on both host and guest. Is anyone experiencing something similar and maybe even found a solution (like turning certain effects off)?  

Thanks and cheers,
      Riko

PS: Using Mint13+Cinnamon as host system does NOT show this behavior ...

---

### Post by TJet1.8 on 2012-06-28
Well...there are many factors that can impead VM performance...too many to list.

So...let's start with the obvious things to check,

1.) Generally speaking, the rule of thumb in assigning virtual hardware resources to a VM are:

a.) do not give a VM more vCPU's than half of your hardwares physical CPU's
(i.e. - If your laptop/workstation has a dual core processor, do not give more than 1 vCPU to your VM, if your laptop/workstation has a quad core processor, do not assigned more than 2 vCPU's to your VM, etc...)

b.) Ensure your host has enough RAM installed to run the host operating system...plus the total amount of RAM you are assigning to your VM's.

c.) Ensure your VMware reserved memory allocation (Edit, Preferences, Memory tab) doesn't reserve more than your host needs (i.e. - If you have 8GB of RAM total, and your hosts requires 1.5 GB to run smoothly without swapping memory to disk, then set the reserved memory in VMware to 6.5GB).

d.)  In the same screen where you configure reserved memory, make sure your additional memory settings are set to "Fit all virtual memory in reserved host RAM". Anything else will start swapping memory to disk...which will slow down performance.

e.) Make sure you have installed VMware Tools in your Guest Operating System.

This is just a start....

P.S. - If your laptop/workstation has very little RAM or only has a single physical CPU....GET A NEW laptop/workstation with alot of RAM and/or multiple CPU cores!!

Good luck!!

---

### Post by RikoW on 2012-06-29
Thanks for the general hints. That is certainly also helpful for people starting to use virtualization.

What helped me in the end was reducing the VM RAM to the recommended value by VMware (1 GB). My host has 4 GB and I had 2 GB assigned to the Win7 guest. There didn't seem to be a problem with swapping, since I monitored host RAM and swap and neither was the RAM maxed out nor was more than minimum swap used.

The Win7 image required 2 GB of RAM to install, so I reduced the RAM after the slowness issues occurred.

I also had problem with 3D acceleration of the guest, so had to turn that off.

The the Win7 guest is running great, except some artefacts of tooltip windows of the guest remain on the on the host desktop when the guest runs in VMware unity mode. The goes away after restarting the window manager. So may with going updates of compiz, unity of the xorg drivers that will be fixed.

The original issue was solved by reducing the RAM, so I'm mark this thread as such.

Cheers and happy virtualization,

                  Riko

---

