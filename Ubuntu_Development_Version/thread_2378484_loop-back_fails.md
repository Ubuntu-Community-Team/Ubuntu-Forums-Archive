---
title: "loop-back fails"
date: 2017-11-23
forum: Ubuntu Development Version
---

### Post by VMC on 2017-11-23
My loopback menu has worked for years, but now fails on bionic. It boots up bonic, but when I try to install to existing partition, it tries and fails to remove sda from /isodevice Most likely ubiquity has changed:
```
menuentry "ISO" {
    set isofile="/ISO/bionic-desktop-amd64.iso"
    loopback loop (hd0,8)$isofile
    linux (loop)/casper/vmlinuz.efi boot=casper **toram** maybe-ubiquity iso-scan/filename=$isofile noprompt noswap noeject
    initrd (loop)/casper/initrd.lz
}
```

Before answer see this explanation regarding [loopback]("https://askubuntu.com/questions/968141/iso-on-hard-drive-boot-install") boot.

---

### Post by oldfred on 2017-11-23
I have only used loopback method for years, and last several years from one hard drive to another.
I had similar issues before.
On suggestion was to use toram boot parmeter which I now use as a default in all my grub stanzas.
And other was to unmount the isodrive which seems to auto mount into where one of my regular partitions is on sda.
sudo umount -l -r -f /isodevice

 # Required as /isodevice usually mounts to a partition and installer does not correctly unmount
sudo umount -lrf /isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216)
Says to use toram boot parameter

---

### Post by VMC on 2017-11-24
Yes, I "bold" the **toram** above to show its there. This loopback has always worked and still does using the latest 'xenial' iso. Just 'bionic' fails to remove sda.
whenever I try the unmount command, it keeps saying "/isodevice" is busy when is mounted to sda8.

---

### Post by flocculant on 2017-11-25
I've just tested this lot:
```

menuentry "Xubuntu 18.04 Daily ISO" {
        set isofile="/boot/grubiso/bionic-desktop-amd64.iso"
        # or set isofile="/<username>/Downloads/ubuntu-12.04.2-desktop-amd64.iso"
        # if you use a single partition for your $HOME
        loopback loop (hd0,6)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper toram maybe-ubiquity iso-scan/filename=$isofile noprompt noswap noeject
        initrd (loop)/casper/initrd.lz
}

menuentry "Xubuntu Xenial" {
        set isofile="/boot/grubiso/xenial-desktop-amd64.iso"
        # or set isofile="/<username>/Downloads/ubuntu-12.04.2-desktop-amd64.iso"
        # if you use a single partition for your $HOME
        loopback loop (hd0,6)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper toram maybe-ubiquity iso-scan/filename=$isofile noprompt noswap noeject
        initrd (loop)/casper/initrd.lz
}

menuentry "Xubuntu Zesty" {
        set isofile="/boot/grubiso/zesty-desktop-amd64.iso"
        # or set isofile="/<username>/Downloads/ubuntu-12.04.2-desktop-amd64.iso"
        # if you use a single partition for your $HOME
        loopback loop (hd0,6)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper toram maybe-ubiquity iso-scan/filename=$isofile noprompt noswap noeject
        initrd (loop)/casper/initrd.lz
}

menuentry "Xubuntu Artful" {
        set isofile="/boot/grubiso/artful-desktop-amd64.iso"
        # or set isofile="/<username>/Downloads/ubuntu-12.04.2-desktop-amd64.iso"
        # if you use a single partition for your $HOME
        loopback loop (hd0,6)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper toram maybe-ubiquity iso-scan/filename=$isofile noprompt noswap noeject
        initrd (loop)/casper/initrd.lz
}

```

The only one that fails to remove isodevice is the latest Steve Austin dev release.

---

### Post by flocculant on 2017-11-25
reported it against ubiquity [lpbug]1734430[/lpbug]

I know the maintainer and see him regularly on irc - will see what happens on the bug - and prod after a while.

---

### Post by VMC on 2017-11-25
> **flocculant said:**
> reported it against ubiquity [lpbug]1734430[/lpbug]

I know the maintainer and see him regularly on irc - will see what happens on the bug - and prod after a while.
Thanks. I wasn't sure which one of your *loopbacks* failed.

---

