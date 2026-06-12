---
title: "viglen mpc-l and acpi"
date: 2008-10-20
forum: Server Platforms
---

### Post by tedius on 2008-10-20
I recently bought a Viglen mpc-l which came with xubuntu 7.04 I think.  Anyway I've installed ubuntu server 8.04.  To get it to boot I had to add acpi=off (I would get a kernel panic with out it) to the grub kernel line (I've also added pnpbios=off as the boot process sugested, though I don't know why).

Now when I use the 'halt' command will go through and stop all the processes, and then just sit there until I press the power button.  Now I presume this is because of the acpi=off bit.  But I know that with the shipped xubuntu the halt command worked.

Does anyone know what I need to do to get this working again?

P.S. It could be apci rather than acpi as I can never remember which way round it is.

---

### Post by volkswagner on 2008-10-20
Do you get the panic if you add acpi=force, rather than acpi=off?

---

### Post by popey on 2008-10-20
acpi=off means that the viglen wont react to acpi calls from the OS. As a result you can't do a shutdown via software.

---

### Post by ChrisBean on 2008-10-24
Hi, I have the same PC and am getting kernel panics too, along with incorrect shutdown.

I have solved this by adding the following commands:

pnpbios=off pci=noacpi

I think the above will let the computer shutdown gracefully.

---

