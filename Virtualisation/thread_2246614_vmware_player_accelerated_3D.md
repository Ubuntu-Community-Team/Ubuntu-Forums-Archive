---
title: "vmware player accelerated 3D"
date: 2014-10-02
forum: Virtualisation
---

### Post by MikeCyber on 2014-10-02
I'm downloading right now win10 and will try it today in the free vmware player:
  
 [http://windows.micro...ows/preview-iso]("http://windows.microsoft.com/en-us/windows/preview-iso")
  
 [https://my.vmware.co...ware_player/6_0]("https://my.vmware.com/de/web/vmware/free#desktop_end_user_computing/vmware_player/6_0")
  
 If accelerated 3D works, like they claim, this will save me hd space as I don't need to fully install it anymore but fire it up
 from Ubuntu. Same for OSX later, if all goes well.
 
Do I need to install Nvidia drivers to get acc. 3D? What about osx?

---

### Post by TheFu on 2014-10-02
No. The actual video hardware inside the physical PC doesn't matter to VMs at all.  Just install the guest additions after the install of the guest VM is finished and rebooted.

Don't know anything about OSX inside VMs. Don't hear much about it, so I don't expect it is trivial.

BTW, you'll find that more people here use VirtualBox than Player, so it may be nicer for support help here.  Picking the lessor of 2 evils (Oracle vs VMware) isn't exactly easy. ;)

---

### Post by MikeCyber on 2014-10-03
Thanks. Yes you might only get basic 3D apps runnning but for ex. X-Plane quits with a shader error message. So I'm done and won't investigate/use that any further, but for a quick preview before installing distros etc.

---

### Post by bashiergui on 2014-10-06
> Don't know anything about OSX inside VMs. Don't hear much about it, so I don't expect it is trivial.You probably don't hear much because the OSX EULA requires that it only be installed on Apple hardware, and I'm guessing Hackintosh isn't supported in this forum.

---

