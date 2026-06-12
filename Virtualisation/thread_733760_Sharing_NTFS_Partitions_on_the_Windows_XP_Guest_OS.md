---
title: "Sharing NTFS Partitions on the Windows XP Guest OS via Virtual Box"
date: 2008-03-24
forum: Virtualisation
---

### Post by amrith on 2008-03-24
I have installed Windows XP as a guest on my Ubuntu Gutsy through Virtual Box.

I Have several NTFS partitions on the physical hard drive which I want to access on my Virtual XP .

Sharing Folder option in VirtualBox just tries to share the / file system.

How do I access my Physical NTFS partitions on my Guest windows XP which is on ubuntu Gutsy ?

Thanks.

---

### Post by codeslicer on 2008-03-24
I can't say that my explanation is correct as I have upgraded to Hardy removed vmware-server (Apparently there is some replacement built in)

But as far as I can remember:
First, go to the configuration of that virtual machine. Then, add a hard drive or something like that. Find the one that you want and add it.

If I'm wrong, do a google search. :)

---

### Post by Kiri on 2008-03-24
> **amrith said:**
> 

Sharing Folder option in VirtualBox just tries to share the / file system.

How do I access my Physical NTFS partitions on my Guest windows XP which is on ubuntu Gutsy ?




How about if you mount the drives in ubuntu first? Then I think they should show up in the vbox sharing options.

---

### Post by amrith on 2008-03-24
Too add the drives as Hard Drives .Virtual Box does gives an option of adding NEW Physical drives but not existing ones.So If I add them it would be a new empty hard drivein XP.

Yes, I tried mounting the NTFS on ubuntu but I couldnt share them as the share option doesnt show me me the NTFS partions to share them either.

---

