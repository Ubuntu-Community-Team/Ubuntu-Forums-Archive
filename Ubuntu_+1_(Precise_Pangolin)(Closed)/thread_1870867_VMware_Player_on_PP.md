---
title: "VMware Player on PP"
date: 2011-10-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-28
If anyone is actually running VMware Player 4 on a fully updated PP, including the current kernel, I sure would like to know how you did it. Been playing with it for 40 minutes and get a clue as to why it won't work. It won't even install. 

I have tried patching, fixing the sources to ignore kernel version, manually building kernel module, etc. The thing not only won't work but it outputs no decent info to logs as to why it fails.

Online tutorials and workarounds are targeted at Oneiric and previous kernel.

Thanks,
Effenberg

---

### Post by effenberg0x0 on 2011-10-28
Solution

I have used the popular workaround for the shared objects... (which is supposed to work for Natty).
```
sudo sed 's/\x83\xe8\x03\x83\xf8\x01\x0f\x96\xc0/\x83\xe8\x02\x83\xf8\x01\x0f\x96\xc0/' -i /usr/lib/vmware/lib/libvmware-modconfig.so/libvmware-modconfig.so
sudo sed 's/\x83\xe8\x03\x83\xf8\x01\x0f\x96\xc0/\x83\xe8\x02\x83\xf8\x01\x0f\x96\xc0/' -i /usr/lib/vmware/lib/libvmware-modconfig-console.so/libvmware-modconfig-console.so
```But the patches that go with it didn't worked (vmware2.6.39fixedv3.patch, patch3031vmware741.patch), so I had to grep and edit files with references to kernel version by hand to allow for 3.0.*.

I have no idea why, but the installer creates a  /usr/bin/vmware-installer that is a soft link to  /usr/lib/vmware-installer/2.0/vmware-installer (which doesn't exist). It  will try to register the first module (vmmon) repeatedly. If you ps ax  you'll see a hundred stalled attempts, until it will exit with error.  You'll find a python error (too many open files). But that was easy with:
```
sudo mkdir /usr/lib/vmware-installer/2.0/
sudo ln -s /usr/lib/vmware-installer/4.0/vmware-installer /usr/lib/vmware-installer/2.0/vmware-installer

```It would be nice to have a better support for it on PP.Can't remember the last time I had such a long fight with a program on Ubuntu. 

Regards,
Effenberg

PS: It does complain about the kernel version repeatedly on the first run, but you have the option to ignore and run anyway. It is working fine with a Win_7 64 VirtualBox machine converted from vdi to raw to vmdk, despite the hours I spent on this instead of sleeping.

---

### Post by jfernyhough on 2011-10-29
Grab the patch from this bug report: [https://bugzilla.redhat.com/show_bug.cgi?id=746428](https://bugzilla.redhat.com/show_bug.cgi?id=746428)

It worked for me to get the modules to compile correctly.

---

