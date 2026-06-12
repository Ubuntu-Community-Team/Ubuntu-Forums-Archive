---
title: "Virtualbox fails on loading a Windows 7 VM"
date: 2024-11-12
forum: Virtualisation
---

### Post by impracticaldogg on 2024-11-12
Years ago I created a Win7 VM using the installation details for a new laptop . Replaced Win 7 with Ubuntu. Used that VM for quite a while under Ubuntu 20.04, and then copied it to an external hdd before wiping that laptop (wasn't new anymore). Now when I try and open that VM under Ubuntu 22.04 on the new laptop (also Ubuntu 22.04) I get the message: "The Virtual Machine ran into a non-fatal error... " for a short while, and then a dialogue to end the session. I've checked the VM settings and scanned the log file, but can't work out what is wrong.

Please advise me what I should do. I didn't create an OVA of the machine that I can find :(

I've attached the log file and png as per instructions.

Thanks!

---

### Post by impracticaldogg on 2024-11-13
I could run the VMs under Oracle VB 7.1 under Windows 11. They would not register with VB at first. Was successful using the command line. Then exported to OVA as soon as possible. 
VB 6.1 under Ubuntu 22.04 would not work. Assume VB 6.1 will be able to import the Win 7 VMs

---

### Post by impracticaldogg on 2024-11-14
Had to replace the Ubuntu stock distribution of VB with the latest release from the website before I could run any of the VMs. Now everything is running fine

---

### Post by ajgreeny on 2024-11-14
VBox 6 is no longer supported so it is necessary to use VBox 7 for security reasons.
Great news that your VMs now run!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 
It is a great help to other users searching the forum.

---

