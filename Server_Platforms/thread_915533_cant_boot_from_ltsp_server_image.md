---
title: "cant boot from ltsp server image"
date: 2008-09-09
forum: Server Platforms
---

### Post by mixersoft on 2008-09-09
problem booting from ltsp server. please help. (I posted this on networking, but now I realize that this might be the right forum)

This is the error message I get on the client midway through boot:
[INDENT]
    ipconfig: eth0: SIOCGIFINDEX: No such device
    ipconfig: no devices to configure
    /init: .: 1: Can't open /tmp/net-eth0.conf
    [] Kernel panic - not syncing: Attempted to kill init![/INDENT]

Here's what I've tried so far:

[LIST]
[*] my ltsp server and client box have identical configs

[*] using Hardy 8.04.1 alternate, with ltsp server installed from the CD

[*] I followed this post to ensure both the ltsp-server and ltsp chroot are up-to-date:

[INDENT]          [ http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-updates.html]( http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-updates.html)[/INDENT]

[*] on the ltsp server, eth0 seems to work just fine:

[INDENT]          sudo lsmod ==> lists the sky2 driver on the ltsp server
          sudo modprobe sky2 ==> shows nothing. but no errors. so the driver is fine, right? [/INDENT]

[*] /opt/ltsp/i386/boot/pxelinux.cfg/default edited as follows:

[INDENT]          DEFAULT vmlinuz ro initrd=initrd.img
          # DEFAULT vmlinuz ro initrd=initrd.img quiet splash[/INDENT]

[*] on the theory that eth0 was being reset in the middle of PXE Boot
[INDENT]      see: [https://help.ubuntu.com/community/DisklessUbuntuHowto#head-320eeefb87afe42faa400af457bd455bec59d7ef ](https://help.ubuntu.com/community/DisklessUbuntuHowto#head-320eeefb87afe42faa400af457bd455bec59d7ef )[/INDENT]
      /opt/ltsp/i386/etc/network/interfaces was edited for eth0 as follows (each config was tested to the same result):

[INDENT]          # This file describes the network interfaces available on your system
          # and how to activate them. For more information, see interfaces(5).

          # The loopback network interface
          auto lo
          iface lo inet loopback

          # The primary network interface for PXE Boot
          #auto eth0
          #iface eth0 inet dhcp
          iface eth0 inet manual[/INDENT]

    [*] each time, I ran these commands to make sure the ltsp image is updated

[INDENT]          sudo ltsp-update-kernels
          sudo ltsp-update-image
          sudo ltsp-update-sshkeys[/INDENT]

[/LIST]
In all cases, I get the PXE boot image, get past the ubuntu splash screen, and then halfway through boot, it crashes.

Can someone offer any additional suggestions???

m.

---

### Post by ubu_dynamite on 2008-10-17
##
## Add some client network card drivers
## On the client find out the driver your network card is using
lshw -C network

## on the server
sudo nano /opt/ltsp/i386/etc/initramfs-tools/modules
## and add your drivers"
<------------

e1000
e1000e
via-rhine
sis900

------------>
## etc."

sudo chroot /opt/ltsp/i386 update-initramfs -u
sudo ltsp-update-kernels

[http://ubuntuforums.org/showthread.php?t=943518](http://ubuntuforums.org/showthread.php?t=943518)

---

