---
title: "tipico: no puedo hacer andar el grub en windows xp"
date: 2010-02-08
forum: Software
---

### Post by Fitmoos on 2010-02-08
antes que me reten
resultados del [B]sudo fdisk -l

''Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x9c439c43

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/sda5            1276        2550    10241406    7  HPFS/NTFS
/dev/sda6            2551        9728    57657253+   c  W95 FAT32 (LBA) ''


y el  /boot/grub/menu.lst

''### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5855d962-e816-4537-80f3-87fe0f364dbd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5855d962-e816-4537-80f3-87fe0f364dbd

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        5855d962-e816-4537-80f3-87fe0f364dbd
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=5855d962-e816-4537-80f3-87fe0f364dbd ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        5855d962-e816-4537-80f3-87fe0f364dbd
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=5855d962-e816-4537-80f3-87fe0f364dbd ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        5855d962-e816-4537-80f3-87fe0f364dbd
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        5855d962-e816-4537-80f3-87fe0f364dbd
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd0,5)
savedefault
makeactive
chainloader +1''


como pueden notarlo, el windows está en sda5 (que exta en la extencion sda2). Aun asi no me anda. Ademas no me da el tiempo para el menu del grub en la partida. me siendo avergonzado como usuario de 8 meces de ubuntu estar preguntanto este tipo de cosas, pero no me anda, y no entiendo como hacerlo andar.
Trate con el sgd y no pude hacerlo andar...
[/B]

---

### Post by Fitmoos on 2010-02-08
estoy usando ubuntu 9.10 64, y el que no puedo hacer andar es al win xp

---

### Post by Tosh78 on 2010-02-08
Probaste resinstalando grub? Sinceramente no soy una persona tecnica y no entiendo el error que tenes, pero yo intentaria googleando el error y despues si no hay caso, reinstalar grub.
Quizas alguno de los chicos que sabe mas que yo puede ayudar un poco.

---

