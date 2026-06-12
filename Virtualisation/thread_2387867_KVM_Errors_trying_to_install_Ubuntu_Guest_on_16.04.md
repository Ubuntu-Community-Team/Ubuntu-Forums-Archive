---
title: "KVM Errors trying to install Ubuntu Guest on 16.04 Server"
date: 2018-03-24
forum: Virtualisation
---

### Post by LVDave on 2018-03-24
I recently bought an offlease Dell R410 (2 x Xeon E5620s) and intend to use it as a VM host using KVM. System currently only has 8Gb of ram but have additional on order. The server is running Ubuntu 16.04 server, and has qemu-kvm, libvirt-bin, virtinstall, bridge-utils, cpu-checker and running "kvm-ok" shows INFO: /dev/kvm exists, KVM acceleration can be used. I also have an R210 I've set up the same way and it works fine with two Win2012 server and two Ubuntu server guests running on it. On the R410, when I run virt-manager and set up an Ubuntu install from an ISO, the install boots to the installer but I cannot get past the language screen. I have to select "force off" to kill the vm. A check of the /var/log/libvirt/qemu/U1404VM2.log shows the following:

```

2018-03-24 22:19:36.664+0000: starting up libvirt version: 1.3.1, package: 1ubuntu10.19 (Marc Deslauriers <marc.deslauriers@ubuntu.com> Fri, 16 Feb 2018 07:51:15 -0500), qemu version: 2.5.0 (Debian 1:2.5+dfsg-5ubuntu10.24), hostname: hands.frandin.org
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=spice /usr/bin/kvm-spice -name U1404VM2 -S -machine pc-i440fx-xenial,accel=kvm,usb=off -cpu Westmere,+rdtscp,+pdpe1gb,+dca,+pcid,+pdcm,+xtpr,+tm2,+est,+smx,+vmx,+ds_cpl,+monitor,+dtes64,+pclmuldq,+pbe,+tm,+ht,+ss,+acpi,+ds,+vme -m 512 -realtime mlock=off -smp 2,sockets=2,cores=1,threads=1 -uuid 35ff5fff-0f25-4f7d-ba66-63eb504095b6 -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-U1404VM2/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=utc,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot strict=on -device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x5.0x7 -device ich9-usb-uhci1,masterbus=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x5 -device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x5.0x1 -device ich9-usb-uhci3,masterbus=usb.0,firstport=4,bus=pci.0,addr=0x5.0x2 -device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x4 -drive file=/var/lib/libvirt/images/U1404VM2.qcow2,format=qcow2,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x6,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=2 -drive file=/home/dave/iso/ubuntu-14.04.3-server-amd64.iso,format=raw,if=none,id=drive-ide0-0-0,readonly=on -device ide-cd,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0,bootindex=1 -netdev tap,fd=26,id=hostnet0,vhost=on,vhostfd=29 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:93:53:75,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -chardev spicevmc,id=charchannel0,name=vdagent -device virtserialport,bus=virtio-serial0.0,nr=1,chardev=charchannel0,id=channel0,name=com.redhat.spice.0 -spice port=5900,addr=127.0.0.1,disable-ticketing,image-compression=off,seamless-migration=on -device qxl-vga,id=video0,ram_size=67108864,vram_size=67108864,vgamem_mb=16,bus=pci.0,addr=0x2 -chardev spicevmc,id=charredir0,name=usbredir -device usb-redir,chardev=charredir0,id=redir0 -chardev spicevmc,id=charredir1,name=usbredir -device usb-redir,chardev=charredir1,id=redir1 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x7 -msg timestamp=on
char device redirected to /dev/pts/2 (label charserial0)
warning: host doesn't support requested feature: CPUID.01H:EDX.ds [bit 21]
warning: host doesn't support requested feature: CPUID.01H:EDX.acpi [bit 22]
warning: host doesn't support requested feature: CPUID.01H:EDX.ht [bit 28]
warning: host doesn't support requested feature: CPUID.01H:EDX.tm [bit 29]
warning: host doesn't support requested feature: CPUID.01H:EDX.pbe [bit 31]
warning: host doesn't support requested feature: CPUID.01H:ECX.dtes64 [bit 2]
warning: host doesn't support requested feature: CPUID.01H:ECX.monitor [bit 3]
warning: host doesn't support requested feature: CPUID.01H:ECX.ds_cpl [bit 4]
warning: host doesn't support requested feature: CPUID.01H:ECX.smx [bit 6]
warning: host doesn't support requested feature: CPUID.01H:ECX.est [bit 7]
warning: host doesn't support requested feature: CPUID.01H:ECX.tm2 [bit 8]
warning: host doesn't support requested feature: CPUID.01H:ECX.xtpr [bit 14]
warning: host doesn't support requested feature: CPUID.01H:ECX.pdcm [bit 15]
warning: host doesn't support requested feature: CPUID.01H:ECX.dca [bit 18]
warning: host doesn't support requested feature: CPUID.01H:EDX.ds [bit 21]
warning: host doesn't support requested feature: CPUID.01H:EDX.acpi [bit 22]
warning: host doesn't support requested feature: CPUID.01H:EDX.ht [bit 28]
warning: host doesn't support requested feature: CPUID.01H:EDX.tm [bit 29]
warning: host doesn't support requested feature: CPUID.01H:EDX.pbe [bit 31]
warning: host doesn't support requested feature: CPUID.01H:ECX.dtes64 [bit 2]
warning: host doesn't support requested feature: CPUID.01H:ECX.monitor [bit 3]
warning: host doesn't support requested feature: CPUID.01H:ECX.ds_cpl [bit 4]
warning: host doesn't support requested feature: CPUID.01H:ECX.smx [bit 6]
warning: host doesn't support requested feature: CPUID.01H:ECX.est [bit 7]
warning: host doesn't support requested feature: CPUID.01H:ECX.tm2 [bit 8]
warning: host doesn't support requested feature: CPUID.01H:ECX.xtpr [bit 14]
warning: host doesn't support requested feature: CPUID.01H:ECX.pdcm [bit 15]
warning: host doesn't support requested feature: CPUID.01H:ECX.dca [bit 18]
main_channel_link: add main channel client
main_channel_handle_parsed: net test: latency 18.429000 ms, bitrate 1492711370 bps (1423.560495 Mbps)
red_dispatcher_set_cursor_peer: 
inputs_connect: inputs channel client create

```

The large number of warnings make me wonder if this might be the issue, but being a newbie to KVM virtualization, I haven't
a clue.... Help??

---

### Post by KillerKelvUK on 2018-03-25
So the warnings just mean you've setup the ubuntu guest with a virtual CPU that has features which your host CPU doesn't have and so cannot provide.  You can change the guests CPU configuration in virt-manager and just select another CPU type to try or you can type manually type in the box "host-passthrough" which does what it says, ensures the emulated CPU for the guest matches that of your host.

Not convinced this would cause a boot blocker on ubuntu install though...if you're getting stuck at a splash screen try editing the boot options on the fly to remove the splash screen so you can see the kernel and system output on screen as the guest boots, this might provide better insight to your problems.

---

### Post by LVDave on 2018-03-25
I'm kinda puzzled as the setting I have in virt-manager/cpu under "configuration" has a checkbox in "copy host cpu configuration". Have tried unchecking that and setting the "model" dropdown box to "hypervisor default", same hang, tried, even though this has 8 cpus (2 quad-core Xeons), setting number of cpus to 1 (had been 2).. Still hangs at the same spot and requires me to use "force off".. Thinking it might be a funky Ubuntu ISO (even though I always check the sha512sum after download), I tried booting a Fedora install ISO that I've used many times elsewhere... Same hang immeidately after boot. Baffled..

Thanks
Dave

---

