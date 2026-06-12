---
title: "Virtualbox --&gt; KVM (WindowsXP)"
date: 2010-03-16
forum: Virtualisation
---

### Post by gunksta on 2010-03-16
I am interested in converting a Virtualbox appliance to KVM. Because it's an installation of Windows, I have to be a little more careful. I'm curious to see if anyone has any experience moving WinXP from Virtualbox to KVM. I am especially interested in steps to prevent XP from triggering a need to re-authorize itself, since this doesn't always work out well.

For the record -- yes the license is legal and I am only running it on a single system. I'm interested in moving to KVM because I am not confident in Virtualbox's future under Oracle.

---

### Post by gunksta on 2010-03-19
bump

---

### Post by TheFu on 2010-03-19
I'm interested in this too. 

I've been successful in migrating an xubuntu from .vdi to .img and things are working fine (actually very good), but migration of WinXP always fails at boot.  Obviously, KVM will need to emulate the same hardware that you selected under VBox.  I found that the "Intel PRO/1000 MT" NIC in vbox can be emulated with [I]
-net nic,model=e1000,macaddr=00:11:22:33:44:70[/I] 
under KVM (using the Linux client as test).  

I'm having less success with the PIIX4 IDE controller emulation, however.  This is critical since Windows requires a reinstall when the disk controller chipset changes. ** Perhaps there's a boot offset that I should apply to get XP booted under KVM?**
The IO-APIC and VT-x settings would be critical too. I've read that KVM APIC was considered experimental, but that could have been an old post.

Of course, you mush de-install the vbox client extensions while running under vbox before the migration has any hope of working. With WinXP, I found if I didn't un-mount the extensions prior to the reboot, they would be automatically found and reinstalled after.

If I uncover anything else, I'll post here.

---

