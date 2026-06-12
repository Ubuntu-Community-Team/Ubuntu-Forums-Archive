---
title: "Problem with locking/stalling GPU when passing it to VMUnknown PCI header type '127'"
date: 2018-11-24
forum: Virtualisation
---

### Post by alex346 on 2018-11-24
hello
I have configured GPU passthroiugh on Ubuntu 18.04 basing on :

[https://ycnrg.org/vga-passthrough-with-ovmf-vfio/](https://ycnrg.org/vga-passthrough-with-ovmf-vfio/)
[https://blog.zerosector.io/2018/07/28/kvm-qemu-windows-10-gpu-passthrough/](https://blog.zerosector.io/2018/07/28/kvm-qemu-windows-10-gpu-passthrough/)
etc
In short words that is something like using vfio-pci and modprobe.blacklist=amdgpu options at the bootloader.

Also has the same problem at Ubuntu 16.10 - about year ago. That frustrated me and I have putted this topic away.

But now... I have bought some new games on Black friday ! I have to run it and I really would like to resolve that problem.  I have seen some posts suggesting that could be something with power modes?

VM is Windows 10 PRO based, with up2date AMD drivers. Virt-manager running as root.

[U][B]When restarting or destroying the VM (via virt-manager, virsh) about 0.5sec after the stopping VM - the fans on the GPU comes to max speed and I can't do anything more with that VM (and also the GPU).
Similar problem is when I am restarting Windows thorugh normal system restart (inside the VM).

At this stage I need to poweroff the host to bring back to using the VM with GPU.
[/B][/U]

That's the information from the message shown in virt-manager when above situation will happen:
```
[COLOR=#202124][FONT=Roboto]Error starting domain: internal error: Unknown PCI header type '127'[/FONT][/COLOR]

[COLOR=#202124][FONT=Roboto]Traceback (most recent call last):[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 89, in cb_wrapper[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    callback(asyncjob, *args, **kwargs)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 125, in tmpcb[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    callback(*args, **kwargs)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]  File "/usr/share/virt-manager/virtManager/libvirtobject.py", line 82, in newfn[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    ret = fn(self, *args, **kwargs)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]  File "/usr/share/virt-manager/virtManager/domain.py", line 1508, in startup[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    self._backend.create()[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 1062, in create[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]libvirtError: internal error: Unknown PCI header type '127'[/FONT][/COLOR]

```

That is not connected with any temperature conditions near the GPU.

There is nothing special in dmesg.

Also I am putting some log from the qemu log dir:

```
2018-11-23 23:37:38.506+0000: Domain id=2 is tainted: host-cpu2018-11-23T23:37:38.556783Z qemu-system-x86_64: -chardev pty,id=charserial0: char device redirected to /dev/pts/1 (label charserial0)
2018-11-23T23:37:57.946548Z qemu-system-x86_64: terminating on signal 15 from pid 2093 (/usr/sbin/libvirtd)
2018-11-23 23:37:59.352+0000: shutting down, reason=destroyed
2018-11-24 16:13:38.555+0000: starting up libvirt version: 4.0.0, package: 1ubuntu8.5 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Tue, 28 Aug 2018 07:26:19 +0200), qe
mu version: 2.11.1(Debian 1:2.11+dfsg-1ubuntu7.7), hostname: ubu-4690
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name guest=win7-2,debug-threads=on -S -object secret,id=master
Key0,format=raw,file=/var/lib/libvirt/qemu/domain-1-win7-2/master-key.aes -machine pc-i440fx-bionic,accel=kvm,usb=off,vmport=off,dump-guest-core=off -cpu host -drive file=/usr/s
hare/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/win7-2_VARS.fd,if=pflash,format=raw,unit=1 -m 4096 -realtime mlock=off -sm
p 2,sockets=2,cores=1,threads=1 -uuid 0188e3d0-cfd7-43b8-912d-6baf699345c5 -display none -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/do
main-1-win7-2/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=delay -no-hpet -no-s
hutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot menu=on,strict=on -device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x4.0x7 -device ich9-usb-uhci1,masterbus
=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x4 -device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x4.0x1 -device ich9-usb-uhci3,masterbus=usb.0,firstport
=4,bus=pci.0,addr=0x4.0x2 -device ahci,id=sata0,bus=pci.0,addr=0x9 -device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x5 -drive file=/dev/sdc,format=raw,if=none,id=driv
e-sata0-0-0 -device ide-hd,bus=sata0.0,drive=drive-sata0-0-0,id=sata0-0-0,bootindex=1 -drive file=/media/root/md0/Windows.iso,format=raw,if=none,id=drive-sata0-0-1,media=cdrom,r
eadonly=on -device ide-cd,bus=sata0.1,drive=drive-sata0-0-1,id=sata0-0-1,bootindex=2 -netdev tap,fd=26,id=hostnet0 -device e1000,netdev=hostnet0,id=net0,mac=52:54:00:d8:5f:84,bu
s=pci.0,addr=0x2 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -device usb-tablet,id=input0,bus=usb.0,port=1 -device intel-hda,id=sound0,bus=pci.
0,addr=0x3 -device hda-duplex,id=sound0-codec0,bus=sound0.0,cad=0 -chardev spicevmc,id=charredir0,name=usbredir -device usb-redir,chardev=charredir0,id=redir0,bus=usb.0,port=2 -
chardev spicevmc,id=charredir1,name=usbredir -device usb-redir,chardev=charredir1,id=redir1,bus=usb.0,port=3 -device usb-host,hostbus=3,hostaddr=12,id=hostdev0,bus=usb.0,port=4
-device vfio-pci,host=01:00.0,id=hostdev1,bus=pci.0,addr=0x6 -device vfio-pci,host=01:00.1,id=hostdev2,bus=pci.0,addr=0x7 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0
x8 -msg timestamp=on
2018-11-24 16:13:38.555+0000: Domain id=1 is tainted: host-cpu
2018-11-24T16:13:38.606440Z qemu-system-x86_64: -chardev pty,id=charserial0: char device redirected to /dev/pts/2 (label charserial0)
2018-11-24T16:15:43.027597Z qemu-system-x86_64: terminating on signal 15 from pid 1981 (/usr/sbin/libvirtd)
2018-11-24 16:15:44.634+0000: shutting down, reason=destroyed
2018-11-24 18:34:25.326+0000: shutting down, reason=failed
2018-11-24 18:34:36.051+0000: starting up libvirt version: 4.0.0, package: 1ubuntu8.5 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Tue, 28 Aug 2018 07:26:19 +0200), qe
mu version: 2.11.1(Debian 1:2.11+dfsg-1ubuntu7.7), hostname: ubu-4690
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name guest=win7-2,debug-threads=on -S -object secret,id=master
Key0,format=raw,file=/var/lib/libvirt/qemu/domain-2-win7-2/master-key.aes -machine pc-i440fx-bionic,accel=kvm,usb=off,vmport=off,dump-guest-core=off -cpu host -drive file=/usr/s
hare/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/win7-2_VARS.fd,if=pflash,format=raw,unit=1 -m 4096 -realtime mlock=off -sm
p 2,sockets=2,cores=1,threads=1 -uuid 0188e3d0-cfd7-43b8-912d-6baf699345c5 -display none -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/do
main-2-win7-2/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=delay -no-hpet -no-s
hutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot menu=on,strict=on -device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x4.0x7 -device ich9-usb-uhci1,masterbus
=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x4 -device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x4.0x1 -device ich9-usb-uhci3,masterbus=usb.0,firstport
=4,bus=pci.0,addr=0x4.0x2 -device ahci,id=sata0,bus=pci.0,addr=0x9 -device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x5 -drive file=/dev/sdc,format=raw,if=none,id=driv
e-sata0-0-0 -device ide-hd,bus=sata0.0,drive=drive-sata0-0-0,id=sata0-0-0,bootindex=1 -drive file=/media/root/md0/Windows.iso,format=raw,if=none,id=drive-sata0-0-1,media=cdrom,r
eadonly=on -device ide-cd,bus=sata0.1,drive=drive-sata0-0-1,id=sata0-0-1,bootindex=2 -netdev tap,fd=26,id=hostnet0 -device e1000,netdev=hostnet0,id=net0,mac=52:54:00:d8:5f:84,bu
s=pci.0,addr=0x2 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -device usb-tablet,id=input0,bus=usb.0,port=1 -device intel-hda,id=sound0,bus=pci.
0,addr=0x3 -device hda-duplex,id=sound0-codec0,bus=sound0.0,cad=0 -chardev spicevmc,id=charredir0,name=usbredir -device usb-redir,chardev=charredir0,id=redir0,bus=usb.0,port=2 -
chardev spicevmc,id=charredir1,name=usbredir -device usb-redir,chardev=charredir1,id=redir1,bus=usb.0,port=3 -device usb-host,hostbus=3,hostaddr=12,id=hostdev0,bus=usb.0,port=4
-device vfio-pci,host=01:00.0,id=hostdev1,bus=pci.0,addr=0x6 -device vfio-pci,host=01:00.1,id=hostdev2,bus=pci.0,addr=0x7 -device usb-host,hostbus=3,hostaddr=2,id=hostdev3,bus=u
sb.0,port=5 -device usb-host,hostbus=3,hostaddr=3,id=hostdev4,bus=usb.0,port=6 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8 -msg timestamp=on
2018-11-24 18:34:36.051+0000: Domain id=2 is tainted: host-cpu
2018-11-24T18:34:36.110767Z qemu-system-x86_64: -chardev pty,id=charserial0: char device redirected to /dev/pts/1 (label charserial0)
2018-11-24T18:39:30.431954Z qemu-system-x86_64: warning: guest updated active QH



```

What can I do to manage that problem? Is there any solution allows to restart the pciex bus maybe?

regards.

---

### Post by alex346 on 2018-11-28
bump

---

### Post by alex346 on 2018-12-03
bump again :)

---

### Post by alex346 on 2018-12-20
please, help

---

### Post by heiko_s on 2018-12-21
Unfortunately libvirt / virt-manager make the debugging process unnecessary complicated.

See if the following helps: [https://forums.unraid.net/topic/69373-graphics-card-reset-issue-amd/]("https://forums.unraid.net/topic/69373-graphics-card-reset-issue-amd/")

Also, see [https://forum.level1techs.com/t/linux-host-windows-guest-gpu-passthrough-reinitialization-fix/121097]("https://forum.level1techs.com/t/linux-host-windows-guest-gpu-passthrough-reinitialization-fix/121097"). I have never tried that (usually I don't use AMD graphics), but it seems your graphics card doesn't reset upon VM shutdown.

Edit: If you care to try another method (not using virt-manager), see my tutorial here: [Running Windows 10 on Linux using KVM with VGA Passthrough]("https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/").

---

