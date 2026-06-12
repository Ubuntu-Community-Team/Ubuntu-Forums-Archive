---
title: "installing my PCI sat card in Vbox , possible ?"
date: 2008-11-19
forum: Virtualisation
---

### Post by medya on 2008-11-19
hey
I have a PCI device ,(sat tv card) is it possible to access to it using Vbox or any other virtual software?

I tried to install the driver of my sat card in virtualbox-win xp but it said the hardware is not instaslled .

---

### Post by medya on 2008-11-20
may I bump ?

---

### Post by medya on 2008-12-26
bump !

---

### Post by Dedoimedo on 2008-12-26
I'm not sure if it's possible.

VB has some extended features meant to work with direct physical access, including acpi, io apic, vt, amd-v, and pae, but this may not be applicable for your chipset and even if it is, you still might not get the hardware to work.

Your best bet is to try to enable these extensions and then try to install the driver in the guest.

Dedoimedo

---

### Post by medya on 2008-12-27
how to enable the extentions ? has anyone ever done it before?

---

### Post by Dedoimedo on 2008-12-27
For the relevant virtual machine, click on Settings.
Then, under General > Advanced, see what Extended Features you can enable.
Dedoimedo

---

