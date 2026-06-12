---
title: "How to make a signed kernel/module from Ubuntu kernel source?"
date: 2017-09-16
forum: Virtualisation
---

### Post by wangt13 on 2017-09-16
Hi all,
    I am new here.
    I have a VM, which is installed with Ubuntu 16.10 LTS x86_64.
    The VM is configured to use EFI BIOS, not legacy BIOS. So there are /boot/vmlinuz-4.8.0-59-generic, and /boot/vmlinuz-4.8.0-59-generic.signed.

    Now, I want to re-build a 4.8.x kernel to do some kernel feature testing.
    I got the Linux-source-`uname -r`package, and edit the kernel configuration, then make, make install, make INSTALL_MOD_STRIP=1 modules_install, to deploy the new-build kernel into /boot/
    With VM reboot, I could NOT boot the new system, instead, it went to (initramfs): prompt.

    Then, I went back to the old kernel, and found that there is ONLY /boot/vmlinuz-4.8.17, no /boot/vmlinuz-4.8.17.signed.
    So, did I missed something? Is there a proper way to build initramfs for the new kernel? Does it need to build a signed kernel for EFI bootup?

    Thanks,
-Tao

---

### Post by wildmanne39 on 2017-09-16
*Thread moved to **Virtualisation.**.*

---

### Post by wangt13 on 2017-09-16
I found it is my bad.
The failure of bootup is from the build process.
the right build commands are
1. make
2. make INSTALL_MOD_STRIP=1 modules_install
3. make install

Thanks,
-Tao

---

### Post by ajgreeny on 2017-09-16
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

