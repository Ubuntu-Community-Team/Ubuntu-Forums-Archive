---
title: "VMWare Player in lubuntu 13.10 - &quot;Unable to install vmnet&quot;"
date: 2014-03-21
forum: Virtualisation
---

### Post by narsarius on 2014-03-21
I am getting the "Unable to install vmnet" error when trying to install VMWare-Player 4.0.6 on lubuntu 13.10. The steps I have followed to reproduce the problem:
1. Install VMWare-Player "sudo sh VMware-Player-4.0.6-1035888.x86_64.bundle"
2. Launch VMWare-Player, returns unable to locate GCC 4.8
3. Install "gcc-4.8" via Synaptic
4.  Launch VMWare-Player, returns kernel headers for version 3.11.0-18-generic were not found
5. Open terminal run "sudo ln -s /usr/src/linux-headers-$(uname -r)/include/generated/uapi/linux/version.h /usr/src/linux-headers-$(uname -r)/include/linux/version."
6. Launch VMWare-Player returns "Before you can run VMWare, several modules must be compiled and loaded into the running kernel". Click install no error nothing happens.
7. Run "sudo vmware-modconfig --console --install-all" in terminal. Returns:

"make[2]: *** [/tmp/vmware-root/modules/vmnet-only/hub.o] Error 1
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-18-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmnet-only'
Unable to install vmnet"

Unable to get past this, does anyone have any tips/direction?

---

