---
title: "[SOLVED] 64 bit virtual os"
date: 2007-11-27
forum: Virtualisation
---

### Post by Inxsible on 2007-11-27
Can I run a 64 bit Xubuntu or a 64 bit Fluxbuntu on my 64 bit Ubuntu?

I have mounted them from the .iso file, but this is the error I get when I select "Install Fluxbuntu" or "Start or install Xubuntu" from the menu:
> Your CPU does not support long mode. Use a 32 bit distribution.I do have the Core 2 Duo, and like I said, I do use 64 bit Ubuntu as my standard installation.

Is there a way I can tell VirtualBox to use both my CPUs ?

---

### Post by Delvien on 2007-11-28
> **Inxsible said:**
> Can I run a 64 bit Xubuntu or a 64 bit Fluxbuntu on my 64 bit Ubuntu?

I have mounted them from the .iso file, but this is the error I get when I select "Install Fluxbuntu" or "Start or install Xubuntu" from the menu:
I do have the Core 2 Duo, and like I said, I do use 64 bit Ubuntu as my standard installation.

Is there a way I can tell VirtualBox to use both my CPUs ?


VMs work off a "virtualized" CPU, that CPU is a 32 bit. You cannot install a 64 bit OS on a VM. Sorry

---

### Post by tribaal on 2007-11-28
You cannot using Virtualbox, but you could using VMware products (I do so on a daily basis).

Maybe Xen could help you do that too, but I'm not too familiar with how it works.

Hope this helps.

- trib'

---

### Post by Inxsible on 2007-11-28
> **tribaal said:**
> You cannot using Virtualbox, but you could using VMware products (I do so on a daily basis).

Maybe Xen could help you do that too, but I'm not too familiar with how it works.

Hope this helps.

- trib'

Then, maybe I should give VMWare a try :)

Thanks guys !

---

### Post by dfreer on 2007-12-01
Just a side note: You should be able to run 64 clients on Vmware Server, *provided* that you have a VT-enabled processor, as I found out my processor didn't actually support VT and now I can't run 64-bit clients (thanks newegg! :( ).

Not sure if you can run 64-bit clients if your host OS is 32-bit, though (I know vmware server is a 32-bit application though).

---

### Post by Inxsible on 2007-12-01
yeah. I just ended up using the 32 bit versions of xubuntu and fluxbuntu.

I think, VirtualBox is much easier to set up and use than VMWare. just my 2 cents. :)

---

