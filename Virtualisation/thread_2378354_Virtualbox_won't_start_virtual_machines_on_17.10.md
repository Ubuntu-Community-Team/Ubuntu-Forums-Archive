---
title: "Virtualbox won't start virtual machines on 17.10"
date: 2017-11-22
forum: Virtualisation
---

### Post by r.whitney on 2017-11-22
When trying to start my Windows 10 VM I got the following error:

```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing


'/sbin/vboxconfig'


as root.


where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.
```

After this error, I attempted installing the linux headers suggested by `/sbin/vboxconfig` however now after running vboxconfig and compiling the kernel modules needed to make virtualbox run, I get the following error:

```
RTR3InitEx failed with rc=-1912 (rc=-1912)


The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing


'/sbin/vboxconfig'


may correct this. Make sure that you do not mix the OSE version and the PUEL version of VirtualBox.


where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user. 
```

---

