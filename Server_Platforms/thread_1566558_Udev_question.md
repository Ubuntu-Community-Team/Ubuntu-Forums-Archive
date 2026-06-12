---
title: "Udev question"
date: 2010-09-02
forum: Server Platforms
---

### Post by bgrabbe on 2010-09-02
I have a server with a boot disk and 18 hard drives in it that I'm trying to set up raid arrays. 
Os is ubuntu 2.6.32. 
I haven't yet been able to tell why, but occasionally when I reboot the physical disks are remapped t different device names.For example, the boot drive is usually /dev/sda, but yesterday, at different times it came up as /dev/sde and /dev/sdf. 

Needless to say this is creating havoc with my raid arrays. I'm looking at udev to see if I could use it to more permanent device names, based on the disk serial number. I know which seria number is in which slot of the computer, and udevadm info will tell me which device maps to which serial number. 
I know I might be able to use the uuid with mdadm to have the arrays be more permanently mapped, but udev really seems like a better answer, if I could get it to work. 

I have a udev rule to try to set one of the drives to a persistent device name, like this:
KERNEL=="sd*[!0-9]", SUBSYSTEM=="block",  ENV{ID_SERIAL_SHORT}=="9QJ5SGPV", SYMLINK+="diskr",  ENV{GENERATED}="1"
This seems like I should get a symlink to the device name diskr for the hard drive that has this serial number. In testing this I get an error "unable to open device '/sys/dev/sdr' "
Udev_root is set to the default, /dev, so I don't really understand the erro. 
Is there anyone familiar enough with udev to be able to offer help ?
Thanks

---

### Post by de0xyrib0se on 2010-09-02
Devices are shown as they are reported by your hardware, Ubuntu itself is not shuffling the drives.

Also use a hardware based raid controller.

---

### Post by bgrabbe on 2010-09-03
That's an unbelievably helpful response. Do you always answer questions so uselessly ?

---

### Post by de0xyrib0se on 2010-09-03
That's an unbelievably useless way to solve something which is caused by faulty hardware/bios.

---

