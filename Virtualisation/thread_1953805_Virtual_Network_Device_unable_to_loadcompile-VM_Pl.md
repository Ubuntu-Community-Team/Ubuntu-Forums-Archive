---
title: "Virtual Network Device unable to load/compile-VM Player 4.0.2 in Ubuntu 12.04 Beta 2"
date: 2012-04-06
forum: Virtualisation
---

### Post by caveman7 on 2012-04-06
Hello all. I'm trying to install VM Player 4.0.2 (the newest version as of 7 April 2012) on Ubuntu 12.04 Precise Pangolin Beta 2.

After successfully installing, I tried running and the following window appears:

[IMG]http://i790.photobucket.com/albums/yy183/caveman712/Troubleshoot/Screenshotfrom2012-04-0709-35-21.png[/IMG]

I clicked on **Install** and entered my password. However, not all modules can be compiled. The **Virtual Network Device** fails to be compiled and hence VM Player cannot be started.

[IMG]http://i790.photobucket.com/albums/yy183/caveman712/Troubleshoot/Screenshotfrom2012-04-0709-37-05.png[/IMG]

Here is the contents of the log file.

```

2012-04-07T09:35:53.980+07:00| vthread-3| I120: Log for VMware Workstation pid=8116 version=8.0.2 build=build-591240 option=Release
2012-04-07T09:35:53.980+07:00| vthread-3| I120: The process is 32-bit.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Host is Linux 3.2.0-22-generic-pae Ubuntu precise (development branch)
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Msg_Reset:
2012-04-07T09:35:53.980+07:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: ----------------------------------------
2012-04-07T09:35:53.980+07:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Msg_Reset:
2012-04-07T09:35:53.980+07:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: ----------------------------------------
2012-04-07T09:35:53.980+07:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Msg_Reset:
2012-04-07T09:35:53.980+07:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: ----------------------------------------
2012-04-07T09:35:53.980+07:00| vthread-3| I120: PREF Failed to load user preferences.
2012-04-07T09:35:53.980+07:00| vthread-3| W110: Logging to /tmp/vmware-root/modconfig-8116.log
2012-04-07T09:35:54.067+07:00| vthread-3| I120: modconf query interface initialized
2012-04-07T09:35:54.068+07:00| vthread-3| I120: modconf library initialized
2012-04-07T09:35:54.100+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.107+07:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.107+07:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-07T09:35:54.107+07:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-07T09:35:54.107+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.111+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.120+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.153+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:54.153+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.157+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.165+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.184+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:54.201+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.203+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.205+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.207+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.209+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.221+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.223+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.225+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.227+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.229+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.230+07:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.230+07:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-07T09:35:54.230+07:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-07T09:35:54.230+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.232+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.238+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.255+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:54.268+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.270+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.272+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.274+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.276+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.277+07:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.277+07:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-07T09:35:54.277+07:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-07T09:35:54.277+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.278+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.283+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.301+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:54.340+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.342+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.344+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.345+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.347+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:56.608+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:56.608+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:56.610+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:56.625+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:56.644+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:56.644+07:00| vthread-3| I120: Building module vmmon.
2012-04-07T09:35:56.644+07:00| vthread-3| I120: Extracting the sources of the vmmon module.
2012-04-07T09:35:56.701+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:01.552+07:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.2.0-22-generic-pae/misc.
2012-04-07T09:36:01.553+07:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-22-generic-pae/misc/vmmon.ko
2012-04-07T09:36:14.695+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:36:14.695+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:36:14.697+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:14.814+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:14.840+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:36:14.840+07:00| vthread-3| I120: Building module vmnet.
2012-04-07T09:36:14.841+07:00| vthread-3| I120: Extracting the sources of the vmnet module.
2012-04-07T09:36:14.881+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:17.706+07:00| vthread-3| I120: Failed to compile module vmnet!
2012-04-07T09:36:17.715+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:36:17.716+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:36:17.720+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:17.778+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:17.813+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:36:17.813+07:00| vthread-3| I120: Building module vmblock.
2012-04-07T09:36:17.814+07:00| vthread-3| I120: Extracting the sources of the vmblock module.
2012-04-07T09:36:17.841+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:20.702+07:00| vthread-3| I120: Installing module vmblock from /tmp/vmware-root/modules/vmblock.o to /lib/modules/3.2.0-22-generic-pae/misc.
2012-04-07T09:36:20.703+07:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-22-generic-pae/misc/vmblock.ko
2012-04-07T09:36:22.254+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:36:22.254+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:36:22.256+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:22.263+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:22.287+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:36:22.287+07:00| vthread-3| I120: Building module vmci.
2012-04-07T09:36:22.287+07:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-04-07T09:36:22.387+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:25.008+07:00| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.2.0-22-generic-pae/misc.
2012-04-07T09:36:25.009+07:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-22-generic-pae/misc/vmci.ko
2012-04-07T09:36:26.338+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:36:26.338+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:36:26.340+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:26.347+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:26.369+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:36:26.369+07:00| vthread-3| I120: Building module vmci.
2012-04-07T09:36:26.369+07:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-04-07T09:36:26.377+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:29.139+07:00| vthread-3| I120: Building module vsock.
2012-04-07T09:36:29.139+07:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-04-07T09:36:29.408+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:31.965+07:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-22-generic-pae/misc.
2012-04-07T09:36:31.965+07:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-22-generic-pae/misc/vsock.ko

```

Can anybody help me resolve this issue? Any help will be greatly appreciated.

**UPDATE**
Here's the solution: [http://communities.vmware.com/message/1902218#1902218](http://communities.vmware.com/message/1902218#1902218)

Basically you just download the file and run the .sh script (with root privilege). For convenience, I've also attached the script in this post (vmware802fixlinux320.tar.gz)

---

### Post by caveman7 on 2012-04-07
can anybody help me?:confused:

---

### Post by hughperkins on 2012-04-08
Same problem here :(  I was rather hoping to find someone had already figured it out :p

---

### Post by hughperkins on 2012-04-08
Here is the solution that worked for me:

[http://communities.vmware.com/message/1902218#1902218](http://communities.vmware.com/message/1902218#1902218)

---

### Post by caveman7 on 2012-04-08
> **hughperkins said:**
> Here is the solution that worked for me:

[http://communities.vmware.com/message/1902218#1902218](http://communities.vmware.com/message/1902218#1902218)

works for me too!! thanks a lot :)

---

### Post by ai4g on 2012-04-10
> **caveman7 said:**
> works for me too!! thanks a lot :)

Fixed mine, as well.  Thanks!

---

### Post by Alan_x on 2012-04-11
Just tried it. Didn't work for me. The error message:

patch-modules_3.2.0.sh: 27: [: player4.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: player4.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. 

Yet, I'm using this Player 4.0.2., downloaded from VMware:

VMware-Player-4.0.2-591240.x86_64.bundle

Any thoughts?

---

### Post by dcstar on 2012-04-12
> **Alan_x said:**
> Just tried it. Didn't work for me. The error message:

patch-modules_3.2.0.sh: 27: [: player4.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: player4.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. 

Yet, I'm using this Player 4.0.2., downloaded from VMware:

VMware-Player-4.0.2-591240.x86_64.bundle

Any thoughts?

So you have **installed** VMware Player and **then** run the patch?

---

### Post by Alan_x on 2012-04-12
Yes, I installed the Player and then ran the patch. Turns out, I didn't know to make the patch executable. Once I did that, the patch worked. VMWare is now running with no apparent problems.

Thanks.

---

### Post by MrAwanish on 2012-04-14
this patch is not working see message like this



patch-modules_3.2.0.sh: 27: [: workstation8.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: workstation8.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. Exiting


have any solution please..............

---

### Post by MrAwanish on 2012-04-14
this patch is not working see message like this



patch-modules_3.2.0.sh: 27: [: workstation8.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: workstation8.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. Exiting


have any solution please..............

---

### Post by MrAwanish on 2012-04-14
> **caveman7 said:**
> Hello all. I'm trying to install VM Player 4.0.2 (the newest version as of 7 April 2012) on Ubuntu 12.04 Precise Pangolin Beta 2.

After successfully installing, I tried running and the following window appears:

[IMG]http://i790.photobucket.com/albums/yy183/caveman712/Troubleshoot/Screenshotfrom2012-04-0709-35-21.png[/IMG]

I clicked on **Install** and entered my password. However, not all modules can be compiled. The **Virtual Network Device** fails to be compiled and hence VM Player cannot be started.

[IMG]http://i790.photobucket.com/albums/yy183/caveman712/Troubleshoot/Screenshotfrom2012-04-0709-37-05.png[/IMG]

Here is the contents of the log file.

```

2012-04-07T09:35:53.980+07:00| vthread-3| I120: Log for VMware Workstation pid=8116 version=8.0.2 build=build-591240 option=Release
2012-04-07T09:35:53.980+07:00| vthread-3| I120: The process is 32-bit.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Host is Linux 3.2.0-22-generic-pae Ubuntu precise (development branch)
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Msg_Reset:
2012-04-07T09:35:53.980+07:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: ----------------------------------------
2012-04-07T09:35:53.980+07:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Msg_Reset:
2012-04-07T09:35:53.980+07:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: ----------------------------------------
2012-04-07T09:35:53.980+07:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: Msg_Reset:
2012-04-07T09:35:53.980+07:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2012-04-07T09:35:53.980+07:00| vthread-3| I120: ----------------------------------------
2012-04-07T09:35:53.980+07:00| vthread-3| I120: PREF Failed to load user preferences.
2012-04-07T09:35:53.980+07:00| vthread-3| W110: Logging to /tmp/vmware-root/modconfig-8116.log
2012-04-07T09:35:54.067+07:00| vthread-3| I120: modconf query interface initialized
2012-04-07T09:35:54.068+07:00| vthread-3| I120: modconf library initialized
2012-04-07T09:35:54.100+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.107+07:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.107+07:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-07T09:35:54.107+07:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-07T09:35:54.107+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.111+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.120+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.153+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:54.153+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.157+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.165+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.184+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:54.201+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.203+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.205+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.207+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.209+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.221+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.223+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.225+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.227+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.229+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.230+07:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.230+07:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-07T09:35:54.230+07:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-07T09:35:54.230+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.232+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.238+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.255+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:54.268+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.270+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.272+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.274+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.276+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.277+07:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.277+07:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-04-07T09:35:54.277+07:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-04-07T09:35:54.277+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:54.278+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.283+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:54.301+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:54.340+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.342+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.344+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.345+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:54.347+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:56.608+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:35:56.608+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:35:56.610+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:56.625+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:35:56.644+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:35:56.644+07:00| vthread-3| I120: Building module vmmon.
2012-04-07T09:35:56.644+07:00| vthread-3| I120: Extracting the sources of the vmmon module.
2012-04-07T09:35:56.701+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:01.552+07:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.2.0-22-generic-pae/misc.
2012-04-07T09:36:01.553+07:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-22-generic-pae/misc/vmmon.ko
2012-04-07T09:36:14.695+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:36:14.695+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:36:14.697+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:14.814+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:14.840+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:36:14.840+07:00| vthread-3| I120: Building module vmnet.
2012-04-07T09:36:14.841+07:00| vthread-3| I120: Extracting the sources of the vmnet module.
2012-04-07T09:36:14.881+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:17.706+07:00| vthread-3| I120: Failed to compile module vmnet!
2012-04-07T09:36:17.715+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:36:17.716+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:36:17.720+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:17.778+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:17.813+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:36:17.813+07:00| vthread-3| I120: Building module vmblock.
2012-04-07T09:36:17.814+07:00| vthread-3| I120: Extracting the sources of the vmblock module.
2012-04-07T09:36:17.841+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:20.702+07:00| vthread-3| I120: Installing module vmblock from /tmp/vmware-root/modules/vmblock.o to /lib/modules/3.2.0-22-generic-pae/misc.
2012-04-07T09:36:20.703+07:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-22-generic-pae/misc/vmblock.ko
2012-04-07T09:36:22.254+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:36:22.254+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:36:22.256+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:22.263+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:22.287+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:36:22.287+07:00| vthread-3| I120: Building module vmci.
2012-04-07T09:36:22.287+07:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-04-07T09:36:22.387+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:25.008+07:00| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.2.0-22-generic-pae/misc.
2012-04-07T09:36:25.009+07:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-22-generic-pae/misc/vmci.ko
2012-04-07T09:36:26.338+07:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-22-generic-pae.
2012-04-07T09:36:26.338+07:00| vthread-3| I120: Validating path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae
2012-04-07T09:36:26.340+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:26.347+07:00| vthread-3| I120: Your GCC version: 4.6
2012-04-07T09:36:26.369+07:00| vthread-3| I120: Header path /lib/modules/3.2.0-22-generic-pae/build/include for kernel release 3.2.0-22-generic-pae is valid.
2012-04-07T09:36:26.369+07:00| vthread-3| I120: Building module vmci.
2012-04-07T09:36:26.369+07:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-04-07T09:36:26.377+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:29.139+07:00| vthread-3| I120: Building module vsock.
2012-04-07T09:36:29.139+07:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-04-07T09:36:29.408+07:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-22-generic-pae/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-04-07T09:36:31.965+07:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-22-generic-pae/misc.
2012-04-07T09:36:31.965+07:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-22-generic-pae/misc/vsock.ko

```

Can anybody help me resolve this issue? Any help will be greatly appreciated.

**UPDATE**
Here's the solution: [http://communities.vmware.com/message/1902218#1902218](http://communities.vmware.com/message/1902218#1902218)

Basically you just download the file and run the .sh script (with root privilege). For convenience, I've also attached the script in this post (vmware802fixlinux320.tar.gz)





this patch is not working see message like this



patch-modules_3.2.0.sh: 27: [: workstation8.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: workstation8.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. Exiting


have any solution please..............

---

### Post by caveman7 on 2012-04-14
> **MrAwanish said:**
> this patch is not working see message like this



patch-modules_3.2.0.sh: 27: [: workstation8.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: workstation8.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. Exiting


have any solution please..............

you don't have to post your cry for help multiple times in a row..

try placing the patches in your /home/<username> directory and run this:

sudo ./patch-modules_3.2.0.sh

it should work.

---

### Post by Apocalypse_X on 2012-04-20
Patch worked like a charm, I just needed to do a apt-get install patch before running the script. 10x a lot!

---

### Post by caveman7 on 2012-04-26
> **Apocalypse_X said:**
> Patch worked like a charm, I just needed to do a apt-get install patch before running the script. 10x a lot!

glad to help :D

---

### Post by nvjopsddhapnv on 2012-04-26
> **hughperkins said:**
> Here is the solution that worked for me:

[http://communities.vmware.com/message/1902218#1902218](http://communities.vmware.com/message/1902218#1902218)

Thanks a lot. It indeed works for me as well.

---

### Post by bhavin23 on 2012-04-29
Greate Help!!!!!!!!!!!!!!!!!!!

Thanks A lOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOt:guitar:

I was struggling with same problem, Got it solved with help of you guys!!!!.

---

### Post by criadoperez on 2012-04-29
The patch worked for me. Thanks a lot!!

---

### Post by TheOneEyedMan on 2012-04-29
I guess I ran into this problem in a previous upgrade process because running this gave me an error concerning a patch already existing. I deleted /usr/vmware/modules/source/.patched and then tried again. Everything worked smoothly after that.

---

### Post by chrisblueearth on 2012-05-03
I'm having the same problem with the script:

> chris@chris-sys76:~/bin$ sudo sh patch-modules_3.2.0.sh 
patch-modules_3.2.0.sh: 27: [: workstation8.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: workstation8.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. Exiting
chris@chris-sys76:~/bin$ vmware-installer -l
Product Name         Product Version     
==================== ====================
vmware-workstation   8.0.2.591240   

---

### Post by ramouz on 2012-05-03
How to force the patch to work
------------------------------

It seems the version checking in the patch failed on my installation (Ubuntu 12.04 with VMWare player 4.0.2) - with similar messages to what I am seeing above

**********
patch-modules_3.2.0.sh: 27: [: player4.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: player4.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. Exiting
**********

Here is what I did, proceed with caution:
-----------------------------------------

1. Open patch-modules_3.2.0.sh in your favorite text editor
2. Comment out lines 27,28,29 (i.e. add '#' at the beginning of the line)

# [ "$vmver" == "workstation$vmreqver" ] && product="VMWare WorkStation"
# [ "$vmver" == "player$plreqver" ] && product="VMWare Player"
# [ -z "$product" ] && error "Sorry, this script is only for VMWare WorkStation $vmreqver or VMWare Player $plreqver"


3. If you are running VMWare Workstation, you likely need to add this line after the above lines (it worked right away on VMWare Player away at my end so I am guessing here, take it off if it fails):
product="VMWare WorkStation"

3. Run the patch
sudo sh patch-modules_3.2.0.sh



To the patch developer: 
-----------------------
Can you take a look at this and see why the version check failed even though the patch is functional? Thank you very much for this patch .. I would have to roll back to 11 (don't even know if it's possible)

---

### Post by djrobthaman on 2012-05-03
I installed vmware player 4.0.2 and had the same problem as the OP. The patch fixed it all up. Just updated to 4.0.3 and back to square one but now the patch won't execute and gives an error message saying it is specifically for 4.0.2.

Does anyone know where I can find a similar patch for 4.0.3?

Thanks

---

### Post by traditionalist on 2012-05-04
> **ramouz said:**
> How to force the patch to work
------------------------------

It seems the version checking in the patch failed on my installation (Ubuntu 12.04 with VMWare player 4.0.2) - with similar messages to what I am seeing above

**********
patch-modules_3.2.0.sh: 27: [: player4.0.2: unexpected operator
patch-modules_3.2.0.sh: 28: [: player4.0.2: unexpected operator
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.2. Exiting
**********

Here is what I did, proceed with caution:
-----------------------------------------

1. Open patch-modules_3.2.0.sh in your favorite text editor
2. Comment out lines 27,28,29 (i.e. add '#' at the beginning of the line)

# [ "$vmver" == "workstation$vmreqver" ] && product="VMWare WorkStation"
# [ "$vmver" == "player$plreqver" ] && product="VMWare Player"
# [ -z "$product" ] && error "Sorry, this script is only for VMWare WorkStation $vmreqver or VMWare Player $plreqver"


3. If you are running VMWare Workstation, you likely need to add this line after the above lines (it worked right away on VMWare Player away at my end so I am guessing here, take it off if it fails):
product="VMWare WorkStation"

3. Run the patch
sudo sh patch-modules_3.2.0.sh



To the patch developer: 
-----------------------
Can you take a look at this and see why the version check failed even though the patch is functional? Thank you very much for this patch .. I would have to roll back to 11 (don't even know if it's possible)

Brilliant!  Thanks very much indeed, that worked for me on UBUNTU 12.04 

Regards...Trad

---

### Post by traditionalist on 2012-05-05
Hmm...worked once.  I had to reinstall the complete system, and I can no longer get it to work.  I have been trying all sorts of things for hours.

Any ideas?

Regards....Trad

---

### Post by traditionalist on 2012-05-05
OK, I give up. Five days, seven installs, and the system breaks after running for a while.  Very odd behaviour as well. things that worked once wont work again even on a new install.  I think I will reluctantly go back to Windows.  

This stuff would be great if it worked, but as it doesn't...................... I haven't really much option.

Regards....Trad.

---

### Post by tajreed on 2012-05-05
I've been down the same route. Try Virtual Box, much, much simpler set-up. and it works. I've been using it for several years in Ubuntu with WinXP as guest to run one windows program that I need occasionally.

I've yet to get VMware to work.

---

### Post by traditionalist on 2012-05-05
Installed the whole system new. Did exactly the same thing again. This time it worked!  I am very puzzled indeed, but I am happy it is working.  I am getting fed up of reinstalling the whole system.  Any ideas on a good backup system?  Those I have tried don't work.

Regards....Trad

---

### Post by djrobthaman on 2012-05-05
For those of you having issues running the patch on a reinstall, there's a hidden file that the patch creates somewhere that you have to delete first before you can do so. I had to do this when I downgraded from vmplayer 4.0.3 to 4.0.2

I can't remember exactly where the hidden file was but there was an error message when the patch wouldn't apply that helped me find it.

---

### Post by dcstar on 2012-05-06
> **ramouz said:**
> 
..........
To the patch developer: 
-----------------------
Can you take a look at this and see why the version check failed even though the patch is functional? Thank you very much for this patch .. I would have to roll back to 11 (don't even know if it's possible)

How on earth is a patch **posted by someone in the VMware forums** going to affected by a post in the Ubuntu forums?

The proper solution is to wait until VMware make their products 12.04 compatible, and that does not happen 5 minutes after Ubuntu release 12.04 (or any new version).

---

### Post by traditionalist on 2012-05-06
> **djrobthaman said:**
> For those of you having issues running the patch on a reinstall, there's a hidden file that the patch creates somewhere that you have to delete first before you can do so. I had to do this when I downgraded from vmplayer 4.0.3 to 4.0.2

I can't remember exactly where the hidden file was but there was an error message when the patch wouldn't apply that helped me find it.

The only hidden file I could find was the backup after editing the modules file. I wiped the disk completely before reinstalls and did everything new.

Anyway, this time it worked, and the system appears to be stable.  I have spent a lot of time tweaking various things as some are still not 100% fit with 12.04 but I am happy with results.  As long as I can run the two essential Windows 7 64 programs I have in the VMware player, and the rest of the system stays stable, ( which it now seems to), I am very pleased with the system.

Some things are unnecessarily difficult to accomplish and as a "newbie" one can lose heart.

Also, I found a reliable backup system,  Remastersys;

[http://www.remastersys.com/](http://www.remastersys.com/)

Regards...Trad

---

### Post by traditionalist on 2012-05-07
OK. System is finally running stable, ( On the current stable final release of 12.04). I removed "unity" altogether and use "Gnome Classic". Since doing this no problems with logins or system breaks. I have installed a lot of stuff and am extremely pleased with the results.

Since the VMware player now runs fine I don't need to try anything else.

Thanks to those who provided the solution and patch.

Regards...Trad

---

### Post by tawfekov on 2012-05-14
Dude you saved my day , vmware player now running on 12.04 ,

my version number is **4.0.3 build-703057** 

 BIG THANK YOU

---

### Post by dcstar on 2012-05-16
> **djrobthaman said:**
> I installed vmware player 4.0.2 and had the same problem as the OP. The patch fixed it all up. Just updated to 4.0.3 and back to square one but now the patch won't execute and gives an error message saying it is specifically for 4.0.2.

**Does anyone know where I can find a similar patch for 4.0.3?**

```
gedit patch-modules_3.2.0.sh 
```
Change the line to:
```
plreqver=**4.0.3**
```
Then do this if you are upgrading from 4.0.2:
```
sudo rm /usr/lib/vmware/modules/source/.patched
```
Then install the patch:
```
sudo ./patch-modules_3.2.0.sh
```

---

### Post by edgicat on 2012-05-19
> **dcstar said:**
> ```
gedit patch-modules_3.2.0.sh 
```
Change the line to:
```
plreqver=**4.0.3**
```
Then do this if you are upgrading from 4.0.2:
```
sudo rm /usr/lib/vmware/modules/source/.patched
```
Then install the patch:
```
sudo ./patch-modules_3.2.0.sh
```

I have the same problem after doing a fresh install of ubuntu 12.04 64bit and downloading a vmplayer 4.03.  I've tried changing "plreqver=4.0.2" to "plreqver=4.0.3" but i get an error on line 42 "patch: command not found".

Any ideas

thanks

---

### Post by helotbc on 2012-05-19
I also was getting the error:

./patch-modules_3.2.0.sh: [COLOR="Red"]line 42: patch: command not found[/COLOR]

As mentioned in a previous post, you need to insta ll the "patch" utility:

[COLOR="red"]sudo apt-get install patch[/COLOR]

Once I had the "patch" utility, and made the modifications to the patch-modules_3.2.0.sh file (on lines 27, 28, 28), as mentioned earlier, the vmware patch installed fine and I can run vmware player.

Thanks for all the help and suggestions,
Brendan

---

### Post by edgicat on 2012-05-20
> **helotbc said:**
> I also was getting the error:

./patch-modules_3.2.0.sh: [COLOR="Red"]line 42: patch: command not found[/COLOR]

As mentioned in a previous post, you need to insta ll the "patch" utility:

[COLOR="red"]sudo apt-get install patch[/COLOR]

Once I had the "patch" utility, and made the modifications to the patch-modules_3.2.0.sh file (on lines 27, 28, 28), as mentioned earlier, the vmware patch installed fine and I can run vmware player.

Thanks for all the help and suggestions,
Brendan

Thanks, worked like a charm

---

### Post by buzzbeebara on 2012-05-21
> **edgicat said:**
> Thanks, worked like a charm

same here, worked for me. ty all!

---

### Post by jujumax on 2012-05-31
This one really worked for me VMware player 4.0.3 and Ubuntu 12.04 LTS 

[http://askubuntu.com/questions/130937/vmware-player-4-0-3-on-ubuntu-12-04](http://askubuntu.com/questions/130937/vmware-player-4-0-3-on-ubuntu-12-04)

All the best

J

---

### Post by dcstar on 2012-06-01
> **jujumax said:**
> This one really worked for me VMware player 4.0.3 and Ubuntu 12.04 LTS 
........

Which is exactly what is already in this thread, so why post it?

---

### Post by sffvba[e0rt on 2012-06-01
*Thread **closed**.*


404

---

