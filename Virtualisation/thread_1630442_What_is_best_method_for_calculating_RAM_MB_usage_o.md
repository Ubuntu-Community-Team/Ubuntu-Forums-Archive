---
title: "What is best method for calculating RAM MB usage of an OS in VirtualBox?"
date: 2010-11-25
forum: Virtualisation
---

### Post by Rytron on 2010-11-25
Hi.

What is the best method for calculating the RAM MB usage of an OS in VirtualBox? To run as a live CD OR to install as a VDI?

The reason I ask is because I ran PCLinuxOS-LXDE-2010.10 with the following programs open: Calculator, File Manager, Firefox, Terminal, Text Editor

[COLOR="DarkSlateGray"]For the LiveCD in virtual box, **245MB** of RAM was used.[/COLOR]

[COLOR="DarkRed"]For the installed VDI in virtual box, **132MB** of RAM was used.[/COLOR]

Almost 50% less. Therefore is running a live CD misleading when calculating potential RAM usage?

---

### Post by kemra on 2010-11-25
I do beleive a LiveCD loads the components it needs to run the live environment into RAM (thats how you can try it without installing to had disk first). Therefore the LiveCD will always report more used RAM than if the Distro is installed to the hard disk assuming you have the same apps open in each.

---

### Post by Rytron on 2010-11-25
> **kemra said:**
> I do beleive a LiveCD loads the components it needs to run the live environment into RAM

Hi kemra. Yes, that makes sense.

---

