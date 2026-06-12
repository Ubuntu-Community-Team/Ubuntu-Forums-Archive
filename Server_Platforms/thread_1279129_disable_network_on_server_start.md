---
title: "disable network on server start"
date: 2009-09-30
forum: Server Platforms
---

### Post by xkaliburx on 2009-09-30
Not sure if this is possible, coming from a RH background, but I am remotely using clonezilla to re-image a server.  When it comes up on restart it will have the IP of the existing.  I have remote KVM, so ssh is not an issue, I am wondering on boot, at the grub screen, is there anyway I can either dump to a shell, mount that drive and change the interface file, or specify network not to start on the grub command line?

Thanks

---

### Post by karlson on 2009-09-30
> **xkaliburx said:**
> Not sure if this is possible, coming from a RH background, but I am remotely using clonezilla to re-image a server.  When it comes up on restart it will have the IP of the existing.  I have remote KVM, so ssh is not an issue, I am wondering on boot, at the grub screen, is there anyway I can either dump to a shell, mount that drive and change the interface file, or specify network not to start on the grub command line?

Thanks

Boot into Single User mode.

---

### Post by ainsworth_t on 2009-09-30
You should be able to boot into single user mode through GRUB, and from the root command line you enter, either use update-rc.d to disable networking on startup or you can edit the /etc/networking/interfaces file and comment out the interfaces or edit the settings to your liking.

---

### Post by cdenley on 2009-09-30
If you're using /etc/network/interfaces to configure your network, then when you clone your drive to another computer, the network adapter should be assigned a new name by udev, which would be unconfigured. I think network manager identifies adapters by MAC address, so "new" adapters should remain unconfigured as well.

---

