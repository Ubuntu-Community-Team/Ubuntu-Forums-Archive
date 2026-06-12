---
title: "XEN PCI Passthrough of USB Controller is not working anymore after Upgrade 16.04"
date: 2016-09-11
forum: Virtualisation
---

### Post by alexander-stockmann on 2016-09-11
Hello Everybody,

this is my first post here and I will try to do it right. So please be gentle! :)

I have/had a server with the following specs:

Dom0=Ubuntu 14.04 LTS
DomU1=Ubuntu 14.04 LTS as HVM Guest
DomU2=IPFire

I did a PCI pass-through of the USB Controller to use a USB 3 Hardrive in DomU1 and it worked very good all the time.

Than two days ago I wanted to upgrade to Ubuntu 16.04 to get XEN 4.6.

Firstly I upgraded the System in DomU1 and everything went well.

After Upgrade Dom0 to Ubuntu 16.04 I ran into troubles....

1. I configured the Dom0 to hide the related PCI devices

    00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
    04:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
    
    via entries in:

    - /etc/initramfs-tools/modules
            xen-platform-pci    
            xen-pciback passthrough=1 hide=(04:00.0)(00:02.0)(00:03.0)(00:1b.0)(00:14.0)(00:1d.0)

    - /etc/default/grub

            GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT="xen-pciback.hide=(04:00.0)(00:14.0)     
            (00:02.0)(00:03.0)(00:1b.0)(00:1d.0)"

    - with a script in rc.local I execute during boot the following:
            
            xl pci-assignable-add 00:14.0
            xl pci-assignable-add 00:1d.0

2. After reboot I checked the settings with **xl pci-assignable-list**

    - the related PCI defices are shown as available

3. DomU2 started and the  04:00.0 Network controller was passed through like expected

4. DomU1 started and I wasn't able to see the HDD and PEN drive which are connected to the USB Controller

    - I tried to discover the root course with Dmesg and I saw the following for DomU1 which could be strange:

[code type="xml"][    0.220195] usbcore: registered new interface driver usbfs
[    0.220195] usbcore: registered new interface driver hub
[    0.220195] usbcore: registered new device driver usb
[    0.615884] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.615886] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.615887] usb usb1: Product: xHCI Host Controller
[    0.615888] usb usb1: Manufacturer: Linux 4.4.0-36-generic xhci-hcd
[    0.615889] usb usb1: SerialNumber: 0000:00:05.0
[    0.620301] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.620302] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.620303] usb usb2: Product: xHCI Host Controller
[    0.620303] usb usb2: Manufacturer: Linux 4.4.0-36-generic xhci-hcd
[    0.620304] usb usb2: SerialNumber: 0000:00:05.0
[   15.868461] usb usb1-port4: couldn't allocate usb_device
[   35.900462] usb usb2-port1: couldn't allocate usb_device
[   55.932463] usb usb1-port8: couldn't allocate usb_device[/code]

[code type="xml"][   56.908037] piix4_smbus 0000:00:01.3: SMBus Host Controller not enabled![/code]



At the end I gave up because I don’t have a clue what to do here because everything should be the same like it was before the upgrade to Ubuntu 16.04 and XEN4.6!



please give me a hint! If you need more information let me know.

Thanks so much and greetings,

Alex

---

