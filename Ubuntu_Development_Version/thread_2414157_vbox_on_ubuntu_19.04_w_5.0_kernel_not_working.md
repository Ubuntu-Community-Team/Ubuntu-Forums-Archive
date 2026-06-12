---
title: "vbox on ubuntu 19.04 w/ 5.0 kernel not working"
date: 2019-03-06
forum: Ubuntu Development Version
---

### Post by bmaring on 2019-03-06
When attempting to start a virtual machine, get error:
where: ```
suplibOsInit
``` what: ```
3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed.
``` On linux, open returned ```
ENOENT
```
Running /sbin/vboxconfig gets:
```
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: Look at /var/log/vbox-setup.log to find out what went wrong.

There were problems setting up VirtualBox. To re-start the set-up process, run
/sbin/vboxconfig
as root.
```
This only started occurring after last night's (3/5) kernel update to 5.0. Version of virtualbox is 6.0.

vbox log:
```
Building the main VirtualBox module.
Error building the module:
make V=1 CONFIG_MODULE_SIG= -C /lib/modules/5.0.0-7-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -j4 modules
make[1]: warning: -j4 forced in submake: resetting jobserver mode.
Makefile:203: ================= WARNING ================
Makefile:204: 'SUBDIRS' will be removed after Linux 5.3
Makefile:205: Please use 'M=' or 'KBUILD_EXTMOD' instead
Makefile:206: ==========================================
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f ./scripts/Makefile.build obj=/tmp/vbox.0
gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/8/include -I./arch/x86/include -I./arch/x86/include/generated -I./include -I./arch/x86/include/uapi -I./arch/x86/include/generated/uapi -I./include/uapi -I./include/generated/uapi -include ./include/linux/kconfig.h -Iubuntu/include -include ./include/linux/compiler_types.h -D__KERNEL__ -Wall -Wundef -Werror=strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fshort-wchar -fno-PIE -Werror-implicit-function-declaration -Werror=implicit-int -Wno-format-security -std=gnu89 -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -m64 -falign-jumps=1 -falign-loops=1 -mno-80387 -mno-fp-ret-in-387 -mpreferred-stack-boundary=3 -mskip-rax-setup -mtune=generic -mno-red-zone -mcmodel=kernel -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_SSSE3=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -Wno-sign-compare -fno-asynchronous-unwind-tables -mindirect-branch=thunk-extern -mindirect-branch-register -fno-delete-null-pointer-checks -Wno-frame-address -Wno-format-truncation -Wno-format-overflow -Wno-int-in-bool-context -O2 --param=allow-store-data-races=0 -Wframe-larger-than=1024 -fstack-protector-strong -Wno-unused-but-set-variable -Wno-unused-const-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -fno-var-tracking-assignments -pg -mrecord-mcount -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wvla -Wno-pointer-sign -Wno-stringop-truncation -fno-strict-overflow -fno-merge-all-constants -fmerge-constants -fno-stack-check -fconserve-stack -Werror=date-time -Werror=incompatible-pointer-types -Werror=designated-init -fmacro-prefix-map=./= -Wno-packed-not-aligned -include /tmp/vbox.0/include/VBox/SUPDrvMangling.h -fno-omit-frame-pointer -fno-pie -I/lib/modules/5.0.0-7-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DSUPDRV_WITH_RELEASE_LOGGER -Wno-declaration-after-statement -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_AMD64 -DVBOX_WITH_64_BITS_GUESTS -DMODULE -DKBUILD_BASENAME='"SUPDrv_linux"' -DKBUILD_MODNAME='"vboxdrv"' -c -o /tmp/vbox.0/linux/SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
gcc -Wp,-MD,/tmp/vbox.0/.SUPDrv.o.d -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/8/include -I./arch/x86/include -I./arch/x86/include/generated -I./include -I./arch/x86/include/uapi -I./arch/x86/include/generated/uapi -I./include/uapi -I./include/generated/uapi -include ./include/linux/kconfig.h -Iubuntu/include -include ./include/linux/compiler_types.h -D__KERNEL__ -Wall -Wundef -Werror=strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fshort-wchar -fno-PIE -Werror-implicit-function-declaration -Werror=implicit-int -Wno-format-security -std=gnu89 -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -m64 -falign-jumps=1 -falign-loops=1 -mno-80387 -mno-fp-ret-in-387 -mpreferred-stack-boundary=3 -mskip-rax-setup -mtune=generic -mno-red-zone -mcmodel=kernel -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_SSSE3=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -Wno-sign-compare -fno-asynchronous-unwind-tables -mindirect-branch=thunk-extern -mindirect-branch-register -fno-delete-null-pointer-checks -Wno-frame-address -Wno-format-truncation -Wno-format-overflow -Wno-int-in-bool-context -O2 --param=allow-store-data-races=0 -Wframe-larger-than=1024 -fstack-protector-strong -Wno-unused-but-set-variable -Wno-unused-const-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -fno-var-tracking-assignments -pg -mrecord-mcount -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wvla -Wno-pointer-sign -Wno-stringop-truncation -fno-strict-overflow -fno-merge-all-constants -fmerge-constants -fno-stack-check -fconserve-stack -Werror=date-time -Werror=incompatible-pointer-types -Werror=designated-init -fmacro-prefix-map=./= -Wno-packed-not-aligned -include /tmp/vbox.0/include/VBox/SUPDrvMangling.h -fno-omit-frame-pointer -fno-pie -I/lib/modules/5.0.0-7-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DSUPDRV_WITH_RELEASE_LOGGER -Wno-declaration-after-statement -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_AMD64 -DVBOX_WITH_64_BITS_GUESTS -DMODULE -DKBUILD_BASENAME='"SUPDrv"' -DKBUILD_MODNAME='"vboxdrv"' -c -o /tmp/vbox.0/SUPDrv.o /tmp/vbox.0/SUPDrv.c
```
apportl,log:
```
ERROR: apport (pid 13473) Wed Mar  6 09:10:52 2019: called for pid 9722, signal 6, core limit 0, dump mode 2
ERROR: apport (pid 13473) Wed Mar  6 09:10:52 2019: not creating core for pid with dump mode of 2
ERROR: apport (pid 13473) Wed Mar  6 09:10:52 2019: executable: /usr/lib/virtualbox/VirtualBoxVM (command line "/usr/lib/virtualbox/VirtualBoxVM --comment Win10 --startvm 05eb6768-42ba-4ba9-8e96-ee4a9b4033ed --no-startvm-errormsgbox")
ERROR: apport (pid 13473) Wed Mar  6 09:10:52 2019: debug: session gdbus call: (true,)


ERROR: apport (pid 13473) Wed Mar  6 09:10:56 2019: wrote report /var/crash/_usr_lib_virtualbox_VirtualBoxVM.0.crash
ERROR: apport (pid 13480) Wed Mar  6 09:10:59 2019: called for pid 9705, signal 6, core limit 0, dump mode 2
ERROR: apport (pid 13480) Wed Mar  6 09:10:59 2019: not creating core for pid with dump mode of 2
ERROR: apport (pid 13480) Wed Mar  6 09:10:59 2019: executable: /usr/lib/virtualbox/VirtualBoxVM (command line "/usr/lib/virtualbox/VirtualBoxVM --comment Win10 --startvm 05eb6768-42ba-4ba9-8e96-ee4a9b4033ed --no-startvm-errormsgbox")
ERROR: apport (pid 13480) Wed Mar  6 09:10:59 2019: debug: session gdbus call: (true,)


ERROR: apport (pid 13480) Wed Mar  6 09:10:59 2019: apport: report /var/crash/_usr_lib_virtualbox_VirtualBoxVM.0.crash already exists and unseen, doing nothing to avoid disk usage DoS
```

---

### Post by DuckHook on 2019-03-06
Massive walls of text will discourage potential helpers from reading your post.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. Also, please refrain from using anything other than standard fonts and formatting, as odd colours and styles make the output very hard to read.

---

### Post by #&amp;thj^% on 2019-03-06
I'm sure you are aware that the gist of the messages you're getting is that the kernel version you're using,(5.0.0-7-generic) is not supported by the version of the VirtualBox tools you're trying to utilize.

To that end, you should go back to the supported kernel in order to use the VBox tools.
Also might be useful to check "/var/crash/_usr_lib_virtualbox_VirtualBoxVM.0.crash" for more clues
EDIT: You could also try:
```
sudo apt autoremove virtualbox-dkms
sudo apt install build-essential linux-headers-`uname -r` dkms virtualbox-dkms
```

---

### Post by bmaring on 2019-03-06
Update to Virtualbox 6.0.4 solved the problem.  Thanks

---

