---
title: "Wanted Features &amp; Issues for Ubuntu 11.10"
date: 2012-03-17
forum: The Cafe
---

### Post by rwonder on 2012-03-17
I wasn't sure where to post my issues with the OS.  But they are here now.

1) Alt-Tab causes the OS to crash
2) Battery life significantly reduced on my laptop

Then I have two features that I want.
1) When my browser is selected and is active, I like how in windows I can press backspace to go back a page
2) When closing the lid of my laptop Ubuntu doesn't automatically go into sleep mode...found that out the hard way :(

---

### Post by JDShu on 2012-03-17
Alt-Tab: File a bug, that shouldn't happen.

Battery Life: This may need some digging, you should ask about it on the forums.

Backspace For Back: This is a browser setting, it's not hard to change.

Suspend on Close: This is a nontrivial problem that has plagued Linux developers for years. It's model specific, so you should probably do some research into what the problem is for your particular model.

---

### Post by rwonder on 2012-03-17
Alt-Tab: Where do i report bugs? Cuz this bug sucks!

Battery Life: All 7 laptops I have run Ubuntu on have had 1/2 the battery life compared to Windows OS.

Backspace For Back: I don't think that is a browser setting.  Or if it is, it shouldn't be.  With Windows I've never had to configure anything. 

Suspend on Close: like the model of my laptop or processor?

---

### Post by philinux on 2012-03-17
> **rwonder said:**
> Alt-Tab: Where do i report bugs? Cuz this bug sucks!

Battery Life: All 7 laptops I have run Ubuntu on have had 1/2 the battery life compared to Windows OS.

Backspace For Back: I don't think that is a browser setting.  Or if it is, it shouldn't be.  With Windows I've never had to configure anything. 

Suspend on Close: like the model of my laptop or processor?

Full laptop specs would help ;)

---

### Post by rwonder on 2012-03-17
___@Ryan:~$ hwinfo --short
> hal.1: read hal dataprocess 3725: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
cpu:                                                            
                       Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz, 2200 MHz
                       Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz, 800 MHz
                       Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz, 800 MHz
                       Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz, 800 MHz
                       Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz, 800 MHz
                       Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz, 800 MHz
                       Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz, 800 MHz
                       Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz, 800 MHz
keyboard:
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      ETPS/2 Elantech Touchpad
graphics card:
                       Intel VGA compatible controller
sound:
                       Intel Audio device
storage:
                       Intel SATA controller
network:
  wlan0                Atheros WLAN controller
  eth0                 Attansic Ethernet controller
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wlan0                WLAN network interface
disk:
  /dev/sda             TOSHIBA MK7559GS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda4            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             Slimtype DVD A  DS8A8SH
usb controller:
                       Intel USB Controller
                       Intel USB Controller
                       USB Controller
bios:
                       BIOS
bridge:
                       Intel Host bridge
                       Intel PCI bridge
                       Intel PCI bridge
                       Intel PCI bridge
                       Intel PCI bridge
                       Intel ISA bridge
hub:
                       Linux 3.0.0-16-generic ehci_hcd EHCI Host Controller
                       Linux 3.0.0-16-generic ehci_hcd EHCI Host Controller
                       Linux 3.0.0-16-generic xhci_hcd xHCI Host Controller
                       Linux 3.0.0-16-generic xhci_hcd xHCI Host Controller
                       Hub
                       Hub
memory:
                       Main Memory
bluetooth:
                       Atheros Bluetooth Device
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel Communication controller
                       Intel SMBus
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
  /dev/input/event7    Azurewave USB 2.0 UVC VGA WebCam

---

### Post by rwonder on 2012-03-17
FYI...Like I said I ran Ubuntu on 6 Dell laptops previous to this: 3 Inspiron's and 3 XPS systems.

Just thought I would add that I hate Dell, Dell sucks!

---

### Post by JDShu on 2012-03-17
> **rwonder said:**
> Alt-Tab: Where do i report bugs? Cuz this bug sucks!


I suspect it's either an ubuntu bug, or something wrong with your system configuration. File a bug with Ubuntu.

> 
Battery Life: All 7 laptops I have run Ubuntu on have had 1/2 the battery life compared to Windows OS.


This could be any number of issues. One general solution might be to install the [Jupiter]("http://www.jupiterapplet.org/") applet. Again, ask on the support forums and give specific details.

> 
Backspace For Back: I don't think that is a browser setting.  Or if it is, it shouldn't be.  With Windows I've never had to configure anything. 


Assuming you're on Firefox, type in "about:config" in the address bar, search for "backspace" in the filter, and there should be a preference named "browser.backspace_action". Double click on it and change the value to 0, and you will get the behavior you want.

Whether it should be on by default is up for debate, I remember using it in Windows, but I never missed it.

> 
Suspend on Close: like the model of my laptop or processor?

Yes, and ask about it on the support forums where people are more likely to help.

---

