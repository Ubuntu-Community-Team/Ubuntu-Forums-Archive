---
title: "Can Wine access Virtualbox somehow?"
date: 2011-05-30
forum: Wine
---

### Post by madsmr on 2011-05-30
Hey.

I have 11.04. I also have Win7 on virtualbox. Is it possible for Wine on my Ubuntu to access and run .exe's in Win7 on virtualbox? If not directly (I'm thinking via the .vdi file in the .Virtualbox folder), then maybe through networking when Win7 is running?

---

### Post by cogadh on 2011-05-30
Not possible and not really a good idea. Even if Wine could access the virtual image, it's not designed to work with an existing Windows installation. Best case scenario, using Wine to run stuff from your Windows drive simply won't work; worst case, it breaks Windows. Software is meant to be installed in Wine first, then used.

---

### Post by bobwyajnr on 2011-05-30
> **madsmr said:**
> Hey.

I have 11.04. I also have Win7 on virtualbox. Is it possible for Wine on my Ubuntu to access and run .exe's in Win7 on virtualbox? If not directly (I'm thinking via the .vdi file in the .Virtualbox folder), then maybe through networking when Win7 is running?

In a word - no!

Long answer - [read the Wine FAQ]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2") (hint 3.1) before attempting advanced usage like this!

Your welcome of course to see what happens (but clone or take a state snapshot of your virtual machine first)!! :popcorn:

You would need to mount the VirtualBox (Samba) folder share using your **fstab** file, **mount.cifs** or Nautilus (*smb* auto-mount in **~/.gvfs/**). The former two tend to work slightly more reliably for Wine (in my experience).

I've certainly been able to launch Windows installers located on Samba shares (using Wine). I've even been able to loop-back mount an .iso image on a remote Windows Samba share (Share mounted using **mount.cifs**) and then execute the installer on that disc. The problem comes when you try to run Windows applications that think they are *installed* somewhere else...:) Also should add I believe Wine has problems installing to non-native file-systems (e.g. that use userspace drivers e.g. NTFS-3G, Samba, etc.)

Bob

---

