---
title: "usb devices wil not list"
date: 2020-04-17
forum: Virtualisation
---

### Post by Ofloo on 2020-04-17
Yes, I've rebooted the system after I added my user to vboxusers

```
id
UID=1000(ofloo) GID=1000(ofloo) groepen=1000(ofloo),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),113(netdev),118(lpadmin),120(scanner),127(sambashare),129(vboxusers),130(vboxsf)

```

```
vboxmanage list usbhost
Host USB Devices:

<none>

```

```
vboxmanage --version
5.2.34_Ubuntur133883

```

```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.4 LTS
Release:	18.04
Codename:	bionic

```

```
lsmod|grep -i vbox
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  2 vboxnetadp,vboxnetflt

```

```
dpkg -l|grep -i virtualbox
ii  virtualbox                               5.2.34-dfsg-0~ubuntu18.04.1                         amd64        x86 virtualization solution - base binaries
ii  virtualbox-dkms                          5.2.34-dfsg-0~ubuntu18.04.1                         all          x86 virtualization solution - kernel module sources for dkms
ii  virtualbox-ext-pack                      5.2.34-1~ubuntu18.04.1                              all          extra capabilities for VirtualBox, downloader.
ii  virtualbox-guest-additions-iso           5.2.34-1~ubuntu18.04.1                              all          guest additions iso image for VirtualBox
ii  virtualbox-guest-utils                   5.2.34-dfsg-0~ubuntu18.04.1                         amd64        x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                     5.2.34-dfsg-0~ubuntu18.04.1                         amd64        x86 virtualization solution - X11 guest utilities
ii  virtualbox-qt                            5.2.34-dfsg-0~ubuntu18.04.1                         amd64        x86 virtualization solution - Qt based user interface

```

It's been doing this for a while now but I can't seem to figure out why that is. They do list as root, .. I would add strace of vboxmanage list usbhost but the log file is to big, let me know if you want it.

---

### Post by Ofloo on 2020-04-18
Tried the same thing with kernel 5.3 and virtualbox 6.1 but it's the same problem. Tried changing the flags of the /dev/vboxusb directory to my user again without luck.

---

### Post by #&amp;thj^% on 2020-04-18
By the way what command did you use to add your user?
There's a lot of things that can go wrong when sharing USB to guests. In any case, the checklist I did was:
[list]
    [*]install the Extension Pack on the host and Guest Additions on the guest.
    [*]added current user to vboxusers group.
    [*]manually add the corresponding USB filter in VirtualBox settings and only connect the device after finish booting the guest OS.
    [*]under VirtualBox, select USB 3.0 (xHCI) Controler.[/list]
Good Luck.

---

