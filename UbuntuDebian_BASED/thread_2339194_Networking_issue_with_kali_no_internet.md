---
title: "Networking issue with kali no internet"
date: 2016-10-05
forum: Ubuntu/Debian BASED
---

### Post by spankymit on 2016-10-05
so, im a linux noob, i had internet just fine when i had installed debian, then when i went to Kali, i have severe networking issue.. i have no connection with wifi or ethernet... i have no networking symbol in the top right of my screen. 

i typed "systemctl --all --no-pager

and got 

```

 UNIT                      LOAD      ACTIVE   SUB       DESCRIPTION
  proc-sys-fs-binfmt_misc.automount loaded    active   running   Arbitrary Executable File 
  dev-cdrom.device          loaded    active   plugged   MATSHITADVD-R_UJ-8A8
  dev-cdrw.device           loaded    active   plugged   MATSHITADVD-R_UJ-8A8
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart1.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart10.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart2.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart3.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart4.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart5.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart6.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart7.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart8.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart9.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-ata\x2dMATSHITADVD\x2dR_UJ\x2d8A8_D02208709K9DTL7BD.device loaded    active   plugged   MATSHITADVD-R_UJ-8A8
  dev-disk-by\x2did-usb\x2dLexar_USB_Flash_Drive_AACB6A3KB4X7B034\x2d0:0.device loaded    active   plugged   USB_Flash_Drive
  dev-disk-by\x2did-usb\x2dLexar_USB_Flash_Drive_AACB6A3KB4X7B034\x2d0:0\x2dpart1.device loaded    active   plugged   USB_Flash_Drive Lexar
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart1.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart10.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart2.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart3.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart4.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart5.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart6.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart7.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart8.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart9.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dlabel-EFI.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dlabel-Lexar.device loaded    active   plugged   USB_Flash_Drive Lexar
  dev-disk-by\x2dlabel-Recovery\x5cx20HD.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dlabel-Untitled\x5cx201.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dlabel-Untitled\x5cx202.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dlabel-Untitled\x5cx203.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartlabel-EFI\x5cx20System\x5cx20Partition.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartlabel-MSDOS.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartlabel-MSDOS2.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartlabel-Recovery\x5cx20HD.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartlabel-Untitled\x5cx201.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartlabel-Untitled\x5cx202.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartlabel-Untitled\x5cx203.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-147ba1b9\x2d6b95\x2d4b7b\x2dbd7b\x2d95c6b0b4bad7.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-234680ad\x2d6602\x2d459b\x2d9900\x2d094a3b3b05fd.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-59d29f7f\x2dadb2\x2d4c32\x2d91b6\x2d08e9072eafa4.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-86aa0b7f\x2d7b19\x2d4600\x2d9755\x2dac193374fa5a.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-941f6b85\x2d0f32\x2d43aa\x2d8ee9\x2da044ea503a8f.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-983ccae2\x2d62b6\x2d40c1\x2d8c38\x2d44a75bf0d718.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-a4fd6ba3\x2d3459\x2d48f2\x2da959\x2d9269c75cb596.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-a98fdc45\x2d419d\x2d482f\x2da9b5\x2d60761efe804d.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-b238f03a\x2df6c5\x2d422b\x2da9c8\x2d25eba2314590.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-ba33fabe\x2dfa37\x2d4b06\x2d89b5\x2d57ed6a2eb174.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpartuuid-c3072e18\x2d01.device loaded    active   plugged   USB_Flash_Drive Lexar
  dev-disk-by\x2dpath-pci\x2d0000:00:1d.7\x2dusb\x2d0:1.2:1.0\x2dscsi\x2d0:0:0:0.device loaded    active   plugged   USB_Flash_Drive
  dev-disk-by\x2dpath-pci\x2d0000:00:1d.7\x2dusb\x2d0:1.2:1.0\x2dscsi\x2d0:0:0:0\x2dpart1.device loaded    active   plugged   USB_Flash_Drive Lexar
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart1.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart10.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart2.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart3.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart4.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart5.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart6.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart7.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart8.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart9.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d2.device loaded    active   plugged   MATSHITADVD-R_UJ-8A8
  dev-disk-by\x2duuid-2d0f812f\x2dafb9\x2d32dd\x2d9bcb\x2dc8074e147e65.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-50a39b3f\x2dcbff\x2d40b1\x2dad10\x2dc050e386b4e0.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-65cf9f87\x2d0fe3\x2d38bf\x2da48e\x2d52984d8aa308.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-70D6\x2d1701.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-74C7\x2d4C26.device loaded    active   plugged   USB_Flash_Drive Lexar
  dev-disk-by\x2duuid-75241e40\x2dc0e4\x2d3cb0\x2db108\x2d8e4ec8acbc69.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-756399e0\x2d11b4\x2d4199\x2db79e\x2d70444a9e0b92.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-89f2de6d\x2dd287\x2d4423\x2da6e2\x2ddbbaf8772c35.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-94496a57\x2d2af1\x2d4226\x2d9844\x2d34b86dff00cf.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-e77f8bd1\x2d1a6b\x2d4e82\x2d8609\x2d31267891d2ad.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-disk-by\x2duuid-edc4270a\x2dd3b4\x2d3dbd\x2da158\x2d7643c92dc2c8.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-dvd.device            loaded    active   plugged   MATSHITADVD-R_UJ-8A8
  dev-dvdrw.device          loaded    active   plugged   MATSHITADVD-R_UJ-8A8
  dev-iio:device0.device    loaded    active   plugged   /dev/iio:device0
  dev-rfkill.device         loaded    active   plugged   /dev/rfkill
  dev-sda.device            loaded    active   plugged   APPLE_HDD_HTS547550A9E384
  dev-sda1.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda10.device          loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda2.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda3.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda4.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda5.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda6.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda7.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda8.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sda9.device           loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  dev-sdb.device            loaded    active   plugged   USB_Flash_Drive
  dev-sdb1.device           loaded    active   plugged   USB_Flash_Drive Lexar
  dev-sr0.device            loaded    active   plugged   MATSHITADVD-R_UJ-8A8
  dev-ttyS0.device          loaded    active   plugged   /dev/ttyS0
  dev-ttyS1.device          loaded    active   plugged   /dev/ttyS1
  dev-ttyS2.device          loaded    active   plugged   /dev/ttyS2
  dev-ttyS3.device          loaded    active   plugged   /dev/ttyS3
  sys-devices-LNXSYSTM:00-LNXSYBUS:00-PNP0A08:00-device:1a-ACPI0008:00-iio:device0.device loaded    active   plugged   /sys/devices/LNXSYSTM:00/L
  sys-devices-pci0000:00-0000:00:02.0-drm-card0-card0\x2dLVDS\x2d1-intel_backlight.device loaded    active   plugged   /sys/devices/pci0000:00/00
  sys-devices-pci0000:00-0000:00:1a.7-usb1-1\x2d1-1\x2d1.1-1\x2d1.1.3-1\x2d1.1.3:1.0-bluetooth-hci0.device loaded    active   plugged   /sys/devices/pci0000:00/00
  sys-devices-pci0000:00-0000:00:1b.0-sound-card0.device loaded    active   plugged   6 Series/C200 Series Chips
  sys-devices-pci0000:00-0000:00:1c.0-0000:02:00.0-net-eth0.device loaded    active   plugged   NetXtreme BCM57765 Gigabit
  sys-devices-pci0000:00-0000:00:1d.7-usb2-2\x2d1-2\x2d1.2-2\x2d1.2:1.0-host6-target6:0:0-6:0:0:0-block-sdb-sdb1.device loaded    active   plugged   USB_Flash_Drive Lexar
  sys-devices-pci0000:00-0000:00:1d.7-usb2-2\x2d1-2\x2d1.2-2\x2d1.2:1.0-host6-target6:0:0-6:0:0:0-block-sdb.device loaded    active   plugged   USB_Flash_Drive
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda1.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda10.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda2.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda3.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda4.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda5.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda6.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda7.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda8.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda9.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384 
  sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda.device loaded    active   plugged   APPLE_HDD_HTS547550A9E384
  sys-devices-pci0000:00-0000:00:1f.2-ata2-host1-target1:0:0-1:0:0:0-block-sr0.device loaded    active   plugged   MATSHITADVD-R_UJ-8A8
  sys-devices-platform-applesmc.768-hwmon-hwmon1.device loaded    active   plugged   /sys/devices/platform/appl
  sys-devices-platform-applesmc.768-leds-smc::kbd_backlight.device loaded    active   plugged   /sys/devices/platform/appl
  sys-devices-platform-coretemp.0-hwmon-hwmon2.device loaded    active   plugged   /sys/devices/platform/core
  sys-devices-platform-serial8250-tty-ttyS0.device loaded    active   plugged   /sys/devices/platform/seri
  sys-devices-platform-serial8250-tty-ttyS1.device loaded    active   plugged   /sys/devices/platform/seri
  sys-devices-platform-serial8250-tty-ttyS2.device loaded    active   plugged   /sys/devices/platform/seri
  sys-devices-platform-serial8250-tty-ttyS3.device loaded    active   plugged   /sys/devices/platform/seri
  sys-devices-virtual-hwmon-hwmon0.device loaded    active   plugged   /sys/devices/virtual/hwmon
  sys-devices-virtual-misc-rfkill.device loaded    active   plugged   /sys/devices/virtual/misc/
  sys-module-fuse.device    loaded    active   plugged   /sys/module/fuse
  sys-subsystem-bluetooth-devices-hci0.device loaded    active   plugged   /sys/subsystem/bluetooth/d
  sys-subsystem-net-devices-eth0.device loaded    active   plugged   NetXtreme BCM57765 Gigabit
  -.mount                   loaded    active   mounted   /
  boot-efi.mount            loaded    active   mounted   /boot/efi
  dev-hugepages.mount       loaded    active   mounted   Huge Pages File System
  dev-mqueue.mount          loaded    active   mounted   POSIX Message Queue File S
  media-root-Lexar.mount    loaded    active   mounted   /media/root/Lexar
  proc-sys-fs-binfmt_misc.mount loaded    active   mounted   Arbitrary Executable File 
  run-user-0-gvfs.mount     loaded    active   mounted   /run/user/0/gvfs
  run-user-0.mount          loaded    active   mounted   /run/user/0
  sys-fs-fuse-connections.mount loaded    inactive dead      FUSE Control File System
  sys-kernel-config.mount   loaded    inactive dead      Configuration File System
  sys-kernel-debug.mount    loaded    active   mounted   Debug File System
&#9679; tmp.mount                 not-found inactive dead      tmp.mount
  acpid.path                loaded    active   running   ACPI Events Check
  cups.path                 loaded    active   running   CUPS Scheduler
  systemd-ask-password-console.path loaded    active   waiting   Dispatch Password Requests
  systemd-ask-password-wall.path loaded    active   waiting   Forward Password Requests 
  init.scope                loaded    active   running   System and Service Manager
  session-2.scope           loaded    active   running   Session 2 of user root
  accounts-daemon.service   loaded    active   running   Accounts Service
  acpid.service             loaded    active   running   ACPI event daemon
  alsa-restore.service      loaded    inactive dead      Save/Restore Sound Card St
  alsa-state.service        loaded    inactive dead      Manage Sound Card State (r
  anacron.service           loaded    inactive dead      Run anacron jobs
  apache2.service           loaded    active   running   LSB: Apache2 web server
&#9679; apparmor.service          not-found inactive dead      apparmor.service
  arpwatch.service          loaded    active   exited    LSB: arpwatch daemon
  atd.service               loaded    active   running   Deferred execution schedul
&#9679; auditd.service            not-found inactive dead      auditd.service
  avahi-daemon.service      loaded    active   running   Avahi mDNS/DNS-SD Stack
  binfmt-support.service    loaded    active   exited    Enable support for additio
  bluetooth.service         loaded    active   running   Bluetooth service
  clamav-daemon.service     loaded    inactive dead      Clam AntiVirus userspace d
  colord.service            loaded    active   running   Manage, Install and Genera
&#9679; console-screen.service    not-found inactive dead      console-screen.service
  console-setup.service     loaded    active   exited    Set console font and keyma
  cpufrequtils.service      loaded    active   exited    LSB: set CPUFreq kernel pa
  cron.service              loaded    active   running   Regular background program
  cups-browsed.service      loaded    active   running   Make remote CUPS printers 
  cups.service              loaded    active   running   CUPS Scheduler
  dbus.service              loaded    active   running   D-Bus System Message Bus
  dm-event.service          loaded    inactive dead      Device-mapper event daemon
  emergency.service         loaded    inactive dead      Emergency Shell
  exim4.service             loaded    active   running   LSB: exim Mail Transport A
&#9679; festival.service          not-found inactive dead      festival.service
  gdomap.service            loaded    active   exited    LSB: Start the GNUstep dis
  getty-static.service      loaded    inactive dead      getty on tty2-tty6 if dbus
  [EMAIL="getty@tty1.servic"]getty@tty1.servic[/EMAIL]e        loaded    active   running   Getty on tty1
&#9679; greylist.service          not-found inactive dead      greylist.service
  iio-sensor-proxy.service  loaded    active   running   IIO Sensor Proxy service
  irqbalance.service        loaded    active   running   LSB: daemon to balance int
&#9679; kbd.service               not-found inactive dead      kbd.service
  keyboard-setup.service    loaded    active   exited    Set the console keyboard l
  kmod-static-nodes.service loaded    active   exited    Create list of required st
  lightdm.service           loaded    active   running   Light Display Manager
  loadcpufreq.service       loaded    active   exited    LSB: Load kernel modules n
  lvm2-lvmetad.service      loaded    inactive dead      LVM2 metadata daemon
  lvm2-lvmpolld.service     loaded    inactive dead      LVM2 poll daemon
  ModemManager.service      loaded    active   running   Modem Manager
  mysql.service             loaded    inactive dead      MySQL Community Server
  network-manager.service   loaded    active   exited    LSB: network connection ma
&#9679; networking.service        loaded    failed   failed    Raise network interfaces
&#9679; NetworkManager.service    not-found inactive dead      NetworkManager.service
  packagekit.service        loaded    active   running   PackageKit Daemon
  pcscd.service             loaded    inactive dead      PC/SC Smart Card Daemon
&#9679; plymouth-quit-wait.service not-found inactive dead      plymouth-quit-wait.service
&#9679; plymouth-start.service    not-found inactive dead      plymouth-start.service
  polkitd.service           loaded    active   running   Authenticate and Authorize
  postgresql.service        loaded    inactive dead      PostgreSQL RDBMS
  [EMAIL="postgresql@9.6-main.servic"]postgresql@9.6-main.servic[/EMAIL]e loaded    inactive dead      PostgreSQL Cluster 9.6-mai
  pppd-dns.service          loaded    inactive dead      Restore /etc/resolv.conf i
  rc-local.service          loaded    active   exited    /etc/rc.local Compatibilit
  rescue.service            loaded    inactive dead      Rescue Shell
  rpcbind.service           loaded    inactive dead      RPC bind portmap service
  rsyslog.service           loaded    active   running   System Logging Service
  smartd.service            loaded    active   running   Self Monitoring and Report
&#9679; spamassassin.service      not-found inactive dead      spamassassin.service
  speech-dispatcher.service loaded    active   exited    LSB: Speech Dispatcher
  ssh.service               loaded    active   running   OpenBSD Secure Shell serve
  stunnel4.service          loaded    active   exited    LSB: Start or stop stunnel
  sysstat.service           loaded    active   exited    LSB: Start/stop sysstat's 
  systemd-ask-password-console.service loaded    inactive dead      Dispatch Password Requests
  systemd-ask-password-wall.service loaded    inactive dead      Forward Password Requests 
  [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e loaded    active   exited    Load/Save Screen Backlight
  [EMAIL="systemd-backlight@leds:smc::kbd_backlight.servic"]systemd-backlight@leds:smc::kbd_backlight.servic[/EMAIL]e loaded    active   exited    Load/Save Screen Backlight
  systemd-binfmt.service    loaded    inactive dead      Set Up Additional Binary F
  systemd-fsck-root.service loaded    inactive dead      File System Check on Root 
  [EMAIL="systemd-fsck@dev-disk-by\x2duuid-70D6\x2d1701.servic"]systemd-fsck@dev-disk-by\x2duuid-70D6\x2d1701.servic[/EMAIL]e loaded    active   exited    File System Check on /dev/
  systemd-fsckd.service     loaded    inactive dead      File System Check Daemon t
  systemd-hwdb-update.service loaded    inactive dead      Rebuild Hardware Database
  systemd-initctl.service   loaded    inactive dead      /dev/initctl Compatibility
  systemd-journal-flush.service loaded    active   exited    Flush Journal to Persisten
  systemd-journald.service  loaded    active   running   Journal Service
  systemd-logind.service    loaded    active   running   Login Service
  systemd-machine-id-commit.service loaded    inactive dead      Commit a transient machine
  systemd-modules-load.service loaded    active   exited    Load Kernel Modules
  systemd-quotacheck.service loaded    inactive dead      File System Quota Check
  systemd-random-seed.service loaded    active   exited    Load/Save Random Seed
  systemd-remount-fs.service loaded    active   exited    Remount Root and Kernel Fi
  systemd-rfkill.service    loaded    inactive dead      Load/Save RF Kill Switch S
  systemd-sysctl.service    loaded    active   exited    Apply Kernel Variables
&#9679; systemd-sysusers.service  not-found inactive dead      systemd-sysusers.service
  systemd-timesyncd.service loaded    inactive dead      Network Time Synchronizati
  systemd-tmpfiles-clean.service loaded    inactive dead      Cleanup of Temporary Direc
  systemd-tmpfiles-setup-dev.service loaded    active   exited    Create Static Device Nodes
  systemd-tmpfiles-setup.service loaded    active   exited    Create Volatile Files and 
  systemd-udev-trigger.service loaded    active   exited    udev Coldplug all Devices
  systemd-udevd.service     loaded    active   running   udev Kernel Device Manager
&#9679; systemd-update-done.service not-found inactive dead      systemd-update-done.servic
  systemd-update-utmp-runlevel.service loaded    inactive dead      Update UTMP about System R
  systemd-update-utmp.service loaded    active   exited    Update UTMP about System B
  systemd-user-sessions.service loaded    active   exited    Permit User Sessions
&#9679; systemd-vconsole-setup.service not-found inactive dead      systemd-vconsole-setup.ser
  thin.service              loaded    active   exited    LSB: thin initscript
  udisks2.service           loaded    active   running   Disk Manager
  upower.service            loaded    active   running   Daemon for power managemen
  [EMAIL="user@0.servic"]user@0.servic[/EMAIL]e            loaded    active   running   User Manager for UID 0
  wpa_supplicant.service    loaded    active   running   WPA supplicant
  -.slice                   loaded    active   active    Root Slice
  system-getty.slice        loaded    active   active    system-getty.slice
  system-postgresql.slice   loaded    inactive dead      system-postgresql.slice
  system-systemd\x2dbacklight.slice loaded    active   active    system-systemd\x2dbackligh
  system-systemd\x2dfsck.slice loaded    active   active    system-systemd\x2dfsck.sli
  system.slice              loaded    active   active    System Slice
  user-0.slice              loaded    active   active    User Slice of root
  user.slice                loaded    active   active    User and Session Slice
  acpid.socket              loaded    active   running   ACPID Listen Socket
  avahi-daemon.socket       loaded    active   running   Avahi mDNS/DNS-SD Stack Ac
  cups.socket               loaded    active   running   CUPS Scheduler
  dbus.socket               loaded    active   running   D-Bus System Message Bus S
  dm-event.socket           loaded    active   listening Device-mapper event daemon
  lvm2-lvmetad.socket       loaded    active   listening LVM2 metadata daemon socke
  lvm2-lvmpolld.socket      loaded    active   listening LVM2 poll daemon socket
  pcscd.socket              loaded    active   listening PC/SC Smart Card Daemon Ac
  rpcbind.socket            loaded    active   listening RPCbind Server Activation 
  syslog.socket             loaded    active   running   Syslog Socket
  systemd-fsckd.socket      loaded    active   listening fsck to fsckd communicatio
  systemd-initctl.socket    loaded    active   listening /dev/initctl Compatibility
  systemd-journald-audit.socket loaded    active   running   Journal Audit Socket
  systemd-journald-dev-log.socket loaded    active   running   Journal Socket (/dev/log)
  systemd-journald.socket   loaded    active   running   Journal Socket
  systemd-rfkill.socket     loaded    active   listening Load/Save RF Kill Switch S
  systemd-udevd-control.socket loaded    active   running   udev Control Socket
  systemd-udevd-kernel.socket loaded    active   running   udev Kernel Socket
  dev-disk-by\x2did-ata\x2dAPPLE_HDD_HTS547550A9E384_J2210051HNAD7A\x2dpart9.swap loaded    active   active    /dev/disk/by-id/ata-APPLE_
  dev-disk-by\x2did-wwn\x2d0x5000cca641d755f2\x2dpart9.swap loaded    active   active    /dev/disk/by-id/wwn-0x5000
  dev-disk-by\x2dpartuuid-234680ad\x2d6602\x2d459b\x2d9900\x2d094a3b3b05fd.swap loaded    active   active    /dev/disk/by-partuuid/2346
  dev-disk-by\x2dpath-pci\x2d0000:00:1f.2\x2data\x2d1\x2dpart9.swap loaded    active   active    /dev/disk/by-path/pci-0000
  dev-disk-by\x2duuid-756399e0\x2d11b4\x2d4199\x2db79e\x2d70444a9e0b92.swap loaded    active   active    /dev/disk/by-uuid/756399e0
  dev-sda9.swap             loaded    active   active    Swap Partition
  basic.target              loaded    active   active    Basic System
  bluetooth.target          loaded    active   active    Bluetooth
  cryptsetup.target         loaded    active   active    Encrypted Volumes
  emergency.target          loaded    inactive dead      Emergency Mode
  getty.target              loaded    active   active    Login Prompts
  graphical.target          loaded    active   active    Graphical Interface
  local-fs-pre.target       loaded    active   active    Local File Systems (Pre)
  local-fs.target           loaded    active   active    Local File Systems
  multi-user.target         loaded    active   active    Multi-User System
  network-online.target     loaded    active   active    Network is Online
  network-pre.target        loaded    inactive dead      Network (Pre)
  network.target            loaded    active   active    Network
  nss-lookup.target         loaded    inactive dead      Host and Network Name Look
  nss-user-lookup.target    loaded    active   active    User and Group Name Lookup
  paths.target              loaded    active   active    Paths
  remote-fs-pre.target      loaded    inactive dead      Remote File Systems (Pre)
  remote-fs.target          loaded    active   active    Remote File Systems
  rescue.target             loaded    inactive dead      Rescue Mode
  rpcbind.target            loaded    inactive dead      RPC Port Mapper
  shutdown.target           loaded    inactive dead      Shutdown
  slices.target             loaded    active   active    Slices
  sockets.target            loaded    active   active    Sockets
  sound.target              loaded    active   active    Sound Card
  swap.target               loaded    active   active    Swap
  sysinit.target            loaded    active   active    System Initialization
&#9679; syslog.target             not-found inactive dead      syslog.target
  time-sync.target          loaded    active   active    System Time Synchronized
  timers.target             loaded    active   active    Timers
  umount.target             loaded    inactive dead      Unmount All Filesystems
  systemd-tmpfiles-clean.timer loaded    active   waiting   Daily Cleanup of Temporary


LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.


309 loaded units listed.
To show all installed unit files use 'systemctl list-unit-files'.
root@debian:~# 
```
  
please help....im trying my best to get the hang of this.. please and thank you

---

### Post by QIII on 2016-10-05
Moved to ***Ubuntu/Debian BASED***

Kali is no longer based on Ubuntu.  Even when it was called BackTrack and based on Ubuntu, it was not a member of the Ubuntu family.  While we are quite happy to answer your questions here if we can, you might also want to see if you can get help at the [Kali Forums]("https://forums.kali.org/").

Please use code tags when posting large sections of messages returned from the terminal.

You may do so by clicking the "#" sign above the text entry box, placing your cursor between the code tags and pasting your text.

You may also paste your text, highlight it and then click the "#" button.

Finally, you may type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after the text.  The square brackets are required.

---

