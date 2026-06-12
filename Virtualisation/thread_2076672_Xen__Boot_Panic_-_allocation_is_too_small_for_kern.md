---
title: "Xen  Boot Panic - allocation is too small for kernel image."
date: 2012-10-26
forum: Virtualisation
---

### Post by bryogenic on 2012-10-26
Current setup: Ubuntu 12.04, 3.2.0-32, Xen4.1-amd64

When booting Xen from Grub2 I get the following kernel panic:

```
(XEN) ********************
(XEN) Panic on CPU 0:
(XEN) Domain 0 allocation is too small for kernel image.
(XEN) ********************
```

So far I have tried every combination I can think of [dom0_mem=].

My current /etc/default/grub
```
GRUB_DEFAULT="Xen 4.1-amd64"
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_XEN_DEFAULT="dom0_mem=min:8192M,max:8192M loglvl=all"

```

and the resulting /boot/grub/grub.cfg menuentry

```
### BEGIN /etc/grub.d/20_linux_xen ###
submenu "Xen 4.1-amd64" {
menuentry 'Ubuntu GNU/Linux, with Xen 4.1-amd64 and Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os --class xen {
        insmod part_gpt
        insmod ext2
        set root='(hd0,gpt3)'
        search --no-floppy --fs-uuid --set=root dfeb1395-8583-4bed-bc97-8f2317a7e9dd
        echo    'Loading Xen 4.1-amd64 ...'
        multiboot       /boot/xen-4.1-amd64.gz placeholder  dom0_mem=min:8192M,max:8192M loglvl=all
        echo    'Loading Linux 3.2.0-32-generic ...'
        module  /boot/vmlinuz-3.2.0-32-generic placeholder root=UUID=dfeb1395-8583-4bed-bc97-8f2317a7e9dd ro  quiet splash
        echo    'Loading initial ramdisk ...'
        module  /boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu GNU/Linux, with Xen 4.1-amd64 and Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --class xen {
        insmod part_gpt
        insmod ext2
        set root='(hd0,gpt3)'
        search --no-floppy --fs-uuid --set=root dfeb1395-8583-4bed-bc97-8f2317a7e9dd
        echo    'Loading Xen 4.1-amd64 ...'
        multiboot       /boot/xen-4.1-amd64.gz placeholder
        echo    'Loading Linux 3.2.0-32-generic ...'
        module  /boot/vmlinuz-3.2.0-32-generic placeholder root=UUID=dfeb1395-8583-4bed-bc97-8f2317a7e9dd ro single 
        echo    'Loading initial ramdisk ...'
        module  /boot/initrd.img-3.2.0-32-generic
}
```

Thanks for any help![LIST=1]
[/LIST]

---

### Post by bryogenic on 2012-10-30
Looks like I am not the only one with this issue : [http://serverfault.com/questions/443555/xen-hipervisor-4-1-kernel-panic-on-ubuntu-12-04](http://serverfault.com/questions/443555/xen-hipervisor-4-1-kernel-panic-on-ubuntu-12-04)
Any ideas?

---

