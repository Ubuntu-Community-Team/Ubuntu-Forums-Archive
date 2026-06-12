---
title: "libvirt + OVMF - Cannot persist boot order"
date: 2018-05-11
forum: Virtualisation
---

### Post by fredsmith456 on 2018-05-11
(Ubuntu 18.04 LTS)

Hello!

I can't get my EFI variables in the OVMF EFI firmware to persist - any changes I make in the textual interface of the EFI firmware are lost the moment I leave the interface. I understand my use-case is a bit unusual, but nevertheless there seems to be a problem here.

This is my use case/setup:
- I am attempting to have a single Windows 10 partition to boot natively (via GRUB option/dual-booting) as well as in a VM
- I am passing through my entire root drive (with both Ubuntu + Win10 partitions) to QEMU by passing through the entire block device found in /dev/disk/by-id/
- I am unmounting the EFI System Partition from the Ubuntu host every time I need to start up the VM
- I have an OVMF-based VM setup (using virt-manager & hence libvirt) to boot the Win10 partition
- I can currently boot the Win10 partition by booting first into rEFInd (via virtual CD drive + ISO) then selecting the Win10 bootloader
- I can also boot directly into Win10 by going into the EFI textual interface and selecting boot from ESP:/EFI/Boot/Microsoft/Boot/bootmgfw.efi
- When I change any settings inside the textual interface (boot order, inserting a new entry for the above bootmgfw.efi file, boot timeout are the ones I've tried), it 'saves' but then a reboot (without even killing the QEMU session) shows default settings again
- I would like to set a default boot order of the windows EFI file (bootmgfw.efi), as I won't be using this VM to boot the Ubuntu partition that the host is running off of (that would lead to file corruption obviously). I don't want to continue using this hacky rEFInd or manual selection through textual interface workflow - I'm sure to forget one time and crash my system.

I have made sure:
- Ubuntu 18.04 uses a 'split' OVMF firmware setup, with the main firmware living under /usr/share/OVMF/OVMF_CODE.fd whereas the persistent storage portion is stored under /var/lib/libvirt/qemu/nvram/<vm-name>_VARS.fd ([ref1]("https://www.redhat.com/archives/libvirt-users/2016-March/msg00135.html"), [ref2]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=764918"))
- the <vm-name>_VARS.fd file is actually being written to (updated on usage of the VM)

I've also tried to look at the OVMF logs (using instructions found [here]("https://www.redhat.com/archives/libvirt-users/2016-March/msg00135.html")), but when I use sudo virsh edit <vm-name> to insert those lines, it complains it can't validate the XML file. If I force it to write and simply start the VM via virt-manager, I find that the debug lines are deleted by libvirt.

Is perhaps libvirt (or virt-manager) overwriting the EFI vars or somehow erasing the NVRAM file to implement the graphical boot order selection? I find that I can enable/disable the 'boot menu' option, and the settings inside the OVMF EFI textual interface will change (specifically the timeout changes from 0 to 3 seconds on 'enable' and vice versa'). Is there another way to debug OVMF other than those XML entries above?

TLDR:
I can't get the OVMF EFI boot order entries to persist, even with a split _VARS.fd file which apparently gets written to. Looking for ways to debug or other suggestions.

Thanks,
Fred

Here is the relevant part of my xml file:ref3

```
  <os>
    <type arch='x86_64' machine='pc-i440fx-bionic'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/win10_VARS.fd</nvram>
    <bootmenu enable='yes'/>
  </os>
```

---

### Post by lersek on 2018-05-12
The UEFI boot order that you set inside the guest seems not to stick because OVMF primarily obeys the boot order specification that comes from QEMU (and, less directly, from libvirt). If you want OVMF to respect the boot order set inside the guest, then you have to remove all "-device ...,bootindex=N" properties from the QEMU command line; or else, less directly, all <boot> elements from the libvirt domain XML. Please read the "boot dev=..." element documentation at [https://libvirt.org/formatdomain.html#elementsOSBIOS](https://libvirt.org/formatdomain.html#elementsOSBIOS) , and also the per-device "boot order=..." elements at [https://libvirt.org/formatdomain.html#elementsHostDev](https://libvirt.org/formatdomain.html#elementsHostDev) .

Now, to my knowledge, if you remove all of those <boot> elements from the domain XML, libvirt will forcefully re-add one, so if you are using libvirt, you cannot *not* specify a boot order to OVMF from the host side. That's fine: just locate the assigned device, and add a single <boot order='1'/> element under that. This way OVMF will attempt to boot off that device first.

Regarding the reason for which you cannot set up debug log capturing. Just "qemu:commandline" and "qemu:arg" elements aren't enough; for libvirtd to keep and understand those elements, the "qemu" namespace prefix has to be defined. And that's done in the root element of the domain XML, as follows:

<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>


Note the "xmlns:qemu=..." attribute. That's what you need in addition.

---

### Post by fredsmith456 on 2018-05-12
> **lersek said:**
> 
Now, to my knowledge, if you remove all of those <boot> elements from the domain XML, libvirt will forcefully re-add one, so if you are using libvirt, you cannot *not* specify a boot order to OVMF from the host side. That's fine: just locate the assigned device, and add a single <boot order='1'/> element under that. This way OVMF will attempt to boot off that device first.

I don't really want to do this (if I wanted this behaviour, I would have specified the boot order under virt-manager or wth libvirt), because booting directly off my SSD (using the fallback EFI file) means booting to GRUB then (after a timeout) to Ubuntu. That is because my main OS *is *Ubuntu (on my physical machine), but I want the VM to have different behaviour from booting natively. Booting a guest off a partition that the host is running off of is obviously going to lead to corruption. This is why I wanted to use OVMF's persistent functionality.

Now I suppose I could set up the fallback to boot to Windows while my physical machine is set to boot to Ubuntu with an EFI entry. I think I'll do that if no other ideas come to mind.

> **lersek said:**
> 

Note the "xmlns:qemu=..." attribute. That's what you need in addition.

I actually did have that namespace attribute, my mistake was not wrapping the <qemu:arg *> tags in <qemu:commandline> and </qemu:commandline> [FONT=arial](as in [here]("https://unix.stackexchange.com/questions/235414/libvirt-how-to-pass-qemu-command-line-args")). Once I did that, the XML validated correctly. However, I then ran into another problem: no matter what file I put under the[/FONT][FONT=arial] <qemu:arg value='file:/tmp/guest_name.log'/>[/FONT][FONT=arial] tag, I got a permission error from virt-manager (and therefore libvirt). Even changing /etc/libvirt/qemu.conf to run QEMU under the root account didn't fix it [(reference)]("https://github.com/jedi4ever/veewee/issues/996").

Error:

```
Error starting domain: internal error: process exited while connecting to monitor: 2018-05-12T16:35:54.806597Z qemu-system-x86_64: -debugcon file:/tmp/win10.ovmf.log: Could not open '/tmp/win10.ovmf.log': Permission denied

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 89, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 125, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/libvirtobject.py", line 82, in newfn
    ret = fn(self, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1508, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 1062, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: internal error: process exited while connecting to monitor: 2018-05-12T16:35:54.806597Z qemu-system-x86_64: -debugcon file:/tmp/win10.ovmf.log: Could not open '/tmp/win10.ovmf.log': Permission denied


```[/FONT]

---

### Post by KillerKelvUK on 2018-05-13
So you say "sudo virsh xxxx", have you been sudo'ing loosley and ballzed up your permissions? With a stock libvirt setup sudo is not needed to manage guests. Is the VARS file now root owned and without an ACL for the qemu user perhaps and so cannot be written to?

---

### Post by fredsmith456 on 2018-05-13
> **KillerKelvUK said:**
> So you say "sudo virsh xxxx", have you been sudo'ing loosley and ballzed up your permissions? With a stock libvirt setup sudo is not needed to manage guests. Is the VARS file now root owned and without an ACL for the qemu user perhaps and so cannot be written to?

****, I didn't know that sudo wasn't required for virsh. Okay, my permissions are:
```
# file: var/lib/libvirt/qemu/nvram/win10_VARS.fd
# owner: root
# group: root
user::rw-
group::---
other::---

```

*However,* I'm not certain this is the problem - I haven't altered the VARS.fd file by hand, and it was root:root the first time I looked (after it was created by virt-manager). It also gets written to (modified date gets updated) every time I start the VM.

---

### Post by KillerKelvUK on 2018-05-13
Yeah so libvirt's default installation is to use a separate user account named libvirt-qemu and it handles all the user group permissions necessary so that uid 1000 I believe can start/stop/manage guests using virsh without needing root privileges.  You can then go one step further and change the default user/group libvirt starts guest with via the config in /etc/libvirt/.

Anyways my VARS file is root owned when the guest is not running but when I start the guest the ownership changes to my configured user/group, it then reverts to being root owned when the guest is shutdown, in addition the parent nvram directory is owned by my uid 1000 user.

Just compared my guest xml snippet to yours and other than I'm running 17.10 my guest is using q35 chipset rather than the i440fx which yours is.

---

### Post by fredsmith456 on 2018-05-14
So, I've decided to avoid the issue entirely and not use OVMF's  persistent NVRAM to achieve the behaviour I want. Again, the behaviour I  want is for my VM to boot directly into Windows without any chance of  getting it wrong and booting into Ubuntu.

My solution is to make a  new virtual disk (using qemu-img) and edit it from the host (via  qemu-nbd to connect + mount) to contain just one partition: an EFI  system partition with rEFInd. That install of rEFInd is configured such  that it boots by default (no delay) into Windows 10 on my physical disk,  by executing the (main disk ESP)/EFI/microsoft/boot/bootmgfw.efi file.  I'm also going to configure rEFInd to not enumerate GRUB/Ubuntu at all.  That way there is no chance of mix-up, of booting into the host's Ubuntu partition. In virt-manager, I have set the  boot priority to boot from this virtual 'boot disk' first, and unchecked  all other disks.

In configuring my setup this way, I avoid  having to mess with my main drive's ESP, instead only using it to access  the Windows EFI loader. Since I've found a solution (even if it's not a  direct one), I'm marking the thread as solved.

---

