---
title: "grub2 unable to boot ubuntu iso"
date: 2014-09-28
forum: Ubuntu Development Version
---

### Post by nhasian on 2014-09-28
Hello,

I thought it would be fun to test Ubuntu 14.10 beta2.  rather than burning it to a dvd or onto a thumbdrive, I am trying to get grub2 to simply boot the ISO.  It is claiming it cannot find the file.  I don't think it's anything wrong with the ISO (I've downloaded it twice and can mount it in nautilus).  It is probably something I'm doing wrong with my grub configuration.  I am able to boot the fedora ISO just fine but they both have different options as you can see below.  What am I doing wrong?

EDIT: I should also point out that I have separate /boot and /home partitions.  The /home partition where the ISO resides is btrfs which I don't think should be a problem as the fedora iso boots fine from there.  Also my laptop is several years old and UEFI is disabled. It is booting in legacy (BIOS) mode.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu 14.10 ISO" {
  set isoname="ubuntu-14.10-beta2-desktop-amd64.iso"
  set isofile="/nasser/ISOs/${isoname}"
  echo "Using ${isoname}..."
  loopback loop (hd0,6)$isofile
  linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} locale=en_US.UTF-8 quiet splash
  initrd (loop)/casper/initrd.lz
}

menuentry "Fedora 21 ISO" --class fedora {
  set isoname="fedora21.iso"
  set isofile="/nasser/ISOs/${isoname}"
  echo "Using ${isoname}..."
  loopback loop (hd0,6)$isofile
  linux (loop)/isolinux/vmlinuz0 root=live:CDLABEL=Fedora-Live-Workstation-x86_64-2 rootfstype=auto ro rd.live.image quiet rhgb rd.luks=0 rd.md=0 rd.dm=0 iso-scan/filename=${isofile}
  initrd (loop)/isolinux/initrd0.img
}
```

---

### Post by d-cosner on 2014-09-28
Maybe something here could be of help?

[http://www.wikihow.com/Boot-an-Ubuntu-ISO-from-Your-Hard-Drive](http://www.wikihow.com/Boot-an-Ubuntu-ISO-from-Your-Hard-Drive)

---

### Post by CantankRus on 2014-09-28
Nothing stands out.
Check the isoname.
This is my entry which is a zsynced iso, so name may be different.
```
menuentry 'ISO Utopic  ' {
set isofile="/distros/utopic-desktop-amd64.iso"
loopback loop (hd1,6)$isofile
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject 
initrd (loop)/casper/initrd.lz 
}
```

---

### Post by oldfred on 2014-09-28
I thought you might need an insmod btrfs command, but if Fedora boots that then may not be required?

Usually when I get that type of error, it either is path or name of ISO is not correct. If Fedora boots, then I would think path is ok. Is that the latest name for the ISO, mine is older and is just  utopic-desktop-amd64.iso.
I also have grub on my sdd drive and the ISO on a gpt partitioned sdb drive. In grub drive you boot from is always hd0 and other drives then are listed, my sdb then becomes hd2 and files are in partition 4.

[codeE]menuentry "Ubuntu 14.10 Utopic ISO 64bit Daily" {
    set isofile="/iso/utopic-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}
[/code]

---

### Post by grahammechanical on 2014-09-30
From my experiments with brtfs I noticed that if Ubuntu is installed onto a btrfs partition then Ubuntu will show up in a Grub menu and load successfully. But if there are other installations of Ubuntu and they are also on btrfs partitions the Grub os-prober utility does not detect them and put them in its menu. I concluded that Grub has a bit of difficulty with btrfs.

Regards.

---

### Post by jerrylamos on 2014-10-01
Do note that if there is a file anywhere in the system even on a different partition and a different hard drive named
/iso/utopic-desktop-amd64.iso
it is my experience that grub gets confused and starts using both files getting all screwed up.

I've had better luck with the iso file on the root of whatever partition and not in a folder

btrfs I tried and it screwed up.  At the time it did not appear capable of handling two drives one of which boots windows7 and the other has several partitions.  

Can btrfs reliably handle several partitions on the same hard drive some of which are not btrfs?  

Do they all have to be btrfs?  What about windows7 too?

My ignorance about btrfs is showing.....maybe when it is proven to be solid and reliable.

---

### Post by ventrical on 2014-10-01
Last I checked, btrfs was not solid and reliable with other partitions or, as Graham said, especially with another btrfs partition and/or grub. What it *is* good for is that if you have an extra hdd, like to experiment on the cutting edge and want to test 'proposed' repository then if and when your dev install borks up you can always restore to working image.

---

