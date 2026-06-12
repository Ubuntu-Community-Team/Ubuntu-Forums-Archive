---
title: "VMWare Workstation 14.0 - not enough physical memory (+other instabilities)"
date: 2017-10-06
forum: Ubuntu Development Version
---

### Post by izznogooood on 2017-10-06
I've been trying to get vmware workstation 14 up and running for days but it would just segfault when creating a new machine. Today I updated Ubuntu and it started working, but there was / is another issue with memory allocation. I have / had the same problem on Antergos and by looking at som vmware forums I found a patch and I "made" a crud way of applying it. Anyway, this will get you up and running! Working great!

```

sudo sucd /tmp
cp /usr/lib/vmware/modules/source/vmmon.tar .
tar xf vmmon.tar
rm vmmon.tar
wget https://raw.githubusercontent.com/mkubecek/vmware-host-modules/fadedd9c8a4dd23f74da2b448572df95666dfe12/vmmon-only/linux/hostif.c
mv -f hostif.c vmmon-only/linux/hostif.c 
tar cf vmmon.tar vmmon-only
rm -fr vmmon-only
mv -f vmmon.tar /usr/lib/vmware/modules/source/vmmon.tar 
vmware-modconfig --console --install-all

```

Another tip you should follow if you run intels onboard graphics is to enable 3D accelleration (adjust GFX memory to the guest machine accordingly) like a 7500U cpu is more than powerful enough for that. VMware does not allow this by default.

add:  

```
mks.gl.allowBlacklistedDrivers = TRUE 
```  

in  ~/.vmware/preferences

Sources:
[https://communities.vmware.com/thread/571370](https://communities.vmware.com/thread/571370)
[https://github.com/mkubecek/vmware-host-modules/commit/fadedd9c8a4d](https://github.com/mkubecek/vmware-host-modules/commit/fadedd9c8a4d)
[https://communities.vmware.com/message/2708206#2708206](https://communities.vmware.com/message/2708206#2708206)
[https://wiki.archlinux.org/index.php/VMware](https://wiki.archlinux.org/index.php/VMware)

---

### Post by rava2 on 2017-11-08
life saver man thank you

---

