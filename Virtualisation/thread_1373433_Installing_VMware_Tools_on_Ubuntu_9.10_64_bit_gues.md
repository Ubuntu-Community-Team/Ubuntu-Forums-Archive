---
title: "Installing VMware Tools on Ubuntu 9.10 64 bit guest"
date: 2010-01-05
forum: Virtualisation
---

### Post by n00b2ubuntu on 2010-01-05
I am trying to install vmware tools on an Ubuntu 9.10 64bit guest. True to form it simply doesn't work.

Running ./vmware-install.pl it gets to the bit where it runs vmware-config-tools.pl

I get the "None of the pre-built <module name> modules for VMware Tools is suitable for your running kernel" message

It then fails to build every single module e.g.

```
Building the vmmemctl module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config15/vmmemctl-only'
make -C /lib/modules/2.6.31-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /tmp/vmware-config15/vmmemctl-only/backdoorGcc64.o
In file included from /tmp/vmware-config15/vmmemctl-only/backdoor.h:29,
                 from /tmp/vmware-config15/vmmemctl-only/backdoorGcc64.c:38:
/tmp/vmware-config15/vmmemctl-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
  CC [M]  /tmp/vmware-config15/vmmemctl-only/os.o
In file included from /tmp/vmware-config15/vmmemctl-only/os.c:51:
/tmp/vmware-config15/vmmemctl-only/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
make[2]: *** [/tmp/vmware-config15/vmmemctl-only/os.o] Error 1
make[1]: *** [_module_/tmp/vmware-config15/vmmemctl-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [vmmemctl.ko] Error 2
make: Leaving directory `/tmp/vmware-config15/vmmemctl-only'
Unable to build the vmmemctl module.
```

I don't think I've ever managed to get vmware tools to install on Ubuntu without seeking out fixes, patch files etc :(

Any assistance greatfully received.

Alex

---

### Post by n00b2ubuntu on 2010-01-05
Ok, I think I have had some success following this guide:

[http://langui.sh/2009/10/05/ubuntu-9-10-in-vmware/](http://langui.sh/2009/10/05/ubuntu-9-10-in-vmware/)



Then, after adding a sound device I had the stuttering audio problem, fixed by following the bottom part of this guide:

[http://www.linwik.com/wiki/installing+vmware+tools+in+ubuntu+9.10](http://www.linwik.com/wiki/installing+vmware+tools+in+ubuntu+9.10)

```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui esound esound-clients esound-common libesd-alsa0 gnome-alsamixer

```

---

### Post by HDave on 2010-01-07
Were you running Fusion, Workstation, or Vmware Server when you got it to work?

Edit: Indeed the instruction do work on my installation of VMware Server 2 -- however through the use of the open-vm-tools package, I have apparently lost the copy/paste and screen resizing functionality.  Any ideas there?

---

