---
title: "Low resolution and guest addition errors"
date: 2019-10-03
forum: Virtualisation
---

### Post by danielsender on 2019-10-03
My host is 18.04.3 and the guest is Centos 7. After the last updates in which VirtualBox was part of those I cannot go back to the higher resolution screen for the guest system. I re-installed the guest-additions and it gave me a bunch of errors. I was wondering if there is fix for this or is a bug in the GA. Please see the attached log file. Thanks.

```
Building the main Guest Additions module for kernel 3.10.0-1062.1.1.el7.x86_64.Building the shared folder support module.
Building the graphics driver module.
Error building the module.  Build output follows.
make V=1 CONFIG_MODULE_SIG= -C /lib/modules/3.10.0-1062.1.1.el7.x86_64/build M=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -j4 modules
make[1]: warning: -jN forced in submake: disabling jobserver mode.
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
echo >&2;                            \
echo >&2 "  ERROR: Kernel configuration is invalid.";        \
echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
echo >&2 ;                            \
/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/.hgsmi_base.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/3.10.0-1062.1.1.el7.x86_64/build/include -I/tmp/vbox.0 -Iinclude/drm -D__KERNEL__ -DMODULE  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(hgsmi_base)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_hgsmi_base.o /tmp/vbox.0/hgsmi_base.c
  gcc -Wp,-MD,/tmp/vbox.0/.modesetting.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/3.10.0-1062.1.1.el7.x86_64/build/include -I/tmp/vbox.0 -Iinclude/drm -D__KERNEL__ -DMODULE  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(modesetting)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_modesetting.o /tmp/vbox.0/modesetting.c
  gcc -Wp,-MD,/tmp/vbox.0/.vbox_drv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/3.10.0-1062.1.1.el7.x86_64/build/include -I/tmp/vbox.0 -Iinclude/drm -D__KERNEL__ -DMODULE  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vbox_drv)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_vbox_drv.o /tmp/vbox.0/vbox_drv.c
  gcc -Wp,-MD,/tmp/vbox.0/.vbox_fb.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/3.10.0-1062.1.1.el7.x86_64/build/include -I/tmp/vbox.0 -Iinclude/drm -D__KERNEL__ -DMODULE  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vbox_fb)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_vbox_fb.o /tmp/vbox.0/vbox_fb.c
In file included from /tmp/vbox.0/vboxvideo_guest.h:32:0,
                 from /tmp/vbox.0/modesetting.c:27:
/tmp/vbox.0/vbox_drv.h:178:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:179:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
In file included from /tmp/vbox.0/vbox_fb.c:31:0:
/tmp/vbox.0/vbox_drv.h:178:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:179:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
In file included from /tmp/vbox.0/hgsmi_base.c:27:0:
/tmp/vbox.0/vbox_drv.h:178:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:179:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
In file included from /tmp/vbox.0/vbox_drv.c:31:0:
/tmp/vbox.0/vbox_drv.h:178:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:179:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
make[2]: *** [/tmp/vbox.0/hgsmi_base.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [/tmp/vbox.0/modesetting.o] Error 1
make[2]: *** [/tmp/vbox.0/vbox_fb.o] Error 1
make[2]: *** [/tmp/vbox.0/vbox_drv.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxvideo] Error 2
```

---

### Post by danielsender on 2019-10-04
Anyone?

---

### Post by ajgreeny on 2019-10-04
Do you have the same version of VBox and the GA installed?

They must be the same version for the GA to work properly, and of course the GA must be installed in the guest after booting it, usually by going to Devices in the VB menu and choosing "Insert Guest Additions CD Image" then opening the CD image in the guest file manager and running the VBoxLinuxAdditions.run shell script.

---

### Post by danielsender on 2019-10-04
> **ajgreeny said:**
> Do you have the same version of VBox and the GA installed?

They must be the same version for the GA to work properly, and of course the GA must be installed in the guest after booting it, usually by going to Devices in the VB menu and choosing "Insert Guest Additions CD Image" then opening the CD image in the guest file manager and running the VBoxLinuxAdditions.run shell script.

They are the same versions, and all the errors occur during installation of the GA in the guest - yesterday I made an experiment: on another machine also running 18.04.3 but with a windows10 guest, I installed the GA in the windows10 without any problems - wouldn't be the case of something with the Centos kernel that is not working properly?

---

### Post by danielsender on 2019-10-05
any ideas?

---

### Post by cruzer001 on 2019-10-05
You say vBox worked till the latest round of updates so your running the repository version.  Go to the site and install 6.0, thats what I prefer to run.

Have you tried reinstalling current vBox?

Also consider running qemu/kvm. You can have both VMs installed, but only one can be ran at a time.
```
sudo apt install qemu-kvm libvirt-bin bridge-utils virt-manager
```
And your ready to load guest.

---

### Post by ajgreeny on 2019-10-05
A sudden thought; do you have the kernel headers installed in your guest CentOS distro? They are needed, I think, to build the many kernel modules in the guest Linux system.

---

### Post by danielsender on 2019-10-05
Yes, I have the headers installed. I'm a bit hesitant to use the Oracle version because they have very frequent updates and sometimes I'm not available to install the GA and the person using this VM doesn't like to go through that. Besides, I would like to understand what the problem is.

---

### Post by danielsender on 2019-10-05
Sorry, I made a mistake: I didn't have the headers installed in the guest. I have done it now but the problem remains. Here is the vboxadd-setup.log file created after the last attempt.
```
Building the main Guest Additions module for kernel 3.10.0-1062.1.1.el7.x86_64.Building the shared folder support module.
Building the graphics driver module.
Error building the module.  Build output follows.
make V=1 CONFIG_MODULE_SIG= -C /lib/modules/3.10.0-1062.1.1.el7.x86_64/build M=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -j4 modules
make[1]: warning: -jN forced in submake: disabling jobserver mode.
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
echo >&2;                            \
echo >&2 "  ERROR: Kernel configuration is invalid.";        \
echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
echo >&2 ;                            \
/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/.hgsmi_base.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/3.10.0-1062.1.1.el7.x86_64/build/include -I/tmp/vbox.0 -Iinclude/drm -D__KERNEL__ -DMODULE  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(hgsmi_base)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_hgsmi_base.o /tmp/vbox.0/hgsmi_base.c
  gcc -Wp,-MD,/tmp/vbox.0/.modesetting.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/3.10.0-1062.1.1.el7.x86_64/build/include -I/tmp/vbox.0 -Iinclude/drm -D__KERNEL__ -DMODULE  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(modesetting)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_modesetting.o /tmp/vbox.0/modesetting.c
  gcc -Wp,-MD,/tmp/vbox.0/.vbox_drv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/3.10.0-1062.1.1.el7.x86_64/build/include -I/tmp/vbox.0 -Iinclude/drm -D__KERNEL__ -DMODULE  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vbox_drv)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_vbox_drv.o /tmp/vbox.0/vbox_drv.c
  gcc -Wp,-MD,/tmp/vbox.0/.vbox_fb.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/3.10.0-1062.1.1.el7.x86_64/build/include -I/tmp/vbox.0 -Iinclude/drm -D__KERNEL__ -DMODULE  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vbox_fb)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_vbox_fb.o /tmp/vbox.0/vbox_fb.c
In file included from /tmp/vbox.0/vbox_drv.c:31:0:
/tmp/vbox.0/vbox_drv.h:178:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:179:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
In file included from /tmp/vbox.0/hgsmi_base.c:27:0:
/tmp/vbox.0/vbox_drv.h:178:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:179:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
make[2]: *** [/tmp/vbox.0/vbox_drv.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [/tmp/vbox.0/hgsmi_base.o] Error 1
In file included from /tmp/vbox.0/vboxvideo_guest.h:32:0,
                 from /tmp/vbox.0/modesetting.c:27:
/tmp/vbox.0/vbox_drv.h:178:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:179:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
In file included from /tmp/vbox.0/vbox_fb.c:31:0:
/tmp/vbox.0/vbox_drv.h:178:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:179:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
make[2]: *** [/tmp/vbox.0/modesetting.o] Error 1
make[2]: *** [/tmp/vbox.0/vbox_fb.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxvideo] Error 2
```

---

### Post by cruzer001 on 2019-10-06
Try reinstalling the host kernel module.
```
sudo /sbin/vboxconfig
```
I installed the liveGnome session and get dev/loop boot errors, but it will boot up.  Won't allow me to install guest additions since I seem to be running off the live.iso.  Not knowing centos I probably picked the wrong iso.

Have you tried centos8?

---

### Post by SeijiSensei on 2019-10-06
I strongly recommend using the version of VirtualBox in the Oracle repository. I've never had problems with that version.

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by ajgreeny on 2019-10-06
> **SeijiSensei said:**
> I strongly recommend using the version of VirtualBox in the Oracle repository. I've never had problems with that version.

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

^^^^^^^  +  ^^^^^^^

I totally agree; I would not use any other source for the VBox deb itself or the GA.

VBox gets updated along with all other application updates, and then when you next start VBox it immediately tells you to update the GA; perhaps that's the same with a repo version of VBox but I haven't used that ever.

---

### Post by danielsender on 2019-10-06
I don't see anything such as /sbin/vboxconfig in the Ubuntu host.

I didn't try Centos 8 yet, maybe sometime in the future.

---

### Post by cruzer001 on 2019-10-06
> **danielsender said:**
> I don't see anything such as /sbin/vboxconfig in the Ubuntu host.
Must be 6.0
Do a restart in terminal and see if you get a kernel module fail.
```
sudo /etc/init.d/virtualbox restart
```
And this is suppose to be another way to reload module.
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by danielsender on 2019-10-06
There is no problem in restarting, the main issue is that the graphic interface is not set up properly with the GA so I get low resolution.

---

### Post by ajgreeny on 2019-10-06
What settings do you have for the graphics in the VM setup? You may find that whatever  default has been set when you created the VM is not what is needed. 
Try VBOXVGA for a start and one by one try the others if the first does not work.

---

### Post by danielsender on 2019-10-07
Let me repeat my first post: everything was fine until one of the last round of updates. Now when I right click on the window I only get offered 1024x768 as the maximum resolution, I think I previously had 1440x1080 or something like that. According to the log file, the GA setting is aborted for the graphic interface.

---

### Post by cruzer001 on 2019-10-07
Purge and reinstall, think I mention this before, but no reply on that.

Personally I think its time for 6.0.  LiveGnome did work for me.

---

### Post by danielsender on 2019-10-07
Well, I obeyed and purged 5.2.32 and installed 6.0.12 from the Oracle repository. It seems that I'm going nowhere on the resolution thing, it is the same list of errors. Please see the log file.
```

Building the main Guest Additions 6.0.12 module for kernel 3.10.0-1062.1.1.el7.x86_64.
Building the shared folder support module.
Building the graphics driver module.
Error building the module.  Build output follows.
make V=1 CONFIG_MODULE_SIG= -C /lib/modules/3.10.0-1062.1.1.el7.x86_64/build M=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -j4 modules
make[1]: warning: -jN forced in submake: disabling jobserver mode.
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
echo >&2;                            \
echo >&2 "  ERROR: Kernel configuration is invalid.";        \
echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
echo >&2 ;                            \
/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/.hgsmi_base.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I./include -I/tmp/vbox.0/ -I./include/drm -D__KERNEL__ -DMODULE -DRT_WITHOUT_PRAGMA_ONCE -DRT_ARCH_AMD64  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(hgsmi_base)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_hgsmi_base.o /tmp/vbox.0/hgsmi_base.c
  gcc -Wp,-MD,/tmp/vbox.0/.modesetting.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I./include -I/tmp/vbox.0/ -I./include/drm -D__KERNEL__ -DMODULE -DRT_WITHOUT_PRAGMA_ONCE -DRT_ARCH_AMD64  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(modesetting)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_modesetting.o /tmp/vbox.0/modesetting.c
  gcc -Wp,-MD,/tmp/vbox.0/.vbox_drv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I./include -I/tmp/vbox.0/ -I./include/drm -D__KERNEL__ -DMODULE -DRT_WITHOUT_PRAGMA_ONCE -DRT_ARCH_AMD64  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vbox_drv)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_vbox_drv.o /tmp/vbox.0/vbox_drv.c
  gcc -Wp,-MD,/tmp/vbox.0/.vbox_fb.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-redhat-linux/4.8.5/include -I./arch/x86/include -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -std=gnu89 -O2 -m64 -mno-mmx -mno-sse -mpreferred-stack-boundary=3 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -Wframe-larger-than=2048 -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_AVX512=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -mindirect-branch=thunk-extern -mindirect-branch-register -DRETPOLINE -Wframe-larger-than=2048 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -pg -mfentry -DCC_USING_FENTRY -fno-inline-functions-called-once -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I./include -I/tmp/vbox.0/ -I./include/drm -D__KERNEL__ -DMODULE -DRT_WITHOUT_PRAGMA_ONCE -DRT_ARCH_AMD64  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(vbox_fb)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxvideo)" -c -o /tmp/vbox.0/.tmp_vbox_fb.o /tmp/vbox.0/vbox_fb.c
In file included from /tmp/vbox.0/vboxvideo_guest.h:34:0,
                 from /tmp/vbox.0/modesetting.c:27:
/tmp/vbox.0/vbox_drv.h:187:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:188:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
In file included from /tmp/vbox.0/vbox_drv.c:38:0:
/tmp/vbox.0/vbox_drv.h:187:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:188:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
In file included from /tmp/vbox.0/hgsmi_base.c:27:0:
/tmp/vbox.0/vbox_drv.h:187:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:188:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
In file included from /tmp/vbox.0/vbox_fb.c:46:0:
/tmp/vbox.0/vbox_drv.h:187:31: error: field 'mem_global_ref' has incomplete type
   struct drm_global_reference mem_global_ref;
                               ^
/tmp/vbox.0/vbox_drv.h:188:28: error: field 'bo_global_ref' has incomplete type
   struct ttm_bo_global_ref bo_global_ref;
                            ^
make[2]: *** [/tmp/vbox.0/modesetting.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [/tmp/vbox.0/hgsmi_base.o] Error 1
make[2]: *** [/tmp/vbox.0/vbox_drv.o] Error 1
make[2]: *** [/tmp/vbox.0/vbox_fb.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxvideo] Error 2
```

---

### Post by SeijiSensei on 2019-10-07
```
error: field 'mem_global_ref' has incomplete type
```

I did a bit of [searching for this error]("https://forums.virtualbox.org/viewtopic.php?f=3&t=94218"), and it seems to be happening since late summer.  However it may be fixed in the most recent "Test Build": [https://www.virtualbox.org/download/testcase/VirtualBox-6.0.13-133688-Linux_amd64.run](https://www.virtualbox.org/download/testcase/VirtualBox-6.0.13-133688-Linux_amd64.run)

Another suggestion is to try this beta for the Guest Additions: [https://download.virtualbox.org/virtualbox/6.1.0_BETA1/VBoxGuestAdditions_6.1.0_BETA1.iso](https://download.virtualbox.org/virtualbox/6.1.0_BETA1/VBoxGuestAdditions_6.1.0_BETA1.iso). I'd give that a shot before using a test build.

---

### Post by cruzer001 on 2019-10-07
You can download 5.2.30 or earlier and lock the version so it cannot be upgraded.

[https://www.virtualbox.org/wiki/Download_Old_Builds_5_2](https://www.virtualbox.org/wiki/Download_Old_Builds_5_2)

Not a recommended route to go, but it will get you by in a pinch.

You may still be a candidate for KVM :)

---

### Post by danielsender on 2019-10-07
Hi guys,

I appreciate your time to help, luckily I can do my stuff using 'ssh -AX <IP of guest>' and go from there in full resolution windows and wait until some VB guru fixes the problem.

Cheers

---

### Post by danielsender on 2019-10-08
I posted the issue on the VB forum website and was advised to try the GA test built 6.0.13 and that fixed the problem. Thanks guys.

---

### Post by cruzer001 on 2019-10-08
Nice!  vBox does stay on top of their game when a fix needs to be put out.

I still got this low mileage KVM unit for sale :)

---

