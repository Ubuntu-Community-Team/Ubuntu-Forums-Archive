---
title: "Ubuntu Host, Vista Virtual Machine.. Can't get nic drivers for vista to work."
date: 2009-09-06
forum: Virtualisation
---

### Post by risen75 on 2009-09-06
Ok, so i have ubuntu 8.10 and i want to run Windows Vista as a virtual machine, ( i have 1 program that i need that will not run under wine, Quickbooks pro 2009) and that is the ONLY reason i keep vista dual booted on my computer.. Now I want to get rid of that partition and just run it under the ubuntu host.. 

Now here's the problem.. no matter what I do I can't get the vista machine to get access to the network card.. it asks for a driver.. but w/o access to the network.. well i can't exactly give it a driver (to my knowledge anyways) 

Any ideas? Please help.. I'm new to the virtualization implementations...

---

### Post by SoftwareExplorer on 2009-09-06
Do you know what the virtualization software is? Virtualbox? VMware?

---

### Post by risen75 on 2009-09-06
VirtualBox-OSE

Sorry I forgot to give details...

---

### Post by SoftwareExplorer on 2009-09-07
What happens if you open virtualbox and select the machine, then in the details tab scroll down to the Network Section and click the "Network" Heading, and in the window that comes up change the adapter type?

Hopefully, you can find one vista supports without needing to download a driver.

---

