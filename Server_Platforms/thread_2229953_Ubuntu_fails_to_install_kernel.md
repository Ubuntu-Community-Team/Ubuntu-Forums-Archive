---
title: "Ubuntu fails to install kernel"
date: 2014-06-16
forum: Server Platforms
---

### Post by tnteverett on 2014-06-16
I posted this thread under general installation issues but have not gotten any traction on finding a solution.  
[http://ubuntuforums.org/showthread.php?t=2228793](http://ubuntuforums.org/showthread.php?t=2228793)
I am reposting here for two reasons.  One to see if I can get help from another group or individual. Two because I now know this is not a serial console installation issue.  I have tried multiple times with serial console options.  I have now duplicated the same failure on a system with a monitor and keyboard.  
The failure always occurs when the kernel is being installed and I cannot get past it.  Please review some of the messages on the first thread.  
Please help or point me to where I can get help on this issue.  Any help is appreciated.

Ubuntu 14.04 server 64 bit
Sun Microsystems CP3250 ATCA Blade

Thanks,
Tom

---

### Post by matt_symes on 2014-06-16
Hi
> 
There are problems and -y was used without --force-yes
WARNING: The following packages cannot be authenticated!

Maybe a pgp key issue on the second attempt ?

I assume the second attempt was a chroot over the serial connection ?

You could try updatoing the keys from the key server or using --force-yes when trying to install the kernel.

The first attempt is maybe a bug in the installer ? 

What do you mean by a custom iso ? Did you customise it to allow support for the serial console ?

Can you supply a bit more information about what you have done.

Kind regards

---

### Post by tnteverett on 2014-06-16
I started by trying to install 14.04 on my target without any modification to the USB I created from the "ubuntu-14.04-server-amd64.iso".
This does not work because I have no keyboard or mouse on my Sun Microsystems CP3250 ATCA blade. I modified the USB files to allow output to the serial console.  I ran the install and it gets to the end and won't install the kernel. 
Message is "Unable to install the selected kernel An error was returned while trying to install the kernel into the target system. Kernel package: 'linux-generic'."
I tried many variations of the install options and always got the same error.  I eventually found an HP DL360 system with keyboard and monitor to use so I recreated an unmodified USB for the install.  The install gets to the end where I get the same message about not being able to install the kernel.
The only common thing between the two systems is the SAS hard disk I need to use for the CP3250 system.  
I need to capture the logs from the HP system but since the failure is identical I assumed that the logs would pretty much say the same thing.  When I attempt the install on the HP system which has a keyboard and monitor there are zero modifications to the USB files created from the same ISO.  
I also tried the desktop version of the ISO with the same end result.

---

### Post by tnteverett on 2014-06-17
Here is a copy of the tail end of syslog from a fresh USB install.  USB created using "Universal-USB-Installer-1.9.5.3.exe", and "ubuntu-14.04-server-amd64.iso".
Installed using the HP DL380 with keyboard, mouse, and monitor.
Error message is the same.
```

Jun 17 18:57:04 in-target: Building dependency tree...
Jun 17 18:57:04 in-target: 
Jun 17 18:57:04 in-target: locales is already the newest version.
Jun 17 18:57:04 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Jun 17 18:57:04 localechooser: Generating locales...
Jun 17 18:57:04 localechooser:   en_US.UTF-8... 
Jun 17 18:57:04 localechooser: done
Jun 17 18:57:04 localechooser: Generation complete.
Jun 17 18:57:04 localechooser: Generating locales...
Jun 17 18:57:04 localechooser:   en_US.UTF-8... 
Jun 17 18:57:04 localechooser: up-to-date
Jun 17 18:57:04 localechooser: Generation complete.
Jun 17 18:57:05 base-installer: info: kernel linux-signed-generic usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-generic-lts-quantal usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-generic-lts-quantal-eol-upgrade usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-generic-lts-raring usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-generic-lts-raring-eol-upgrade usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-generic-lts-saucy usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-generic-lts-saucy-eol-upgrade usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-generic-lts-trusty usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-generic usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-generic-lts-quantal usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-generic-lts-quantal-eol-upgrade usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-generic-lts-raring usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-generic-lts-raring-eol-upgrade usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-generic-lts-saucy usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-generic-lts-saucy-eol-upgrade usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-generic-lts-trusty usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-server usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-virtual usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-image-generic usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-image-generic-lts-quantal usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-image-generic-lts-raring usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-image-generic-lts-saucy usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-image-generic-lts-trusty usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-extra-3.13.0-24-generic usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-extra-virtual usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-generic usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-generic-lts-quantal usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-generic-lts-raring usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-generic-lts-saucy usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-generic-lts-trusty usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-lowlatency not usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-server usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-virtual usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-signed-image-3.13.0-24-generic usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-3.13.0-24-lowlatency not usable on em64t-p4
Jun 17 18:57:05 base-installer: info: kernel linux-image-3.13.0-24-generic usable on em64t-p4
Jun 17 18:57:05 base-installer: info: Found kernels 'linux-signed-generic,linux-signed-generic-lts-quantal,linux-signed-generic-lts-quantal-eol-upgrade,linux-signed-generic-lts-raring,linux-signed-generic-lts-raring-eol-upgrade,linux-signed-generic-lts-saucy,linux-signed-generic-lts-saucy-eol-upgrade,linux-signed-generic-lts-trusty,linux-generic,linux-generic-lts-quantal,linux-generic-lts-quantal-eol-upgrade,linux-generic-lts-raring,linux-generic-lts-raring-eol-upgrade,linux-generic-lts-saucy,linux-gen
Jun 17 18:57:05 base-installer: info: arch_kernel candidates: linux-generic linux-image-generic linux-server linux-image-server linux-virtual linux-image-virtual linux-xen linux-image-xen linux-preempt linux-image-preempt linux-rt linux-image-rt
Jun 17 18:57:05 base-installer: info: arch_kernel: linux-generic (present)
Jun 17 18:57:05 base-installer: info: Using kernel 'linux-generic'
Jun 17 18:57:05 base-installer: warning: Failed to get debconf answer 'base-installer/kernel/linux/initrd'.
Jun 17 18:57:05 base-installer: info: Setting do_initrd='yes'.
Jun 17 18:57:05 base-installer: info: Setting link_in_boot='no'.
Jun 17 18:57:05 in-target: Reading package lists...
Jun 17 18:57:05 in-target: 
Jun 17 18:57:05 in-target: Building dependency tree...
Jun 17 18:57:05 in-target: 
Jun 17 18:57:05 in-target: busybox-initramfs is already the newest version.
Jun 17 18:57:05 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Jun 17 18:57:06 kernel: [  867.324637] usb 5-2: USB disconnect, device number 15
Jun 17 18:57:06 in-target: Reading package lists...
Jun 17 18:57:06 in-target: 
Jun 17 18:57:06 in-target: Building dependency tree...
Jun 17 18:57:06 in-target: 
Jun 17 18:57:06 in-target: initramfs-tools is already the newest version.
Jun 17 18:57:06 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Jun 17 18:57:06 in-target: Reading package lists...
Jun 17 18:57:06 in-target: 
Jun 17 18:57:06 in-target: Building dependency tree...
Jun 17 18:57:06 in-target: 
Jun 17 18:57:06 in-target: The following extra packages will be installed:
Jun 17 18:57:06 in-target:   crda libnl-3-200 libnl-genl-3-200 linux-firmware linux-headers-3.13.0-24
Jun 17 18:57:06 in-target:   linux-headers-3.13.0-24-generic linux-headers-generic
Jun 17 18:57:06 in-target:   linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Jun 17 18:57:06 in-target:   linux-image-generic wireless-regdb
Jun 17 18:57:06 in-target: Suggested packages:
Jun 17 18:57:06 in-target:   fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
Jun 17 18:57:06 in-target: Recommended packages:
Jun 17 18:57:06 in-target:   iw grub-pc grub-efi-amd64 grub-efi-ia32 grub lilo
Jun 17 18:57:06 in-target: The following NEW packages will be installed:
Jun 17 18:57:06 in-target:   crda libnl-3-200 libnl-genl-3-200 linux-firmware linux-generic
Jun 17 18:57:06 in-target:   linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
Jun 17 18:57:06 in-target:   linux-headers-generic linux-image-3.13.0-24-generic
Jun 17 18:57:06 in-target:   linux-image-extra-3.13.0-24-generic linux-image-generic wireless-regdb
Jun 17 18:57:06 in-target: 0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Jun 17 18:57:06 in-target: Need to get 80.2 MB of archives.
Jun 17 18:57:06 in-target: After this operation, 330 MB of additional disk space will be used.
Jun 17 18:57:06 in-target: WARNING: The following packages cannot be authenticated!
Jun 17 18:57:06 in-target:   libnl-3-200 libnl-genl-3-200 linux-image-3.13.0-24-generic wireless-regdb
Jun 17 18:57:06 in-target:   crda linux-firmware linux-image-extra-3.13.0-24-generic linux-image-generic
Jun 17 18:57:06 in-target:   linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
Jun 17 18:57:06 in-target:   linux-headers-generic linux-generic
Jun 17 18:57:06 in-target: E: There are problems and -y was used without --force-yes
Jun 17 18:57:06 in-target: Reading package lists...
Jun 17 18:57:06 in-target: 
Jun 17 18:57:06 in-target: Building dependency tree...
Jun 17 18:57:06 in-target: 
Jun 17 18:57:06 in-target: The following extra packages will be installed:
Jun 17 18:57:06 in-target:   linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
Jun 17 18:57:06 in-target: The following NEW packages will be installed:
Jun 17 18:57:06 in-target:   linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
Jun 17 18:57:06 in-target:   linux-headers-generic
Jun 17 18:57:06 in-target: 0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Jun 17 18:57:06 in-target: Need to get 9,581 kB of archives.
Jun 17 18:57:06 in-target: After this operation, 76.5 MB of additional disk space will be used.
Jun 17 18:57:06 in-target: WARNING: The following packages cannot be authenticated!
Jun 17 18:57:06 in-target:   linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
Jun 17 18:57:06 in-target:   linux-headers-generic
Jun 17 18:57:06 in-target: E: There are problems and -y was used without --force-yes
Jun 17 18:57:07 base-installer: error: exiting on error base-installer/kernel/failed-install
Jun 17 18:57:07 kernel: [  868.987617] usb 5-2: new low-speed USB device number 16 using uhci_hcd
Jun 17 18:57:08 kernel: [  869.570337] usb 5-2: New USB device found, idVendor=046d, idProduct=c06a
Jun 17 18:57:08 kernel: [  869.570342] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 17 18:57:08 kernel: [  869.570346] usb 5-2: Product: USB Optical Mouse
Jun 17 18:57:08 kernel: [  869.570348] usb 5-2: Manufacturer: Logitech
Jun 17 18:57:08 kernel: [  869.585527] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input19
Jun 17 18:57:08 kernel: [  869.585973] hid-generic 0003:046D:C06A.0011: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.3-2/input0
Jun 17 18:57:24 main-menu[538]: WARNING **: Configuring 'bootstrap-base' failed with error code 1
Jun 17 18:57:24 main-menu[538]: WARNING **: Menu item 'bootstrap-base' failed.
Jun 17 18:57:29 main-menu[538]: INFO: Modifying debconf priority limit from 'high' to 'medium'
Jun 17 18:57:29 debconf: Setting debconf/priority to medium
Jun 17 18:57:40 main-menu[538]: INFO: Menu item 'save-logs' selected
Jun 17 18:58:08 kernel: [  929.786697] usb 5-2: USB disconnect, device number 16
Jun 17 18:58:10 kernel: [  931.233684] usb 5-2: new low-speed USB device number 17 using uhci_hcd
Jun 17 18:58:10 kernel: [  931.612506] usb 5-2: New USB device found, idVendor=046d, idProduct=c06a
Jun 17 18:58:10 kernel: [  931.612511] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 17 18:58:10 kernel: [  931.612514] usb 5-2: Product: USB Optical Mouse
Jun 17 18:58:10 kernel: [  931.612517] usb 5-2: Manufacturer: Logitech
Jun 17 18:58:10 kernel: [  931.627695] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input20
Jun 17 18:58:10 kernel: [  931.628137] hid-generic 0003:046D:C06A.0012: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.3-2/input0
Jun 17 18:59:10 kernel: [  991.752912] usb 5-2: USB disconnect, device number 17
Jun 17 18:59:12 kernel: [  993.275785] usb 5-2: new low-speed USB device number 18 using uhci_hcd
Jun 17 18:59:12 kernel: [  993.451784] usb 5-2: New USB device found, idVendor=046d, idProduct=c06a
Jun 17 18:59:12 kernel: [  993.451789] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 17 18:59:12 kernel: [  993.451792] usb 5-2: Product: USB Optical Mouse
Jun 17 18:59:12 kernel: [  993.451795] usb 5-2: Manufacturer: Logitech
Jun 17 18:59:12 kernel: [  993.466950] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input21
Jun 17 18:59:12 kernel: [  993.467365] hid-generic 0003:046D:C06A.0013: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.3-2/input0
```

---

