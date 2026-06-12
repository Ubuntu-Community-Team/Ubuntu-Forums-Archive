---
title: "boot iso from usb"
date: 2012-05-15
forum: Server Platforms
---

### Post by dstefaniuk on 2012-05-15
I've prepared an usb stick this way:

```
echo "d
1
d
n
p
1

+1024M
t
b
n
p
2


a
1
w
" | fdisk /dev/sdb
mkfs.vfat -F 32 /dev/sdb1
fdisk -l
mkdir -p /mnt/usb > /dev/null 2>&1
mount -t vfat /dev/sdb1 /mnt/usb
grub-install --no-floppy --force --root-directory=/mnt/usb /dev/sdb
cp -v ~/ubuntu-12.04-server-amd64.iso /mnt/usb
sync
function substring() {
    local STR="${1#${1%${2}*}${2}}";
    echo "${STR%${3}*}";
}
UUID=$(substring $(blkid | grep /dev/sdb1 | awk '{ print $2 }') 'UUID="' '"')
cat <<EOF > /mnt/usb/boot/grub/grub.cfg
set default=0
set timeout=10

insmod fat
search --no-floppy --fs-uuid $UUID --set=usb
set iso_path=/ubuntu-12.04-server-amd64.iso
loopback loop (\${usb})\${iso_path}
set root=(loop)
set bootopts="boot=casper iso-scan/filename=\${iso_path} ro noprompt noeject --"

menuentry "Boot ISO from USB" {
    linux (loop)/install/vmlinuz \$bootopts
    initrd (loop)/install/initrd.gz
}
EOF
```

This script should create a bootable usb stick that starts installation from mounted iso image - and it does. However, everything goes well up to the point when it tries to read from the image. So, it boots, starts installation process, I'm able to select language and keyboard type and that's it. Next, I get a message that the CD/DVD is not valid.

Why is that? How can I solve this problem?

---

### Post by oldfred on 2012-05-15
I recently tried server and had similar issues trying to loopmount with grub2. I was able to get parts to work but never the entire thing.

this was filed on the alternative version, but I think server is the same issue.
Grub does not loopmount alternate
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926)

Someone posted this, which got me further:

> With Debian Installer(Which is text/ncurses based) ,it asks to Mount Ubuntu CD when booted from hard disk iso.What I did was ,to symlink(symbolic Linking) Lucid Alternate cd ISO to /dev/sr0(Which is the device file for dvd drive) .Then If I ask debian-installer to retry to mount cd ,it got mounted!
Code:

ln -sf /yourubuntuisodirectory/ubuntu.iso /dev/sr0



---

### Post by dstefaniuk on 2012-05-16
I created the symbolic link but no success. It might be because I did it after the message about wrong CD/DVD appeared. When I came back from shell it didn't find the media.

What I wanted to do, was to be able to crate a bootable USB stick from a remastered ISO image from a shell scipt. So, if you don't need multiboot you may find this post [http://ubuntuforums.org/showthread.php?t=1980215]("http://ubuntuforums.org/showthread.php?t=1980215") helpful.

---

