---
title: "Slax frugal install (sort of)"
date: 2008-03-02
forum: Slackware and derivatives
---

### Post by kagashe on 2008-03-02
Slax is a fast Live CD distribution. I copied the iso on a spare partition and run it from there after writing necessary entry in /boot/grub/menu.lst

I wanted to save my configurations (like one can do for Puppy) and found a cheatcode "changes=/folder" so I wrote that cheatcode and it has become a sort of Frugal install on the spare partition.

I posted about it on my [blog]("http://kagashe.blogspot.com/") and find that there are queries on this forum, therefore I am copying the [blog post]("http://kagashe.blogspot.com/2008/02/slax-is-very-fast.html") below:
> I love Puppy Linux because of its speed but Slax is equally fast and it has KDE desktop.

Today I downloaded the latest updated version Slax 6.0.1 which has fixed many bugs in Slax 6.0 which was launched on 13th Feb 2008.

I keep a spare 1 GB partition on my hard disc where I copy the iso and modify /boot/grub/menu.lst file to boot directly from the iso without burning CD.

First I create a "install_cd" directory in /tmp and mount the iso on it by the following commands:

    mkdir /tmp/install_cd
    mount slax-6.0.1.iso -o loop /tmp/install_cd

Then I copy the contents of the iso on /media/hda8 (hda8 is 1 GB partition formatted in ext3) by following command:

    cp -r /tmp/install_cd/* /media/hda8

Then I edit /boot/grub/menu.lst to add the following line:

    title Slax 6.0.1
    root (hd0,7)
    kernel /boot/vmlinuz root=/dev/ram ramdisk_size=6666 rw changes=/dev/hda8
    initrd /boot/initrd.gz

"changes=/dev/hda8" is the cheatcode for saving configurations since Slax is a Live CD distribution which is loaded into RAM.

After rebooting I could run Slax.

After setting up the Network connection (Slax sets up automatically if it is dhcp but mine is static ip) I went to Slax site and downloaded Firefox module from this page.

After downloading I copied the module to /mnt/hda8/slax/modules so that it is available permanently.

Then I activated the module through Slax Module Manager. It is really very neat.

I have also changed time zone and added Hindi (IN) Keyboard and installed additional fonts through KDE Control Centre.

It is an excellent distribution and very fast since it runs from RAM.

kagashe

---

