---
title: "Save and Re-install virtual machine, as is?"
date: 2011-03-26
forum: Virtualisation
---

### Post by teejay17 on 2011-03-26
Hi all,
I'm just wondering if it is possible to somehow save my virtual machine externally, to a back up hard drive, to be re-installed at a later time? 
My host machine is Ubuntu 10.04 and I'm hosting Windows 7 in VirtualBox. With a new release of Ubuntu looming, I want to know if I can back up the virtual Windows 7 as-is, to be re-installed in VirtualBox after I reformat my host system.

---

### Post by CharlesA on 2011-03-26
Export it and then import it into the new install.

---

### Post by teejay17 on 2011-03-26
> **CharlesA said:**
> Export it and then import it into the new install.
Wow, it's that easy eh? Cool. 
So I just have to go through the screens in the Export Appliance, and then when it is time to import, run the Import Appliance?

---

### Post by CharlesA on 2011-03-26
> **teejay17 said:**
> Wow, it's that easy eh? Cool. 
So I just have to go through the screens in the Export Appliance, and then when it is time to import, run the Import Appliance?
Yep.

---

### Post by SeijiSensei on 2011-03-26
> **CharlesA said:**
> Yep.

Actually I've found that just preserving my $HOME/.VirtualBox directory is sufficient.  Last time I installed I just copied that from backup and all my VMs were there and working.  Upgrading to 4.04 didn't have any problems with them either.

---

### Post by CharlesA on 2011-03-26
> **SeijiSensei said:**
> Actually I've found that just preserving my $HOME/.VirtualBox directory is sufficient.  Last time I installed I just copied that from backup and all my VMs were there and working.  Upgrading to 4.04 didn't have any problems with them either.
That can work too. With VBox 4.0, they changed the location the virtual machines are stored.

You can backup ~/.VirtualBox and ~/VirtualBox VMs and then restore then and be good to go.

EDIT: The new location only applies to new virtual machines and virtual machines you've exported and imported again. Existing VMs still reside in ~/.VirtualBox.

---

### Post by drdos2006 on 2011-03-26
I store my VMs in the data section of my hard drive. ie /media/sda2/VirtualDrives. I also store the ISOs there as well. On initial setup I load the ISO through the CD location and reset the CD back to the physical drive after installation.

regards

---

### Post by HermanAB on 2011-03-27
As noted above, for Virtualbox, it is best to use the export/import function.

For VMware, simply make a tar ball of the directory the VM resides in.

---

