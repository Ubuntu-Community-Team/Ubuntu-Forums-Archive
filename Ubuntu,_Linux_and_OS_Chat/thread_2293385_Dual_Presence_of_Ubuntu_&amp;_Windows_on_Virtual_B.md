---
title: "Dual Presence of Ubuntu &amp; Windows on Virtual Box, Easier than Dual-Boot?"
date: 2015-09-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Geoffrey_Arndt on 2015-09-04
Sorry for the long title, but as I've become much less savvy with any version of Windows (than Linux) . . . I'm wondering if there's a down side to removing Windows from a dual-boot laptop with 6 gb ram & I5 1st gen duo cpu?    I do zero gaming - - so that's not an issue.    In other words, is it easier to maintain Windows as a guest OS than it is to do a full dual boot.    I've never run a virtual machine, but have read up on them over past couple years.   Seems it would be easier to switch between OS's as no reboot involved.

However, even as a guest OS, the MS security patches will or should be applied also (yes/no/maybe so?).   Is file sharing and access still harder with a VM than a traditional dua-boot?

---

### Post by msh8er on 2015-09-04
I've seen Win8 and I have no desire to see Win10, so I'm leaning toward setting up Win7 and MS Office 2007 as a VM.  Other windows programs, e.g. Quickbooks, which require a later OS will be in another VM.  
I've used Ubuntu with Windows in dual-boot environments for years, but Ubuntu is of little benefit to the users which I support.  I've been experimenting with Win7, Ubuntu 14.04, and VM Box.  While seemingly a good idea, I've spent a week trying to get it to work.  Very little user support (Oracle wants you to subscribe, funny how that works) so I'm not sure where I'll go next. 
Would appreciate your ideas/feedback.

---

### Post by jason_gibson2 on 2015-09-04
I'm also looking for suggestions on this topic. I'm currently running Windows 10, I do like it but I prefer a Linux environment at home. However I need to keep a Windows going for Quickbooks and Office. My laptop is only so powerful so I don't know what to do. I don't want to stay with Windows, but I don't know if I can rely on a virtual machine on my laptop either. Considering dual boot but once you start dual booting what is the point. I'd kind of like best of both worlds at the same time.

---

### Post by howefield on 2015-09-05
> **Geoffrey_Arndt said:**
> However, even as a guest OS, the MS security patches will or should be applied also (yes/no/maybe so?).   Is file sharing and access still harder with a VM than a traditional dua-boot?

Yes, your windows vm would need to cared for just the same as it would installed directly to the machine. No difference, so anti virus, updates ect, ect, all need to be maintained. File sharing isn't any harder on a vm, use bridged mode in the network settings to make the vm appear as a machine on the network.

One suggestion I'd add is to have the VM on a separate disk for better performance if possible.

---

