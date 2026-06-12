---
title: "VirtualBox disappears going from 17.10 to 18.04"
date: 2018-05-17
forum: Virtualisation
---

### Post by anoldguy on 2018-05-17
I had VirtualBox 5.2 installed on Ubuntu 17.10 (AMD 64 bit desktop).  I just upgraded from 17.10 to Ubuntu 18.04 and I don't see VirtualBox on my desktop or in the applications.  I still have my VirtualBox VMs folder with my vboxusers folder, and my usr/lib/virtualbox folder.  Do I have to start over with a VirtualBox install?  It took me days to get my legal copy of Windows XP running in VirtualBox.  I hope I don't have to do that again.

---

### Post by monkeybrain20122 on 2018-05-17
VB is not a Ubuntu package so was removed when you upgraded. You have to reinstall it. The VM folder (anything in your home) is a part of your data, therefore was kept.

---

### Post by anoldguy on 2018-05-17
Ah, thank you.  It looks like a reset to the beginning.  Sigh.

---

### Post by ajgreeny on 2018-05-18
> **anoldguy said:**
> Ah, thank you.  It looks like a reset to the beginning.  Sigh.
No, not a reset to the begining; if you kept all the configs for VBox in your home along with the VMs themselves it should all be found and run just as it did previously.

---

### Post by monkeybrain20122 on 2018-05-18
> **ajgreeny said:**
> No, not a reset to the begining; if you kept all the configs for VBox in your home along with the VMs themselves it should all be found and run just as it did previously.

I thought it would work too, but I have tried before, didn't work. Reinstall VB and it couldn't find the VM. So I have instead made a snapshot. You can then make a new VM from the snapshot (instead of an iso) if you move your installation or try to run the VM on a different host. That way you keep everything.

---

### Post by SeijiSensei on 2018-05-19
Have you tried using Machine > Add and pointing to the relevant .vbox files?  I've usually been able to reconstruct my menu of VMs this way.

---

### Post by cruzer001 on 2018-05-19
> **SeijiSensei said:**
> Have you tried using Machine > Add and pointing to the relevant .vbox files?  I've usually been able to reconstruct my menu of VMs this way.
That's a good point.

I have also found that a clone of the problem VM will sometimes start when the original will not.

---

### Post by anoldguy on 2018-05-19
Success!  I did an apt install of virtualbox and the extensions.  I started VirtualBox and it had my Windows XP virtual machine.  I started Win XP and it seems to run well.  Thank you to those who replied!  

Note: this was an upgrade in place from Ubuntu 17.10 to 18.04 on the same AMD computer.  I am relieved that I don't have to jump through the Microsoft hoops again.  The only reason I have Windows XP around is to run Pacific Data's Cyberview X to use my PF 3650 slide scanner.  No driver for Linux, Win 7, or Win 10.  I have hundreds of slides to scan.

---

### Post by ajgreeny on 2018-05-20
Make sure to keep a good working snapshot of WinXP  in case it should become corrupt and even though XP is no longer supported you ought to be able to keep it going well enough.

---

