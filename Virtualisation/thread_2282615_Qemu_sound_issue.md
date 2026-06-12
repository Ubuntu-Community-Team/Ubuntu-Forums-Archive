---
title: "Qemu sound issue?"
date: 2015-06-15
forum: Virtualisation
---

### Post by eezacque on 2015-06-15
Sounds like qemu (using pulse audio) chops off a second or so from each sound played, which makes alerts pretty much useless.
Any clue on how to debug thus?

---

### Post by KillerKelvUK on 2015-06-16
Lots of post about passing qemu parameters forcing audio backends and sample rates however most come with a health warning that they only make the problem less worse so aren't a full fix.  I personally have no issue with sound using SPICE on a local network but depending on your use case this may not be viable?

---

### Post by eezacque on 2015-06-16
> **KillerKelvUK said:**
> Lots of post about passing qemu parameters forcing audio backends and sample rates however most come with a health warning that they only make the problem less worse so aren't a full fix.  I personally have no issue with sound using SPICE on a local network but depending on your use case this may not be viable?

Care to elaborate on using SPICE?

---

### Post by KillerKelvUK on 2015-06-16
Sure, SPICE is an alternative to VNC/RDP for accessing the vm guest consoles/desktops... [http://www.spice-space.org/home.html](http://www.spice-space.org/home.html)

I have a win7 vm for all my corp stuff and use spice as the graphical and audio performance (local) are pretty top notch, I pass through a USB webcam and headset and use Skype and WebEx on a daily basis for calls and UC...no issues with audio.

If you're using virt-manager to admin the vm's you can easily edit the 'Display' properties for the guest and select spice as the server and protocol, I'd recommend setting the video adapter to QXL as this I believe is the native spice adapter expected.  The guest drivers for all things spice and virtio can be found here...[https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download) I'd recommend using the latest (i.e. not the stable) release as this encorporates some additional driver updates that Win7 & Win8 guest benefit from.  Spice works for linux vm's also.

Ubuntu ships an old version of the virt-viewer package which is what provides the remote access client (remote-viewer)...you need this to access the vm's desktop.

EDIT:
sorry the above was assuming you're using qemu with kvm and thus the virt-manager assumption was a bigger leap...if you're just running qemu from the command line then the below is an example based on my setup...


> qemu-system-x86_64 -enable-kvm -name blackwindows7 -S -machine pc-i440fx-utopic,accel=kvm,usb=off -cpu Haswell,+invtsc,+abm,+pdpe1gb,+rdrand,+f16c,+osxsave,+pdcm,+xtpr,+tm2,+est,+smx,+vmx,+ds_cpl,+monitor,+dtes64,+pbe,+tm,+ht,+ss,+acpi,+ds,+vme -m 4096 -realtime mlock=off -smp 4,sockets=1,cores=2,threads=2 -uuid a5f8e785-3013-43f5-8ae9-204589cc1311 -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/blackwindows7.monitor,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot strict=on -device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x9.0x7 -device ich9-usb-uhci1,masterbus=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x9 -device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x9.0x1 -device ich9-usb-uhci3,masterbus=usb.0,firstport=4,bus=pci.0,addr=0x9.0x2 -device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x5 -drive file=/mnt/vms/blackwindows7.qcow2,if=none,id=drive-virtio-disk0,format=qcow2 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -drive file=/mnt/share/Filestorage/Software/Drivers/virtio-win-0.1.103.iso,if=none,id=drive-ide0-0-0,readonly=on,format=raw -device ide-cd,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0 -netdev tap,fd=26,id=hostnet0,vhost=on,vhostfd=27 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:64:1a:7d,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -chardev socket,id=charchannel0,path=/var/lib/libvirt/qemu/channel/target/blackwindows7.org.qemu.guest_agent.0,server,nowait -device virtserialport,bus=virtio-serial0.0,nr=1,chardev=charchannel0,id=channel0,name=org.qemu.guest_agent.0 -device usb-tablet,id=input0 _**-spice port=5902,addr=127.0.0.1,disable-ticketing,seamless-migration=on -device qxl-vga,id=video0,ram_size=67108864,vram_size=67108864,vgamem_mb=16,bus=pci.0,addr=0x2**_ -device intel-hda,id=sound0,bus=pci.0,addr=0x4 -device hda-duplex,id=sound0-codec0,bus=sound0.0,cad=0 -chardev spicevmc,id=charredir0,name=usbredir -device usb-redir,chardev=charredir0,id=redir0 -chardev spicevmc,id=charredir1,name=usbredir -device usb-redir,chardev=charredir1,id=redir1 -chardev spicevmc,id=charredir2,name=usbredir -device usb-redir,chardev=charredir2,id=redir2 -chardev spicevmc,id=charredir3,name=usbredir -device usb-redir,chardev=charredir3,id=redir3 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8 -msg timestamp=on

---

### Post by eezacque on 2015-06-16
> **KillerKelvUK said:**
> Sure, SPICE is an alternative to VNC/RDP for accessing the vm guest consoles/desktops... [http://www.spice-space.org/home.html](http://www.spice-space.org/home.html)

I have a win7 vm for all my corp stuff and use spice as the graphical and audio performance (local) are pretty top notch, I pass through a USB webcam and headset and use Skype and WebEx on a daily basis for calls and UC...no issues with audio.

If you're using virt-manager to admin the vm's you can easily edit the 'Display' properties for the guest and select spice as the server and protocol, I'd recommend setting the video adapter to QXL as this I believe is the native spice adapter expected.  The guest drivers for all things spice and virtio can be found here...[https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download](https://fedoraproject.org/wiki/Windows_Virtio_Drivers#Direct_download) I'd recommend using the latest (i.e. not the stable) release as this encorporates some additional driver updates that Win7 & Win8 guest benefit from.  Spice works for linux vm's also.

Ubuntu ships an old version of the virt-viewer package which is what provides the remote access client (remote-viewer)...you need this to access the vm's desktop.

EDIT:
sorry the above was assuming you're using qemu with kvm and thus the virt-manager assumption was a bigger leap...if you're just running qemu from the command line then the below is an example based on my setup...

I am using an OS X guest, which does pretty much all I need, including running my Cintiq tablet with Photoshop, so I am a little reluctant overhauling my setup just to fix a sound issue. I appreciate your suggestion, will keep it in mind, but  for now will try to debug the sound issue...

---

### Post by KillerKelvUK on 2015-06-17
> **eezacque said:**
> I am using an OS X guest, which does pretty much all I need, including running my Cintiq tablet with Photoshop, so I am a little reluctant overhauling my setup just to fix a sound issue. I appreciate your suggestion, will keep it in mind, but  for now will try to debug the sound issue...

I've previously setup an unhacked OS X guest and used spice was the remote access protocol, from recollection that struggled although I remember something around grabbing the latest Voodoo HDA drivers which made a positive impact.  If you're in hackintosh territory I've no experience with that.

---

