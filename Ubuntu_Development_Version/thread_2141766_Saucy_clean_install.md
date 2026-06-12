---
title: "Saucy clean install"
date: 2013-05-03
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2013-05-03
Forum looked like the Daily Build was settling down.

Copied raring...amd64.iso to saucy .....

Ran zsync was 74.8% complete so not too much saucy stuff in yet.

Acer netbook test pc, 1 gb, duo intel Atom 1.5 ghz  20" 1600x900 external monitor wireless keyboard & mouse, hard drive has Windows 7 & stable ubuntu's so target install is to partition 5 of USB Intel SSD.

Booted .iso direct from hard drive with /etc/grub.d/40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ringtail64 13.04" {
set isofile="/raring-desktop-amd64.iso"
loopback loop (hd0,10)$isofile 
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
sudo update-grub, reboot, select the .iso and boot.
Comes up in 800x600 so laptop screen off, external monitor to 1024x768 since 1600x900 will not allow rotation normal.
df to find the boot partition /dev/sda6, then sudo umount -rl /dev/sda6.  Umounted all the rest of the USB drive devices too.
Open install
Tried setting format to btrfs on USB SSD partition 5, got a couple abends, so went to ext4.
Install went normally.  Reboot.

Usual setup for me, turn screenlock off, launcher icons 32, hidden, laptop monitor off, external monitor to 1024x768 apply to get normal rotation then 1600x900 apply,  Yes there's a launchpad bug.  Nobody interested.

As usual saucy thinks the encrypted network is "out of range" because sus;og sayd "requires secrets" which of course it already has but chooses not to use. so on every boot I have to do systems settings network, connect to hidden network, select the only one, wait, wait, then it finally brings up panel all filled in with encryption key, select it, wait, and connects.  All the info it had already.  Chromebook, Pangolin, Galaxy Tab2, Asus Transformer, etc. just connect with no manual intervention to wireless encrypted.  There's a launchpad bug but seems to me raring/saucy network manager policy is NOT to connect to an encrypted network.  Not user friendly.

Ran setup exec to set software-properties-gtk partners on, unsupported updates no, updates never, apt-get update, apt-get dist-upgrade, install gparted, install samba, zsync, synaptic, flashplugin installer, ufw enable.  Saves time on the installs I do frequently.

unity privacy files off, firefox extensions disable last 3 items, import bookmarks I must have a couple hundred, unlock launcher icons I don't use..

Up and running.  Now for the "dread updates"....

---

### Post by cariboo on 2013-05-03
@jerrylamos, have you tried wicd, to see if that solves your problem, see [here]("https://help.ubuntu.com/community/WICD"), for a howto.

---

