---
title: "My Vivid Vervet Alpha2 install. Default grub is always wrong."
date: 2015-01-25
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-01-25
I downloaded and installed the Alpha 2 from the daily ISOs yesterday. The default grub is wrong but, it's been wrong on every install I've used since Quantal. This is another reason I customize my grub.
The default grub has all of my linux systems pointing to **sda2** where Precise 12.04 is installed. The **set root=** line or the  **linux /vmlinuz root=** line is wrong on everything except Precise 12.04.

This is why when I try to select another OS besides Vivid, it seems like it is booting into that system but never goes any where. I have to press Cntl+Alt+F1 to login tty and I see I'm on sda2 Precise.
I then install grub with my custom setup and then can boot into whatever system I want to.

Ran a grub-mkconfig and everything is fine in the **/etc/grub.d/10_linux** portion, but not in the **/etc/grub.d/30_os-prober** portion. (The [COLOR=#0000ff]blue[/COLOR] denotes where it is correct and the [COLOR=#ff0000]red[/COLOR] denotes where it is wrong.)

```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
[sudo] password for cavsfan: 
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" PARTUUID="a55f55ec-01"
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" PTTYPE="dos" PARTUUID="a55f55ec-02"
/dev/sda3: UUID="e14dc02e-6ea8-4c95-b4d0-9dc04d32294d" TYPE="swap" PARTUUID="a55f55ec-03"
/dev/sda5: LABEL="Vivid" UUID="d9b27f95-c89c-4e79-a128-1c9b5e02797a" TYPE="ext4" PARTUUID="a55f55ec-05"
/dev/sda6: LABEL="Trusty" UUID="d3281f82-3582-4081-b4d7-4769a2f427c5" TYPE="ext4" PARTUUID="a55f55ec-06"
/dev/sda7: LABEL="Mint-Rebecca" UUID="673f25f0-6149-4da7-98f8-4ebfe08a2188" TYPE="ext4" PARTUUID="a55f55ec-07"
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" PARTUUID="f87b4c9a-01"
```

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/[COLOR=#0000ff]sda1[/COLOR])' --class windows --class os $menuentry_id_option 'osprober-chain-1CFC7A8DFC7A60C6' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,[COLOR=#0000ff]msdos1[/COLOR]'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos1[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos1[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos1[/COLOR]  1CFC7A8DFC7A60C6
    else
      search --no-floppy --fs-uuid --set=root 1CFC7A8DFC7A60C6
    fi
    parttool ${root} hidden-
    chainloader +1
}
menuentry 'Ubuntu 12.04.5 LTS (12.04) (on /dev/[COLOR=#0000ff]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
    insmod part_msdos
    insmod ext2
    set root='hd0,[COLOR=#0000ff]msdos2[/COLOR]'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
    else
      search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
    fi
    linux /vmlinuz root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro quiet splash
    initrd /initrd.img
}
submenu 'Advanced options for Ubuntu 12.04.5 LTS (12.04) (on /dev/[COLOR=#0000ff]sda2[/COLOR])' $menuentry_id_option 'osprober-gnulinux-advanced-a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
    menuentry 'Precise Pangolin 12.04 (on /dev/[COLOR=#0000ff]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#0000ff]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Precise Pangolin 12.04 (Recovery Mode) (on /dev/[COLOR=#0000ff]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro single-a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#0000ff]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro single
        initrd /initrd.img
    }
    menuentry 'Trusty Tahr 14.04 (on /dev/[COLOR=#ff0000]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Trusty Tahr 14.04 (Recovery Mode) (on /dev/[COLOR=#ff0000]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro recovery nomodeset-a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 (devel branch) (on /dev/[COLOR=#ff0000]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 Upstart (devel branch) (on /dev/[COLOR=#ff0000]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro quiet splash init=/sbin/upstart
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 (devel branch) (Recovery Mode) (on /dev/[COLOR=#ff0000]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro recovery nomodeset-a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
    menuentry 'Mint 17 Rebecca (on /dev/[COLOR=#ff0000]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Mint 17 Rebecca (Recovery Mode) (on /dev/[COLOR=#ff0000]sda2[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro recovery nomodeset-a162dc8a-e4df-4b79-b4c3-524761ff7ae1' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos2[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos2[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos2[/COLOR]  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        else
          search --no-floppy --fs-uuid --set=root a162dc8a-e4df-4b79-b4c3-524761ff7ae1
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
}

menuentry 'Ubuntu 14.04.1 LTS (14.04) (on /dev/[COLOR=#0000ff]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-d3281f82-3582-4081-b4d7-4769a2f427c5' {
    insmod part_msdos
    insmod ext2
    set root='hd0,[COLOR=#0000ff]msdos6[/COLOR]'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos6[/COLOR] --hint-baremetal=ahci0,msdos6  d3281f82-3582-4081-b4d7-4769a2f427c5
    else
      search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
    fi
    linux /vmlinuz root=/dev/[COLOR=#ff0000]sda2[/COLOR] ro quiet splash
    initrd /initrd.img
}
submenu 'Advanced options for Ubuntu 14.04.1 LTS (14.04) (on /dev/[COLOR=#0000ff]sda6[/COLOR])' $menuentry_id_option 'osprober-gnulinux-advanced-d3281f82-3582-4081-b4d7-4769a2f427c5' {
    menuentry 'Precise Pangolin 12.04 (on /dev[COLOR=#0000ff]/sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#0000ff]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos6[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos6[/COLOR]  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#ff0000]sda2[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Precise Pangolin 12.04 (Recovery Mode) (on /dev/[COLOR=#ff0000]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro single-d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-baremetal=ahci0,msdos6  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro single
        initrd /initrd.img
    }
    menuentry 'Trusty Tahr 14.04 (on /dev/[COLOR=#0000ff]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#0000ff]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos6[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos6[/COLOR]  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Trusty Tahr 14.04 (Recovery Mode) (on /dev/[COLOR=#0000ff]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro recovery nomodeset-d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#0000ff]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos6[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos6[/COLOR]  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 (on /dev/[COLOR=#ff0000]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-baremetal=ahci0,msdos6  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 Upstart (devel branch) (on /dev/[COLOR=#ff0000]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos6[/COLOR]  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro quiet splash init=/sbin/upstart
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 (devel branch) (Recovery Mode) (on /dev/[COLOR=#ff0000]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro recovery nomodeset-d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos6[/COLOR]  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
    menuentry 'Mint 17 Rebecca (on /dev/[COLOR=#ff0000]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos6[/COLOR]  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Mint 17 Rebecca (Recovery Mode) (on /dev/[COLOR=#ff0000]sda6[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro recovery nomodeset-d3281f82-3582-4081-b4d7-4769a2f427c5' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos6[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos6[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos6[/COLOR]  d3281f82-3582-4081-b4d7-4769a2f427c5
        else
          search --no-floppy --fs-uuid --set=root d3281f82-3582-4081-b4d7-4769a2f427c5
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
}

menuentry 'Linux Mint 17.1 Rebecca (17.1) (on /dev/[COLOR=#0000ff]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-673f25f0-6149-4da7-98f8-4ebfe08a2188' {
    insmod part_msdos
    insmod ext2
    set root='hd0,[COLOR=#0000ff]msdos7[/COLOR]'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
    else
      search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
    fi
    linux /vmlinuz root=/dev/[COLOR=#ff0000]sda2[/COLOR] ro quiet splash
    initrd /initrd.img
}
submenu 'Advanced options for Linux Mint 17.1 Rebecca (17.1) (on /dev[COLOR=#0000ff]/sda7[/COLOR])' $menuentry_id_option 'osprober-gnulinux-advanced-673f25f0-6149-4da7-98f8-4ebfe08a2188' {
    menuentry 'Precise Pangolin 12.04 LTS (on /dev/[COLOR=#0000ff]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#0000ff]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#ff0000]sda2[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Precise Pangolin 12.04 LTS (Recovery Mode) (on /dev/[COLOR=#ff0000]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro recovery nomodeset-673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
    menuentry 'Trusty Tahr 14.04 LTS (on /dev/[COLOR=#ff0000]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Trusty Tahr 14.04 LTS (Recovery Mode) (on /dev/[COLOR=#ff0000]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro recovery nomodeset-673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda6[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 (devel branch) (on /dev/[COLOR=#ff0000]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 Upstart (devel branch) (on /dev/[COLOR=#ff0000]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro quiet splash init=/sbin/upstart
        initrd /initrd.img
    }
    menuentry 'Vivid Vervet 15.04 (devel branch) (Recovery Mode) (on /dev/[COLOR=#ff0000]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro recovery nomodeset-673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#ff0000]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#ff0000]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#ff0000]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda5[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
    menuentry 'Mint 17 Rebecca LTS (on /dev/[COLOR=#0000ff]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#0000ff]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro quiet splash
        initrd /initrd.img
    }
    menuentry 'Mint 17 Rebecca LTS (Recovery Mode) (on /dev/[COLOR=#0000ff]sda7[/COLOR])' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro recovery nomodeset-673f25f0-6149-4da7-98f8-4ebfe08a2188' {
        insmod part_msdos
        insmod ext2
        set root='hd0,[COLOR=#0000ff]msdos7[/COLOR]'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,[COLOR=#0000ff]msdos7[/COLOR] --hint-efi=hd0,[COLOR=#0000ff]msdos7[/COLOR] --hint-baremetal=ahci0,[COLOR=#0000ff]msdos7[/COLOR]  673f25f0-6149-4da7-98f8-4ebfe08a2188
        else
          search --no-floppy --fs-uuid --set=root 673f25f0-6149-4da7-98f8-4ebfe08a2188
        fi
        linux /vmlinuz root=/dev/[COLOR=#0000ff]sda7[/COLOR] ro recovery nomodeset
        initrd /initrd.img
    }
}

set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###
```

Not sure why the submenu entries for every install also contain all of the other linux systems either.

I'm going to reboot and verify what I have.

Edit: changed title to grub only

---

### Post by Cavsfan on 2015-01-25
I can confirm what I said in the first post. Everything is OK with booting into Vivid where grub is installed default and Precise appears OK.

But, on all of the rest of them either **set root=** line or the  **linux /vmlinuz root=** line is wrong causing it to boot into Precise on sda2 no matter what choice is made.

Also on the submenu entries for example Precise 12.04 on sda2, every system has sda2 beside of it.
On the menu submenu entries for Trusty 14.04 on sda6, every system has sda6 beside of it.
And so on...

Perhaps someone with more grub knowlege like maybe **Oldfred** could offer an explanation.

BTW: I also checked every /etc/fstab entry and they are all correct.

---

### Post by Cavsfan on 2015-01-25
Here is part of the "other things" as in the title:

I installed Gnome Flashback and purged gnome-screensaver since it's only a lock and not a real screensaver and installed xscreensaver.
The first time I started it up a box popped up telling me this:

[ATTACH=CONFIG]259494[/ATTACH]

It did this when I initially installed Alpha 1. It mentions that my disto is doing me a disservice by shipping with an older version of Xscreensaver.

[ATTACH=CONFIG]259497[/ATTACH]

I went to the website mentioned and replaced version 5.26 with  5.30.
They had a deb file which I installed with Ubuntu SOftware Center.

---

### Post by sammiev on 2015-01-25
> **Cavsfan said:**
> Here is part of the "other things" as in the title:

It mentions that my disto is doing me a disservice by shipping with an older version of Xscreensaver.

[ATTACH=CONFIG]259497[/ATTACH]

I went to the website mentioned and replaced version 5.26 with  5.30.
They had a deb file which I installed with Ubuntu SOftware Center.

I did the same as well to get rid of that little hiccup.

---

### Post by Cavsfan on 2015-01-25
> **Cavsfan said:**
> Here is part of the "other things" as in the title:

[ATTACH=CONFIG]259497[/ATTACH]

I went to the website mentioned and replaced version 5.26 with  5.30.
They had a deb file which I installed with Ubuntu SOftware Center.

> **sammiev said:**
> I did the same as well to get rid of that little hiccup.

Ha! Glad to see I'm not the only one. That was a strange one. Never seen that before and forgot to mention it earlier.

---

### Post by Cavsfan on 2015-01-25
About the grub problem. I had to edit the Trusty 14.04 line and change the sda2 to sda6 and then it booted into Trusty OK.
Then I installed grub there. I also installed **systemd-sysv** which makes systemd default and upstart an option.

---

### Post by sammiev on 2015-01-25
> **Cavsfan said:**
> About the grub problem. I had to edit the Trusty 14.04 line and change the sda2 to sda6 and then it booted into Trusty OK.
Then I installed grub there. I also installed **systemd-sysv** which makes systemd default and upstart an option.

I'm running in a VM on Vivid so not seeing the grub issues but for making systemd default is not an option at this point as it takes systemd an extra 1- 1/2 mins to boot ( likely because of the VM ).

---

### Post by Cavsfan on 2015-01-25
> **sammiev said:**
> I'm running in a VM on Vivid so not seeing the grub issues but for making systemd default is not an option at this point as it takes systemd an extra 1- 1/2 mins to boot ( likely because of the VM ).

Yeah most likely the VM. I've never done that. I just install using "other" options and pick my partition. This grub thing has been going on for quite a while.
It did the exact same when Trusty 14.04 LTS was released and rather than ugrade my Precise, which I'll hang onto until 2017, I just installed it on another partition.

---

### Post by syntaxerror74 on 2015-01-26
Jumping in with a seemingly dumb question...

How can all this work in the first place, anyway?

```
linux /vmlinuz root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro quiet splash
```

Considering that udev will always juggle around device names with each startup run, how can we be sure that /dev/sda will always point to the same hardware?

In my case, I would probably have done without ANY "hard-coded" device names like /dev/sdaX ...

---

### Post by Alan F on 2015-01-26
Please forgive me if this is a stupid question but I am trying to learn.

Cavsfan - When installing all these different Linux versions just how do you instruct the installer where to put the Grub bootloader?

What I have done with multiboot systems is to instruct the 'first' Linux install to install Grub to the MBR on sda. All subsequent installs are told to install Grub to the partition that they are loaded to. This I find keeps the installer happy and ensures that only one Grub install (the first) actually controls all booting.

This approach works well although it means that after changes it is necessary to boot the 'first' Linux install to run "sudo update-grub" (a small price to pay)

---

### Post by Elfy on 2015-01-26
> **Alan F said:**
> ...

What I have done with multiboot systems is to instruct the 'first' Linux install to install Grub to the MBR on sda. All subsequent installs are told to install Grub to the partition that they are loaded to. This I find keeps the installer happy and ensures that only one Grub install (the first) actually controls all booting.

This approach works well although it means that after changes it is necessary to boot the 'first' Linux install to run "sudo update-grub" (a small price to pay)

This is what I do.

Works for me - has worked for a long time :)

---

### Post by Cavsfan on 2015-01-26
> **syntaxerror74 said:**
> Jumping in with a seemingly dumb question...

How can all this work in the first place, anyway?

```
linux /vmlinuz root=/dev/[COLOR=#0000ff]sda2[/COLOR] ro quiet splash
```

Considering that udev will always juggle around device names with each startup run, how can we be sure that /dev/sda will always point to the same hardware?

In my case, I would probably have done without ANY "hard-coded" device names like /dev/sdaX ...

No question is a dumb question. We are all here to learn stuff and I'll be darned if I don't learn something new every day I feel like I'm not doing anything. :)
That entry is straight from this untouched file - **/etc/grub.d/30_os-prober** that is produced when **sudo update-grub** is entered. If you look while the system is being installed from CD or DVD you will see that it runs **sudo update-grub** at the end of the installation. You can run **sudo grub-mkconfig** in terminal and that will produce a listing of your grub.cfg.
If it's too large like mine is you can enter **sudo grub-mkconfig > <text-file-name>** and it will put it all in a text document so you can see it all.
That sda2 points to the second parition on drive number 1. This is my customized grub entries that I learned from a guy in this forum named Ranch Hand:
(Keep in mind that I have installed systemd-sysv in Vivid to make systemd the permanent default startup daemon, which is why you see the **init=/sbin/upstart** on the line I have to boot Vivid with upstart.)

[PHP]
#!/bin/sh
echo 1>&2 "Adding Precise Pangolin 12.04, Trusty Tahr 14.04, Vivid Vervet 15.04 (devel branch), Mint 17 Rebecca and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04" (devel branch){
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 Upstart (devel branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash init=/sbin/upstart
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 (devel branch) (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Mint 17 Rebecca" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Mint 17 Rebecca (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}[/PHP]

> **Alan F said:**
> Please forgive me if this is a stupid question but I am trying to learn.

Cavsfan - When installing all these different Linux versions just how do you instruct the installer where to put the Grub bootloader?

What I have done with multiboot systems is to instruct the 'first' Linux install to install Grub to the MBR on sda. All subsequent installs are told to install Grub to the partition that they are loaded to. This I find keeps the installer happy and ensures that only one Grub install (the first) actually controls all booting.

This approach works well although it means that after changes it is necessary to boot the 'first' Linux install to run "sudo update-grub" (a small price to pay)

There are no stupid questions and I've seen you a lot on here. You must know your fair share of this stuff. :)

I always install my grub on sda, the only hard drive I have. I have a 1TB USB drive that is connected at all times. During installation of previous systems it would try to put the grub on sdb (my USB drive) and didn't give me the option to change it so I had to unmount it before installation. However they've fixed that issue I believe in Trusty or Utopic.

You can only install grub to the hard drive (sda) and never the partitition eg. sda4. So, I don't understand how you say 
> All subsequent installs are told to install Grub to the partition that they are loaded to.

If you enter **sudo grub-install /sda3** for example you will get an error and it will not be installed there. It will remain wherever it was before.


> **Alan F said:**
> 
...

What I have done with multiboot systems is to instruct the 'first' Linux  install to install Grub to the MBR on sda. All subsequent installs are  told to install Grub to the partition that they are loaded to. This I  find keeps the installer happy and ensures that only one Grub install  (the first) actually controls all booting.

This approach works well although it means that after changes it is  necessary to boot the 'first' Linux install to run "sudo update-grub" (a  small price to pay)
> **Elfy said:**
> This is what I do.

Works for me - has worked for a long time :)

Again I do not understand the concept of installing grub on any partition; it has to be the drive **sda**.
Besides just **sudo update-grub** one would have enter **sudo grub-install /sda** from the system that you desire to have your grub on.

I have customized every installation I have on this box. And in my case as you can see from the 1st post everything points to my "primary install" Precise on sda2.

I'm still wanting to know why everything points to sda2 (Precise) while it's still untouched by any customization.

I also wonder about this in red which I have never noticed before:

```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
[sudo] password for cavsfan: 
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" PARTUUID="a55f55ec-01"
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" [COLOR=#ff0000]PTTYPE="dos"[/COLOR] PARTUUID="a55f55ec-02"
/dev/sda3: UUID="e14dc02e-6ea8-4c95-b4d0-9dc04d32294d" TYPE="swap" PARTUUID="a55f55ec-03"
/dev/sda5: LABEL="Vivid" UUID="d9b27f95-c89c-4e79-a128-1c9b5e02797a" TYPE="ext4" PARTUUID="a55f55ec-05"
/dev/sda6: LABEL="Trusty" UUID="d3281f82-3582-4081-b4d7-4769a2f427c5" TYPE="ext4" PARTUUID="a55f55ec-06"
/dev/sda7: LABEL="Mint-Rebecca" UUID="673f25f0-6149-4da7-98f8-4ebfe08a2188" TYPE="ext4" PARTUUID="a55f55ec-07"
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" PARTUUID="f87b4c9a-01"
```

---

### Post by kansasnoob on 2015-01-26
> You can only install grub to the hard drive (sda) and never the partitition eg. sda4.

You can install grub to a pbr rather than the mbr during installation of the OS only if you choose the option "Something else" (aka; advanced partitioning). See towards the very bottom where it says "Device for boot loader installation":

[ATTACH=CONFIG]259524[/ATTACH]

> If you enter sudo grub-install /sda3 for example you will get an error and it will not be installed there.

The syntax is slightly wrong there, it should be like sudo grub-install /dev/sda3, but it's really better to just run:

```
sudo dpkg-reconfigure grub-pc
```

Otherwise each time an update triggers update-grub it'll revert to it's previously installed location.

---

### Post by Alan F on 2015-01-27
> **kansasnoob said:**
> You can install grub to a pbr rather than the mbr during installation of the OS only if you choose the option "Something else" (aka; advanced partitioning). See towards the very bottom where it says "Device for boot loader installation":

[ATTACH=CONFIG]259524[/ATTACH]

This is exactly what I do. I have always felt nervous/unsure about attempting installs through the CLI.

---

### Post by Cavsfan on 2015-01-27
> You can only install grub to the hard drive (sda) and never the partitition eg. sda4.

> **kansasnoob said:**
> You can install grub to a pbr rather than the mbr during installation of the OS only if you choose the option "Something else" (aka; advanced partitioning). See towards the very bottom where it says "Device for boot loader installation":

[ATTACH=CONFIG]259524[/ATTACH]

>                                                          If you enter sudo grub-install /sda3 for example you will get an error and it will not be installed there.                      

     
 

The syntax is slightly wrong there, it should be like sudo grub-install /dev/sda3, but it's really better to just run:

```
sudo dpkg-reconfigure grub-pc
```

Otherwise each time an update triggers update-grub it'll revert to it's previously installed location.

Yeah I always get that command wrong it would be **sudo grub-install /dev/sda3** if it worked but it doesn't.

I always choose "Something else" when I install and I make sure Grub will be installed to /dev/sda as in your picture.

I don't understand the concept of pbr vs mbr. You're saying install it on the partition? I have never seen that option. 
All I have seen is /dev/sda (my hard drive) and /dev/sdb (which is my USB drive) at the bottom of the installation screen.
Luckily they changed it to where it automagically finds my hard drive instead of my USB drive.

And how would this get grub to point to the correct partitions anyway?

I booted into Vivid and got a bunch of updates and a new kernel, then rebooted and there was no way to enter my password.
I even rebooted and selected the previous kernel and got the same results.

So, I am in Precise 12.04 for the time being, which BTW was the only other option than Vivid that had the correct boot line pointing to the correct partition sda2.
If I want to get into anything else I would need to edit the line and change sda2 to whatever partition it is really installed on.

---

### Post by Elfy on 2015-01-27
When you choose Something Else - or whatever they might call it currently :)

Set up which partition is /

In the grub area - pick the partition (disregarding any warning written there) then just carry on installing.

Once done - update grub from whichever DOES have it installed to sda and it'll pick the new one up. 

You just need to remember which one does control it - something I forget from time to time ...

---

### Post by Alan F on 2015-01-27
Adding to what Elfy said above, see screenshot

Laptop is booted with Ubuntu Live CD 14.04. Windows 7 and Ubuntu 15.04 is already installed.

The 2nd hard drive sdc has 2 partitions currently formatted NTFS

This demo is simulating installing 14.04 onto partition sdc2 and installing the boot loader to sdc2.

Note that the 'first' Linux install is 15.04 on sdb3 with its bootloader installed to sdb (This one install will control the boot however many partitions for Linux are created)

Note that sda is the flash drive that Live CD files are on and sdd, another connected flash drive, are NOT offered to install the boot loader. sdb, sdb1, sdb2, sdb3, sdc, sdc1 and sdc2 are all offered as potential install locations for the bootloader.

---

### Post by Cavsfan on 2015-01-27
> **Elfy said:**
> When you choose Something Else - or whatever they might call it currently :)

Set up which partition is /

In the grub area - pick the partition (disregarding any warning written there) then just carry on installing.

Once done - update grub from whichever DOES have it installed to sda and it'll pick the new one up. 

You just need to remember which one does control it - something I forget from time to time ...

> **Alan F said:**
> Adding to what Elfy said above, see screenshot

Laptop is booted with Ubuntu Live CD 14.04. Windows 7 and Ubuntu 15.04 is already installed.

The 2nd hard drive sdc has 2 partitions currently formatted NTFS

This demo is simulating installing 14.04 onto partition sdc2 and installing the boot loader to sdc2.

Note that the 'first' Linux install is 15.04 on sdb3 with its bootloader installed to sdb (This one install will control the boot however many partitions for Linux are created)

Note that sda is the flash drive that Live CD files are on and sdd, another connected flash drive, are NOT offered to install the boot loader. sdb, sdb1, sdb2, sdb3, sdc, sdc1 and sdc2 are all offered as potential install locations for the bootloader.

I know what you mean Elfy. I don't really have a special partition except Precise is on a physical partition and I consider my main install sda2.

Wow, I've never seen that before. How do you get partitions to appear on the list of where to install the bootloader? 
All I've ever seen is sda and sdb. Is this a new thing or something?

Worth doing another install just to see that. Or I guess from a live cd would be much easier. Can you go that far and then back out just fine without doing the actual install?

---

### Post by Alan F on 2015-01-27
> **Cavsfan said:**
> 

Wow, I've never seen that before. How do you get partitions to appear on the list of where to install the bootloader? 
All I've ever seen is sda and sdb. Is this a new thing or something?

Worth doing another install just to see that. Or I guess from a live cd would be much easier. Can you go that far and then back out just fine without doing the actual install?

Just boot the computer from the Live CD and work through the install proceedure and select "SOMETHING ELSE" when asked what to do (MOST IMPORTANT)

The next screen should be the one you are looking for.

At this point you can back out without problems.

---

### Post by Cavsfan on 2015-01-28
> **Alan F said:**
> Just boot the computer from the Live CD and work through the install proceedure and select "SOMETHING ELSE" when asked what to do (MOST IMPORTANT)

The next screen should be the one you are looking for.

At this point you can back out without problems.

Thanks I'll give that a go when I can. Really surprised that I had not heard of this before.
So, If I put grub on say sda2 what happens? The grub entries are still wrong pointing to the wrong partitions but you all have custom entries like I do?

Still just a bit curious as to what the difference is between putting grub on sda vs sda2 (for example).

On a side note, I did see a command **sudo grub-install --force /dev/sda2** (--force option - install even if problems are detected) but I would be very hesitant to attempt that one.

---

### Post by kansasnoob on 2015-01-28
Regarding the Precise version of grub-pc displaying incorrect device designations you may want to look at my old bug report here (particularly comment #4):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1065801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1065801)

There's some additional history here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774)

Anyway that's fixed in Trusty which I now use as my everyday OS to get work done and it displays correct device designations.

---

### Post by Cavsfan on 2015-01-28
> **kansasnoob said:**
> Regarding the Precise version of grub-pc displaying incorrect device designations you may want to look at my old bug report here (particularly comment #4):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1065801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1065801)

There's some additional history here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1050774)

Anyway that's fixed in Trusty which I now use as my everyday OS to get work done and it displays correct device designations.

Precise is what I consider my main OS and after looking at that top bug I can see that might be where the problem is coming from.
My drive is laid out like this:

[LIST=1]
[*]sda1 - Windows 7 
[*]sda2 - Precise 12.04 
[*]sda3 - swap 1GB - bad choice on my part to put a 1GB swap file on a physical partition but c'est la vie! 
[*]sda4 - extended partition.
[LIST=1]
[*]sda5 - Vivid 15.04 
[*]sda6 - Trusty 14.04 
[*]sda7 - Mint 17 Rebecca 
[/LIST]
    
[/LIST]

I guess when I upgrade to Trusty in 2017 (if this pc makes it that long) this issue with the mistaken labels should be resolved.
If not then Trusty will be the primary and problem will still be solved based on what you're saying.

I did find out that one doesn't really need a swap file if you have at least 4GB of memory as long as you don't use hibernate.
Hibernate uses that swap file and suspend does not. I always use suspend or sleep on my system anyway.

This is not really a solvable problem I guess as that bug was never fixed. It was a good topic of discussion though and brought out some very good information.

I've definitely learned a lot. Grub has indeed evolved and I like that it keeps getting better.

---

### Post by zika on 2015-01-30
> **syntaxerror74 said:**
> my entire /etc/fstab consists of UUIDsDitto.
An, as far as I know, that behaviour is mainly a default... ;)
```
# Use 'blkid' to print the universally unique identifier for a# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5)
```

---

### Post by Cavsfan on 2015-01-31
OldFred finally got the gist of **sudo dpkg-reconfigure grub-pc** through my head.

[http://ubuntuforums.org/showthread.p...5#post13218885]("http://ubuntuforums.org/showthread.php?t=2263120&page=2&p=13218885#post13218885")

Since grub was updated on Vivid the other day I thought I would try the  above command. It took me through several steps and instead of MBR on  the hard drive I chose /dev/sda6
where Trusty is and where I prefer my grub. It gave some warnings about  installing to a partition but then gave the installation was successful  statement.

So, every thing looked good but, when I rebooted grub was still on Vivid sda5. So, I rebooted and again edited the Trusty line and booted to that and installed grub there again.

According to OldFred he said don't install grub to partitions. Maybe  that command above is for when you have multiple drives you could decide which drive  to install grub on. I could understand that.

And I'm going to customize my grub like I mentioned in post [_#12_]("http://ubuntuforums.org/showthread.php?t=2262516&page=2&p=13216350#post13216350") of this thread with no UUIDs, just partitions. Because I only have to do that once.
I love having more than one install because I can copy that file over, change a few things and it's done. 
Then when the next grub update comes through I'll still have the customized grub screen and it all actually works pointing to the correct partitions.

It will always install grub on the partition where grub is installed/updated. I have not yet seen a proven method to change that.

---

### Post by Cavsfan on 2015-01-31
> **Alan F said:**
> Please forgive me if this is a stupid question but I am trying to learn.

Cavsfan - When installing all these different Linux versions just how do you instruct the installer where to put the Grub bootloader?

What I have done with multiboot systems is to instruct the 'first' Linux install to install Grub to the MBR on sda. All subsequent installs are told to install Grub to the partition that they are loaded to. This I find keeps the installer happy and ensures that only one Grub install (the first) actually controls all booting.

This approach works well although it means that after changes it is necessary to boot the 'first' Linux install to run "sudo update-grub" (a small price to pay)

@Alan F, pardon my slowness... 
But, I think I finally get what you are saying here. You let the 'primary Linux install' install your grub on MBR and then the subsequent installs you install to the partition.
So, in essence the other 'Linux installs' do not install grub at all leaving the one you installed on MBR. 
Then the reason you have to boot into your 'first' Linux install and run "sudo update grub" is so that it will pick up the new 'Linux install'.

Am I finally understanding that right? Taking some heavy meds to try to quell the problems I have and they don't even do a good job of that.

---

### Post by Elfy on 2015-02-01
> So, in essence the other 'Linux installs' do not install grub at all leaving the one you installed on MBR. The don't install to the MBR no - they do install grub though or they'd not be bootable.

>  Then the reason you have to boot into your 'first' Linux install and run "sudo update grub" is so that it will pick up the new 'Linux install'.Correct.

---

### Post by Alan F on 2015-02-01
> **Cavsfan said:**
> @Alan F, pardon my slowness... 
But, I think I finally get what you are saying here. You let the 'primary Linux install' install your grub on MBR and then the subsequent installs you install to the partition.
So, in essence the other 'Linux installs' do not install grub at all leaving the one you installed on MBR. 
Then the reason you have to boot into your 'first' Linux install and run "sudo update grub" is so that it will pick up the new 'Linux install'.

Am I finally understanding that right? Taking some heavy meds to try to quell the problems I have and they don't even do a good job of that.

Please excuse delay in answering but Elfy has summed up perfectly

---

### Post by Cavsfan on 2015-02-01
> **Alan F said:**
> Please excuse delay in answering but Elfy has summed up perfectly

OK, thank you Elfy!
I've got it now. You let the other installs install to a partition rather than MBR so it completes the task of installing grub even though that grub is not usable.
It just goes through the necessary process of installing grub and gets a completion message thus completing the installation.

But, what about when a new version of grub comes down through updates and installs on say another install rather than the preferred one?
Then you'd still have to boot to the preferred install and enter **sudo grub-install /dev/sdxx** right?

Because I see no way to prevent grub from being installed on MBR in that case. You do not have an option to control where it gets installed at that point. Correct?

No problem Alan F,  thanks for the reply! I'm still learning...

---

### Post by zika on 2015-02-01
I might be (very) wrong but if You let primary Linux install put Grub in MBR and subsequent Linux install(s) to put their Grub in PBR then You should be set, bullet-proof, against upgrades of any of those Grub(s) etc.

---

### Post by Elfy on 2015-02-01
Get a new kernel - that updates the grub for *that* install.

The grub which is installed in the MBR won't know anything about that - until it's updated with update-grub, then it will see changes.

You can probably chroot and update - but I've no interest in doing that.

I've never needed to do grub-install to do any of that - thought I've needed to when things get broken of course.

---

### Post by Cavsfan on 2015-02-01
> **zika said:**
> I might be (very) wrong but if You let primary Linux install put Grub in MBR and subsequent Linux install(s) to put their Grub in PBR then You should be set, bullet-proof, against upgrades of any of those Grub(s) etc.

Thanks for that clear explanation. 

> **Elfy said:**
> Get a new kernel - that updates the grub for *that* install.

The grub which is installed in the MBR won't know anything about that - until it's updated with update-grub, then it will see changes.

You can probably chroot and update - but I've no interest in doing that.

I've never needed to do grub-install to do any of that - thought I've needed to when things get broken of course.

Ditto thanks for the clarification. Now I have it etched in concrete.

And I too shall abide by these rules forever more! But, I do understand that I cannot fix it that way now. It has to be done when installing each install initially selecting "something else".
So my grub in MBR now gets constantly changed when any of them get updated. I see that now.

I think I will install Trusty 14.04.2 over Precise 12.04 when it's released on February 5th and the other installs can be easily backed up and clean installs performed.
Then I will comprehend where you all are coming from finally when I see it with my own eyes. Plus it'll be something to keep me off the streets. :p

My partitions are out of sequence besides that. The pc is old but my daughter just gave me this hard drive a year ago for Christmas. So, I should be good for a while then.

Again thanks very much for the posts!

---

### Post by Cavsfan on 2015-02-01
BTW, isn't this a fine looking grub menu here on Vivid?

[[IMG]http://www.zimagez.com/miniature/20150201141509.jpg[/IMG]]("http://www.zimagez.com/zimage/20150201141509.php")

The picture is a little crooked but I never said I was a Ubuntu expert or a photographer either. :p I'm just a minion like a lot of people are.

---

### Post by kansasnoob on 2015-02-01
> But, I do understand that I cannot fix it that way now. It has to be done when installing each install initially selecting "something else".
So my grub in MBR now gets constantly changed when any of them get updated. I see that now.

That's not true. That's where this command comes into play:

```
sudo dpkg-reconfigure grub-pc
```

When you run that command in each of your currently installed Ubuntu installs you can change where grub is installed and the change will remain in place during kernel updates and things that cause update-grub to be run. Just be sure you know where you want grub installed!

> I think I will install Trusty 14.04.2 over Precise 12.04 when it's released on February 5th

Just a word of caution; if 14.04.2 gets the Utopic HWE stack as previously planned it'll end up in HWE EOL shortly after 16.04 is released. Have a look at the support life cycle here:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

A lot of users were upset when they discovered their 12.04.2, 12.04.3, and 12.04.4 installs required a major kernel and Xstack upgrade nearly three years before Precise itself reached EOL.

---

### Post by Cavsfan on 2015-02-01
> But, I do understand that I cannot fix it that way now. It has to be  done when installing each install initially selecting "something else".
So my grub in MBR now gets constantly changed when any of them get updated. I see that now.

> **kansasnoob said:**
> That's not true. That's where this command comes into play:

```
sudo dpkg-reconfigure grub-pc
```

When you run that command in each of your currently installed Ubuntu installs you can change where grub is installed and the change will remain in place during kernel updates and things that cause update-grub to be run. Just be sure you know where you want grub installed!

>  I think I will install Trusty 14.04.2 over Precise 12.04 when it's released on February 5th                      

Just a word of caution; if 14.04.2 gets the Utopic HWE stack as previously planned it'll end up in HWE EOL shortly after 16.04 is released. Have a look at the support life cycle here:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

A lot of users were upset when they discovered their 12.04.2, 12.04.3, and 12.04.4 installs required a major kernel and Xstack upgrade nearly three years before Precise itself reached EOL.

Thanks for that information! I'll do that and keep my grub on Trusty where I have kept it most of the time,

Sounds like a bummer about 14.04.2. I'll have to read that when I can. Precise is supposed to be good until 2017 so I may not do a whole lot.

Thanks for the post!

---

### Post by Cavsfan on 2015-02-06
Well, I read some of that article. Just enough to see that they are switching kernels within the lifecycle I believe is what you were getting at.

I guess I'll just leave it as it is for the time being. At least I've got until 2017 for Precise which I'm sort of fond of.

I'll probably do this when I get a chance. 
```
sudo dpkg-reconfigure grub-pc
```

You all can keep your grub on whatever system you like. I have to be kept up to date of when grub changes for my wiki so I'll likely keep it on the development system.
I've never seen grub change drastically during it's system life cycle at least in my limited 5 or so years of dealing with Linux. 
So, once a system is at final release I can relax until the next developement system comes up. It's just **/etc/grub.d/05_debian_theme** that changes where to put the font colors mainly.

I've never seen grub go awry at any time during the developmental cycle but even if it should I have done a couple of grub rescues in my time and can get around that.

I'll probably add this information to the bottom of my wiki about having one grub control all of the systems.

Thanks again for all of the information and help!

---

