---
title: "Ubuntu Dom0 pciback not working"
date: 2012-10-14
forum: Virtualisation
---

### Post by fireoptic on 2012-10-14
For the past few days I have been trying to setup an Ubuntu Dom0 with a  Windows 7 DomU and have run into many issues. The current roadblock has  me stumped however and I need some pointers. I started with a fresh  install from liveusb, fully updated and ran,

```

sudo apt-get update
sudo apt-get install xen-hypervisor-amd64 libvirt-bin virt-manager
sudo update-grub

```All  of this left me with a working Xen Ubuntu Dom0 but no screens would  work at startx. I activated the FGLRX AMD driver and bingo screens  worked in Xen Ubuntu Dom0.  So with that sorted I made a config file for  a Windows 7 HVM,

```

kernel = "hvmloader"
builder='hvm'
memory = 8192
name = "win7a"
vcpus=5
pae=1
acpi=1
apic=1
vif = [ 'type=ioemu, bridge=virbr0' ]
disk = [ 'phy:sdc,ioemu:hdc,w' ]
device_model = 'qemu-dm'
boot="dc"
sdl=0
opengl=1
vnc=1
vncpasswd=''
stdvga=0
#nographic=1 
serial='pty'
tsc_mode=0
soundhw='all'
usb=1
usbdevice='mouse'
gfx_passthru=0
pci=[ '08:00.0', '08:00.1' , '04:00.0' ]

```The  pci=*** is my 7970 its onboard audio and my usb3 controller which is  keyboard and mouse. I will be adding my Soundblaster X-fi later. I am  using an existing windows 7 install to run from currently though I do  not think I will be able to get it running as it crashes the VM on  classPNP.sys load in boot. 

The issue I need help with is  pciback. No matter what I do, weather adding in grub command line or in  /etc/modprobe.d/options.conf, I cannot get pciback to seize the devices  and thereby pass them along to the VM.  All I get is this error about  pciback and pcistub not owning the device, NOTE this error output is  only for 08:00.0 I removed the others in testing but the error is the  same for all decives. 

```

Error starting domain: POST  operation failed: xend_post: error from xen daemon: (xend.err "pci: PCI  Backend and pci-stub don't own device 0000:08:00.0")

details

Error  starting domain: POST operation failed: xend_post: error from xen  daemon: (xend.err "pci: PCI Backend and pci-stub don't own device  0000:08:00.0")

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 45, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 66, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1120, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 551, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError:  POST operation failed: xend_post: error from xen daemon: (xend.err  "pci: PCI Backend and pci-stub don't own device 0000:08:00.0")

```After changing to the xl toolstack and running,

```

sudo xl pci-assignable-add 08:00.0 

```I get the error of command not implemented yet, or  something like that. The next best thing I can think of to do is install  xen from source. I have tried with fedora 16/17 and Ubuntu 11.10, same  result in 11.10 could not even get xserver to start with xen in fedora.

I  am going to scrap the whole install and try again from source tomorrow  unless someone has some idea on where to go from here. My google is worn  out for the night but I will be checking back in soon.

Thanks in advance.

Spec's
Amd 1100t @ 4.3ghz IOMMU 
ASUS M4A89TD PRO USB3 *Confirmed IOMMU support by Xen team*
16gb G.Skill Ripjaws X ddr3 9-9-9-24 1600
Sapphire Radeon HD 7970 3gb Domu windows 
Sapphire Radeon HD 6870 1gb Dom0 Ubuntu

---

### Post by fireoptic on 2012-10-14
Well on to build from source then I will post results when I have them.  ](*,)

---

