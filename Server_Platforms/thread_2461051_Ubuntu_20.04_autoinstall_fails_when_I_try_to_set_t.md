---
title: "Ubuntu 20.04 autoinstall fails when I try to set the storage"
date: 2021-04-23
forum: Server Platforms
---

### Post by paull28 on 2021-04-23
I want to do an Ubuntu 20.04 autoinstall from a separate partition. The block structure:

 ```
sda
| -- sda1 vfat  /cdrom     (iso image copied) - bootable
| -- sda2 ext4 /var/crash (added by ubuntu)

```

On sda1 I have copied the data from the Ubuntu iso and added a nocloud folder that contains the files user-data and meta-data.
 The grub.cfg menu entry:
 ```
menuentry "Install Ubuntu Server" {
        set gfxpayload=keep
        linux   /casper/vmlinuz autoinstall   ds='nocloud;s=file://cdrom/nocloud/'  ---
        initrd  /casper/initrd
}
grub_platform
if [ "$grub_platform" = "efi" ]; then
menuentry 'Boot from next volume' {
        exit 1
}
menuentry 'UEFI Firmware Settings' {
        fwsetup
}
fi

``` 
[LIST=1]
[*]Using a simple, basic user-data configuration: 
[/LIST]
 ```
#cloud-config
autoinstall:
  version: 1
  identity:
    hostname: ubuntu-server2
    password: "$6$exDY1mhS4KUYCE/2$zmn9ToZwTKLhCw.b4/b.ZRTIZM30JZ4QrOQ2aOXJ8yk96xpcCof0kxKwuX1kqLG/ygbJ1f8wxED22bTL4F46P0"
    username: ubuntu

```[INDENT] I get the error: "NoneType" object has no attribute "grub_device"
 [/INDENT]

[LIST=1]
[*]Adding storage layout as lvm or direct I get the same error. 
[*]Changing storage to: 
[/LIST]
 ```
storage:
    config:
    - grub_device: true
      id: disk-sda
      path: /dev/sda
      ptable: gpt
      type: disk
      wipe: superblock-recursive

```[INDENT] I get the error: "No match"

 [/INDENT]

[LIST=1]
[*]I also tried by adding dev/sda2 as root: 
[/LIST]
 ```
linux   /casper/vmlinuz autoinstall   root=/dev/sda2 ds='nocloud;s=file://cdrom/nocloud/'  ---

``` same errors as above.
 
[LIST=1]
[*]I tried to set the storage interactive for testing purpose: 
[/LIST]
 ```
interactive-sections:
    - storage

``` the autoinstall just freeze, no option to set storage available.
 How can I fix this, and what are the rules to set storage in case of multiple storage devices ?

---

