---
title: "Problème de webcam intégrée sous UBUNTU 9.10"
date: 2009-11-06
forum: Tunisia Team
---

### Post by TheWhiteTiger on 2009-11-06
Bonjour tout le monde,
j'ai un laptop professionnel IBM ThinkPad Z61m, qui possède un webcam intégré, que j'arrive pas à le faire fonctionner sous Ubuntu 9.10 (puisque c la distribution que j'utilise actuellement).
je vous tiens informer comme même que le webcam ne fonctionnais pas aussi lorsque j'avais la distribution 9.04 et 8.10 aussi :(

Au par-avant j'avais aussi des problèmes de carte graphique et de quelques boutons spécifiques à ce modèle de laptop, dont j'ai résolu quelques uns et que le passage de 8.10 à 9.04 me les a résolu aussi :) .

Sa n'empêche qu'avec un webcam sur USB, sa fonctionne à merveille!
Pouvez vous m'aider svp!
merci.

---

### Post by Neo31 on 2009-11-06
Salut TheWhiteTiger,
Merci de bien donner les détails du problème de votre webcam. On a encore besoin du résultat que renvoi cette commande :
```
lspci&&lsusb
```> Au par-avant j'avais aussi des problèmes de quelques boutons spécifiques à ce modèle de laptop, dont j'ai résolu quelques uns et que le passage de 8.10 à 9.04 me les a résolu aussi.ca veut dire que c'est complètement résolu ou qu'il en reste encore qq uns? S'il en reste encore, un peut plus de détails sur le problème seront utiles.
Ahmed S.

---

### Post by TheWhiteTiger on 2009-11-08
le résultat de la commande lspci&&lsusb :

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752M Gigabit Ethernet PCI Express (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
15:00.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
15:00.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
15:00.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
Bus 001 Device 010: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 007: ID 0c45:627b Microdia PC Camera (SN9C201 + OV7660)
Bus 001 Device 004: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 003: ID 0ac8:3330 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Nizarus on 2009-11-08
Ta webcam est : ID 0c45:627b Microdia PC Camera (SN9C201 + OV7660)
tu peux faire une petite recherche avec le code ID 0c45:627b ou le nom de ta webcam pour voir si il y a déjà une solution.
Exemple : [https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

---

