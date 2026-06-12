---
title: "KVM / QEMU pcie Passtrough failed since new updates [AMD RX580]"
date: 2017-07-23
forum: Virtualisation
---

### Post by th3r3al on 2017-07-23
Hey,

since april I am using an ubuntu mate 17.04 pcie passtrough setup with vfio. Since the latest updates my gpu passtrough is not working anymore, Windows seems to be not responsable anymore and my monitor goes blank. Only a hard reset with libvirt-manager can help at this situation... I updated on 22.07.2017 to this versions:

(/var/log/apt/history.log)

```
Start-Date: 2017-07-22  14:17:59
Commandline: apt-get upgrade
Requested-By: brian (1000)
Upgrade: libgssapi3-heimdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), vlc-bin:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), vlc-plugin-video-output:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), intel-micro
code:amd64 (3.20161104.1, 3.20170511.1~ubuntu17.04.0), libwind0-heimdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), python-samba:amd64 (2:4.5.8+dfsg-0ubuntu0.17.04.3, 2:4.5.8+dfsg-0ubuntu0.17.04.4), linu
x-libc-dev:amd64 (4.10.0-26.30, 4.10.0-28.32), vlc-plugin-samba:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), vlc-plugin-qt:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), libwbclient0:amd64 (2:4.5.8+dfsg-0ubuntu0.17.
04.3, 2:4.5.8+dfsg-0ubuntu0.17.04.4), libexpat1-dev:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), libheimntlm0-heimdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), nextcloud-client:amd64 (2.3.1-20170514.194620~zesty
1, 2.3.2-20170713.070732~zesty1), vlc-plugin-skins2:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), vlc-plugin-visualization:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), vlc-l10n:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubunt
u2.1), libheimbase1-heimdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), qemu-system-x86:amd64 (1:2.8+dfsg-3ubuntu2.2, 1:2.8+dfsg-3ubuntu2.3), vlc-plugin-notify:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1),
 libvlc5:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), flashplugin-installer:amd64 (26.0.0.131ubuntu0.17.04.1, 26.0.0.137ubuntu0.17.04.1), libepoxy0:amd64 (1.3.1-1ubuntu1.17.04.1, 1.3.1-1ubuntu1.17.04.2), libvirt-
clients:amd64 (2.5.0-3ubuntu5.1, 2.5.0-3ubuntu5.2), libspice-server1:amd64 (0.12.8-2ubuntu1, 0.12.8-2ubuntu1.1), libexpat1:amd64 (2.2.0-2, 2.2.0-2ubuntu0.1), libvlccore8:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1
), libvlc-bin:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), samba-libs:amd64 (2:4.5.8+dfsg-0ubuntu0.17.04.3, 2:4.5.8+dfsg-0ubuntu0.17.04.4), apport:amd64 (2.20.4-0ubuntu4.1, 2.20.4-0ubuntu4.5), libvirt-bin:amd64 (
2.5.0-3ubuntu5.1, 2.5.0-3ubuntu5.2), libnextcloudsync0:amd64 (2.3.1-20170514.194620~zesty1, 2.3.2-20170713.070732~zesty1), libxenstore3.0:amd64 (4.8.0-1ubuntu2.1, 4.8.0-1ubuntu2.2), python3-apport:amd64 (2.20.4-
0ubuntu4.1, 2.20.4-0ubuntu4.5), qemu-utils:amd64 (1:2.8+dfsg-3ubuntu2.2, 1:2.8+dfsg-3ubuntu2.3), libvirt-daemon-system:amd64 (2.5.0-3ubuntu5.1, 2.5.0-3ubuntu5.2), samba-common:amd64 (2:4.5.8+dfsg-0ubuntu0.17.04.
3, 2:4.5.8+dfsg-0ubuntu0.17.04.4), libhcrypto4-heimdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), vlc:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), vlc-data:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), lib
smbclient:amd64 (2:4.5.8+dfsg-0ubuntu0.17.04.3, 2:4.5.8+dfsg-0ubuntu0.17.04.4), smbclient:amd64 (2:4.5.8+dfsg-0ubuntu0.17.04.3, 2:4.5.8+dfsg-0ubuntu0.17.04.4), libxen-4.8:amd64 (4.8.0-1ubuntu2.1, 4.8.0-1ubuntu2.
2), samba-common-bin:amd64 (2:4.5.8+dfsg-0ubuntu0.17.04.3, 2:4.5.8+dfsg-0ubuntu0.17.04.4), libmysqlclient20:amd64 (5.7.18-0ubuntu0.17.04.1, 5.7.19-0ubuntu0.17.04.1), qemu-kvm:amd64 (1:2.8+dfsg-3ubuntu2.2, 1:2.8+
dfsg-3ubuntu2.3), libvirt0:amd64 (2.5.0-3ubuntu5.1, 2.5.0-3ubuntu5.2), vlc-plugin-video-splitter:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), apport-gtk:amd64 (2.20.4-0ubuntu4.1, 2.20.4-0ubuntu4.5), libroken18-he
imdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), libasn1-8-heimdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), libkrb5-26-heimdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), vlc-plugin-b
ase:amd64 (2.2.4-14ubuntu2, 2.2.4-14ubuntu2.1), nextcloud-client-l10n:amd64 (2.3.1-20170514.194620~zesty1, 2.3.2-20170713.070732~zesty1), libhx509-5-heimdal:amd64 (7.1.0+dfsg-9ubuntu1, 7.1.0+dfsg-9ubuntu1.1), qe
mu-block-extra:amd64 (1:2.8+dfsg-3ubuntu2.2, 1:2.8+dfsg-3ubuntu2.3), python3-problem-report:amd64 (2.20.4-0ubuntu4.1, 2.20.4-0ubuntu4.5), qemu-system-common:amd64 (1:2.8+dfsg-3ubuntu2.2, 1:2.8+dfsg-3ubuntu2.3), 
libvirt-daemon:amd64 (2.5.0-3ubuntu5.1, 2.5.0-3ubuntu5.2)

```
Here is some libvirt log: (/var/log/libvirt/qemu/Passtrough.log)

```
2017-07-23 20:00:59.067+0000: starting up libvirt version: 2.5.0, package: 3ubuntu5.2 (Christian Ehrhardt <christian.ehrhardt@canonical.com> Mon, 19 Jun 2017 07:52:32 +0200), qemu version: 2.8.0(Debian 1:2.8+dfsg-3ubuntu2.3), hostname: octo
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name guest=Passtrough,debug-threads=on -S -object secret,id=masterKey0,format=raw,file=/var/lib/libvirt/qemu/domain-1-Passtrough/master-key.aes -machine pc-i440fx-zesty,accel=kvm,usb=off,dump-guest-core=off -cpu Skylake-Client,hv_time,kvm=off -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/Passtrough_VARS.fd,if=pflash,format=raw,unit=1 -m 8192 -mem-prealloc -mem-path /dev/hugepages/libvirt/qemu -realtime mlock=off -smp 6,sockets=6,cores=1,threads=1 -uuid 76ad470f-e9df-48bd-9b77-abee61582fe2 -display none -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-1-Passtrough/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot menu=on,strict=on -device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x2.0x7 -device ich9-usb-uhci1,masterbus=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x2 -device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x2.0x1 -device ich9-usb-uhci3,masterbus=usb.0,firstport=4,bus=pci.0,addr=0x2.0x2 -device ahci,id=sata0,bus=pci.0,addr=0x6 -drive file=/mnt/blue/kvm-data/win-data.qcow2,format=qcow2,if=none,id=drive-virtio-disk0,cache=writeback -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x8,drive=drive-virtio-disk0,id=virtio-disk0 -drive file=/var/lib/libvirt/images/Passtrough.qcow2,format=qcow2,if=none,id=drive-virtio-disk1,cache=writeback -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x5,drive=drive-virtio-disk1,id=virtio-disk1,bootindex=1 -drive file=/var/lib/libvirt/images/Passtrough-1.qcow2,format=qcow2,if=none,id=drive-virtio-disk2 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0xa,drive=drive-virtio-disk2,id=virtio-disk2 -drive file=/home/brian/Downloads/virtio-win-0.1.126.iso,format=raw,if=none,media=cdrom,id=drive-sata0-0-1,readonly=on -device ide-cd,bus=sata0.1,drive=drive-sata0-0-1,id=sata0-0-1 -device usb-host,hostbus=1,hostaddr=3,id=hostdev0,bus=usb.0,port=1 -device vfio-pci,host=01:00.0,id=hostdev1,bus=pci.0,addr=0x3 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x4 -msg timestamp=on
2017-07-23T20:07:34.419830Z qemu-system-x86_64: terminating on signal 15 from pid 1312 (<unknown process>)
2017-07-23 20:07:35.620+0000: shutting down, reason=destroyed

```
Also I am using the 4.10.0-28-generic kernel now.

Just to say: The general passtrough is working (if no amd driver is loaded on the guest os). But if I try to reinstall the driver on my guest vm, the vm is going blank and is not more responding. And after there is a driver the screen is going blank on every boot also if I passtrough my AMD RX 580. I could boot the vm successful with enabling the Spice graphics interface and removing the passtrough from my graphics card. I am really curious because its working really fine for months.. and now after the upgrade the vm is hanging. 

I cant find some related errors in my other logfiles (like /var/log/syslog) this seems to be clean. 

Maybe someone got also this issue? Any idea how to resolve this?

Regards
Th3R3al

---

### Post by th3r3al on 2017-07-26
Hey guys,

in the last days I get some new knowledge to the issues.

Something has changed at the pci device redirection. I installed several new virtual machines with q35 and i440fx chipset for testing purposes. Same issues here, the general graphics / device passtrough is OK, but if i am installing drivers the device is not correctly recognized by the driver. (Only the HDMI audio device from the graphics card). The graphics part is only recognized as a "Microsoft basic display device" which results in a low resolution and no performance.

My PCIe Graphics device is redirected with this PCI Device Path / Number: [COLOR=#444444][FONT=Helvetica]PCI\VEN_1002&DEV_67DF&SUBSYS_E3531DA2

Any idea?

Thanks![/FONT][/COLOR]

---

### Post by th3r3al on 2017-07-28
[COLOR=#222222][COLOR=#444444]Just wanna report back that it is working for me now. Upgraded to Ubuntu 17.10 and reinstalled my windows vm - the working for months vm - cant be revived. :( Its always crashing at driver initalization with a black screen. Unless I uninstall all the drivers before with the amd clean uninstall utility or not.[/COLOR]
[COLOR=#444444]Its mostly fixed for me now. Maybe someone got an awesome hint how to revive the old vm?[/COLOR]


[/COLOR]

---

### Post by masato-d on 2017-11-29
By using Devcon.exe it was possible to disable GPU at shutdown and enable GPU at startup.

---

