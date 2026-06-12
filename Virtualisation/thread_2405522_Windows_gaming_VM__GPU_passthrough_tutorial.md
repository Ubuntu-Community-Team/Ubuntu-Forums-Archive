---
title: "Windows gaming VM / GPU passthrough tutorial"
date: 2018-11-07
forum: Virtualisation
---

### Post by heiko_s on 2018-11-07
"The Virtualisation Mega-Thread" sticky on the top of this forum seems a little outdated (2008).

I've written a tutorial on how to install Windows 10 as a virtual machine on Ubuntu / Linux Mint and passing through a graphics card to the VM. The idea is to run Windows (or any other guest OS) on Linux without any significant performance penalty, which makes dual-boot obsolete.

Here is the tutorial: [Running Windows 10 on Linux using KVM with VGA Passthrough]("https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/")

The tutorial uses a script to start the Windows VM, whereas many other tutorials use virt-manager and then hack the resulting xml configuration file to make things actually work. I found the GUI method less intuitive and more error prone, and it took a lot more work to get the best performance out of my Windows VM. Eventually I hope to write another tutorial using the virt-manager GUI.

I thought sharing the tutorial might be relevant for this forum/community.

---

### Post by T.J. on 2018-11-07
Good evening, Heiko_s!

Your tag seems familiar.. Have we met?  I have some experience in this area and would be happy to volunteer information.  

I must SUGGEST caution on the idea that > [LEFT][COLOR=#000000][FONT=Ubuntubeta]run Windows (or any other guest OS) on Linux without any significant performance penalty, which makes dual-boot obsolete.[/FONT][/COLOR][/LEFT]
.  It  is a very specious claim.  It has been made often in the community, but in my experience, the reality is different. Depending on hardware and other factors, there will ALWAYS be some overhead, even if it is marginal.  What I would say is that you can achieve excellent performance with an acceptable overhead.  Furthermore, to make it work, requires some specific hardware, as not all chipsets support IOMMU.

There is much more up to date material on this subject already, and if I might make a suggestion, you might save some time in examining those threads and linking some here.

---

### Post by heiko_s on 2018-11-10
@T.J. - yes, I think we met before on the web. I would definitely love you to share information.

About performance of a Windows or Linux VM: I've run probably hundreds of benchmarks with different Windows VM configurations. I usually achieve somewhere between 95-100% of the performance of a bare-metal Windows installation. In practice, there is no difference I can feel between running a Windows VM and having Windows installed directly on my hardware.

A tricky part is audio, but even that can be overcome. At least in my configuration it works fine.

Regarding tutorials, there are plenty, I agree. Some are very straightforward and focus on the fastest way to success. Most tutorials use virt-manager, and hack the xml file. Some even run benchmarks for comparison. Yet, many tutorials fall short on providing help when things aren't working out that well. As you noticed, performance can vary, and getting top-notch performance requires often much more research and trial and error than most people are prepared to undertake.

Regarding IOMMU, it doesn't make sense to try VGA passthrough on old or non-compliant hardware. Many games, VR, or photo/video editing are quite demanding on the PC hardware. Now, those who need Windows only to run MS Office or similar are better served by VirtualBox - much easier to set up and simple hardware requirements.

> There is much more up to date material on this subject already, and if I might make a suggestion, you might save some time in examining those threads and linking some here. Please share some links.

---

### Post by T.J. on 2018-11-27
I've used this sort of script in the past.  It's been awhile.  I had to run Windows on the metal for about 18 months, for a variety of reasons.  Sometimes, being a developer sucks.  You have to work with things you don't like.  I apologise for my tardiness in responding.  I've been grinding Java the last few weeks.

```
[COLOR=#000000][FONT=&amp]#!/bin/sh

[/FONT][/COLOR]export QEMU_AUDIO_DRV=pa

/usr/bin/qemu-system-x86_64 -enable-kvm -m 8192 -cpu host,kvm=off \
-smp 3,sockets=1,cores=3,threads=1 \
-machine q35,accel=kvm \
-device qxl \
-usb \
-device usb-mouse \
-device usb-kbd \
-soundhw hda \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=04:00.1,bus=root.1,addr=00.1 \
-device virtio-blk-pci,scsi=off,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=0 \
-device virtio-blk-pci,scsi=off,addr=0x8,drive=drive-virtio-disk1,id=virtio-disk1 \
-drive file=/usr/local/VM/Games.img,if=none,id=drive-virtio-disk1,format=raw,media=disk \
-drive file=/usr/local/VM/DevMach.qcow2,if=none,id=drive-virtio-disk0,format=qcow2,media=disk \
-netdev tap,id=user.0 \
-device virtio-net-pci,netdev=user.0,mac=52:54:00:58:ba:9c \
-boot order=c \
-usbdevice host:9.2 \
-rtc base=localtime,driftfix=slew

 [COLOR=#000000][FONT=&amp]wait[/FONT][/COLOR]
```

The script is far from new, nor is it exceptional in any way.  There is one thing I'd like to point out and that is the qxl device.  When you are not using Spice with qemu, this creates an X11 window that will capture keyboard and mouse data. Focus can released  with keystrokes, so that a third party software like Synergy is not required.  You can also avoid Virt-manager/libvirt, which can cause some gaming issues.

---

### Post by T.J. on 2018-11-27
I'm back on Linux after a messy divorce from the latest version of Windows 10.

---

### Post by T.J. on 2018-11-27
I do not recommend Windows 10  for passthrough if you have a choice.  Windows 10 likes to spawn lots of processes to eat at CPU time, and you end up climbing through it, disabling crap. I'd go with 7 instead if possible.

---

