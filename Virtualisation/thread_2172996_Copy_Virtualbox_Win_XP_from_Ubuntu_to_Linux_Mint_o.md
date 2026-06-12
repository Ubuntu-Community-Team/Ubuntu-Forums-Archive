---
title: "Copy Virtualbox Win XP from Ubuntu to Linux Mint on dual-boot PC"
date: 2013-09-07
forum: Virtualisation
---

### Post by nhramirez on 2013-09-07
Hi,

I have a dual-boot distros on my laptop (Ubuntu 12.04 and Mint 13) with virtual Windos XP (using VirtualBox), installed on Ubuntu. I want to copy that Windows to my Mint.
What should I do?
Sorry if there is a thread for that already, but I couldn't find it.

---

### Post by howefield on 2013-09-07
I put the VMs on a separate data partition (actually a separate disk for best performance) then point each install to the same VM.

---

### Post by nhramirez on 2013-09-07
That's really good solution for fresh installation. Unfortunately I already have installed VM with working Windows on my Ubuntu.

---

### Post by monkeybrain20122 on 2013-09-07
You can clone the vdi for the VM and move it to the other OS. Open VB in the host OS (Ubuntu in your case), choose the guest OS to be cloned (win xp in your case ), then click "Snapshot" and click the button with the sheep. It will create a clone in your vbox folder. It may take a while. After that move the clone vdi to your second OS (Mint in your case), start vbox in Mint, create new and use the clone vdi as you would with any guest OS and that's it. 

I have done this but may have forgotten some details. You can google "clone virtualbox" for more info if stuck, but many tutorials are unnecessarily complicated as they are based on older versions of vbox. In particular there is no need to use command line or edit any file.

---

### Post by nhramirez on 2013-09-07
Thank you @[COLOR=#000000]monkeybrain20122! It works. [/COLOR]=D>

---

