---
title: "GCC error when compiling kernel"
date: 2016-02-24
forum: Ubuntu Development Version
---

### Post by sabina2 on 2016-02-24
Hi !  I tried to reinstall the 4.4.2 kernel with Grsecurity patch on my fresh Kubuntu. All works untill I try to compile the kernel with "sudo make deb-pkg", I got this :  ```
Makefile:664: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler   CHK     include/config/kernel.release make clean   CLEAN   arch/x86/purgatory   CLEAN   arch/x86/tools   CLEAN   .tmp_versions   TAR     linux-4.4.2-grsec.tar.gz make KBUILD_SRC= Makefile:664: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler   GENHASH  tools/gcc/size_overflow_plugin/size_overflow_hash.h   GENHASH  tools/gcc/size_overflow_plugin/size_overflow_hash_aux.h   GENHASH  tools/gcc/size_overflow_plugin/disable_size_overflow_hash.h   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/insert_size_overflow_asm.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/intentional_overflow.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/remove_unnecessary_dup.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/size_overflow_debug.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/size_overflow_ipa.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/size_overflow_misc.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/size_overflow_plugin.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/size_overflow_plugin_hash.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/size_overflow_transform.o   HOSTCXX -fPIC tools/gcc/size_overflow_plugin/size_overflow_transform_core.o   HOSTLLD -shared tools/gcc/size_overflow_plugin/size_overflow_plugin.so   HOSTCXX -fPIC tools/gcc/colorize_plugin.o   HOSTCXX -fPIC tools/gcc/constify_plugin.o   HOSTCXX -fPIC tools/gcc/initify_plugin.o   HOSTCXX -fPIC tools/gcc/kernexec_plugin.o   HOSTCXX -fPIC tools/gcc/latent_entropy_plugin.o   GENSEED  tools/gcc/randomize_layout_seed.h   HOSTCXX -fPIC tools/gcc/randomize_layout_plugin.o   HOSTLLD -shared tools/gcc/constify_plugin.so   HOSTLLD -shared tools/gcc/kernexec_plugin.so   HOSTLLD -shared tools/gcc/colorize_plugin.so   HOSTLLD -shared tools/gcc/latent_entropy_plugin.so   HOSTLLD -shared tools/gcc/initify_plugin.so   HOSTLLD -shared tools/gcc/randomize_layout_plugin.so   HOSTCC  scripts/basic/fixdep   HOSTCC  scripts/basic/bin2c   HOSTCC  arch/x86/tools/relocs_32.o   HOSTCC  arch/x86/tools/relocs_64.o   HOSTCC  arch/x86/tools/relocs_common.o   HOSTLD  arch/x86/tools/relocs   CHK     include/config/kernel.release   CHK     include/generated/uapi/linux/version.h   CHK     include/generated/utsrelease.h   CC      arch/x86/purgatory/purgatory.o   AS      arch/x86/purgatory/stack.o   AS      arch/x86/purgatory/setup-x86_64.o   CC      arch/x86/purgatory/sha256.o   AS      arch/x86/purgatory/entry64.o   CC      arch/x86/purgatory/string.o   LD      arch/x86/purgatory/purgatory.ro   BIN2C   arch/x86/purgatory/kexec-purgatory.c   CC      kernel/bounds.s gcc: error: unrecognized command line option ‘-fstack-protector-strong’ make[3]: *** [kernel/bounds.s] Erreur 1 make[2]: *** [prepare0] Erreur 2 make[1]: *** [deb-pkg] Erreur 2 make: *** [deb-pkg] Erreur 2
```  I tried to upgrade my GCC but It still does not work. All was working well with 4.3.4 and 4.3.5-grsec then I resintalled my Kubuntu and tried to patch the 4.4.2 kernel with Grsecurity and got this error message.   Do you know what to do to solve this "fstach-protector-strong" error with Ubuntu ? Thanks in advance !

---

### Post by sabina2 on 2016-02-24
Auto-solved, by upgrading GCC to 4.9.3 and adding gcc-4.9-plugin.dev.  But then next error appeared :  ```
scripts/sign-file.c:23:30: fatal error: openssl/opensslv.h: Aucun fichier ou dossier de ce type  #include                                ^ compilation terminated. make[3]: *** [scripts/sign-file] Erreur 1 make[2]: *** [scripts] Erreur 2 make[1]: *** [deb-pkg] Erreur 2 make: *** [deb-pkg] Erreur 2 
```

---

### Post by sabina2 on 2016-02-24
Auto-solved 2 : Installed libssl-dev and now it is working.  Thanks for your attention ! :D

---

### Post by Doug S on 2016-02-24
The other option for the "stack protector" issue, is just to disable it:
```
scripts/config --disable CC_STACKPROTECTOR_STRONG
```
Note: The stack protector issue is as of kernel 4.4-rc1
Note: The libssl-dev required issue is as of kernel 4.3-rc1.

---

