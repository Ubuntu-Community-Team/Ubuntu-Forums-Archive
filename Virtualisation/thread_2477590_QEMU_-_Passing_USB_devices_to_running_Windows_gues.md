---
title: "QEMU - Passing USB devices to running Windows guest programatically"
date: 2022-07-31
forum: Virtualisation
---

### Post by abtekk2 on 2022-07-31
[COLOR=#D7DADC][COLOR=#000000]My  new professional role is heavily Linux orientated, so it makes sense  for me to a full wipe of my home PC and primarily run Linux. I have a  spare GPU lying around, so what I'd like to do is run a Windows guest  for the odd times I want to play games, and to use USB/PCI passthrough  to hop between my Linux host and Windows guest. As my monitors have dual  input, this makes it easy without a KVM switch.

[/COLOR]
[COLOR=#000000]However,  my QEMU knowledge is limited. Is it possible via the command line to  attach and detach USB devices to/from a running QEMU guest? My plan is  to run a script on the Linux machine, switch inputs on my monitor to get  to Windows, and then SSH back in to the host to detach them.

[/COLOR]
[COLOR=#000000]Has anyone done it like this before?
[/COLOR]
[/COLOR]

---

### Post by #&amp;thj^% on 2022-07-31
> **abtekk2 said:**
> [COLOR=#D7DADC][COLOR=#000000]

[/COLOR]
[COLOR=#000000]Has anyone done it like this before?
[/COLOR]
[/COLOR]
I hate this phrase "kind of" >>but minus the Windows OS, I have at times run 7 Linux QEMU's sessions, switching between them.
It's been a while but something along the likes of this: [https://documentation.suse.com/sles/12-SP4/html/SLES-all/cha-qemu-running.html](https://documentation.suse.com/sles/12-SP4/html/SLES-all/cha-qemu-running.html)
Good Luck
EDIT: I forgot to add how to view my/your opened sessions:
```
ps -ef | awk -e '/qemu/ && !/awk/' | sed -e 's/[^/]*//' -e 's/ -/\n\t-/g'
```
Example Output with Fedora Silverblue & Ubuntu 22.04:
```
/usr/bin/qemu-system-x86_64
        -name guest=fedora-coreos-testing,debug-threads=on
        -S
        -object {"qom-type":"secret","id":"masterKey0","format":"raw","file":"/var/lib/libvirt/qemu/domain-1-fedora-coreos-testin/master-key.aes"}
        -blockdev {"driver":"file","filename":"/usr/share/edk2-ovmf/x64/OVMF_CODE.fd","node-name":"libvirt-pflash0-storage","auto-read-only":true,"discard":"unmap"}
        -blockdev {"node-name":"libvirt-pflash0-format","read-only":true,"driver":"raw","file":"libvirt-pflash0-storage"}
        -blockdev {"driver":"file","filename":"/var/lib/libvirt/qemu/nvram/fedora-coreos-testing_VARS.fd","node-name":"libvirt-pflash1-storage","auto-read-only":true,"discard":"unmap"}
        -blockdev {"node-name":"libvirt-pflash1-format","read-only":false,"driver":"raw","file":"libvirt-pflash1-storage"}
        -machine pc-i440fx-7.0,usb=off,dump-guest-core=off,pflash0=libvirt-pflash0-format,pflash1=libvirt-pflash1-format,memory-backend=pc.ram
        -accel kvm
        -cpu host,migratable=on
        -m 4048
        -object {"qom-type":"memory-backend-ram","id":"pc.ram","size":4244635648}
        -overcommit mem-lock=off
        -smp 4,sockets=4,cores=1,threads=1
        -uuid c9e377ce-b613-416d-b3b4-2d8a9248b64e
        -no-user-config
        -nodefaults
        -chardev socket,id=charmonitor,fd=34,server=on,wait=off
        -mon chardev=charmonitor,id=monitor,mode=control
        -rtc base=utc,driftfix=slew
        -global kvm-pit.lost_tick_policy=delay
        -no-hpet
        -no-shutdown
        -boot strict=on
        -device {"driver":"ich9-usb-ehci1","id":"usb","bus":"pci.0","addr":"0x5.0x7"}
        -device {"driver":"ich9-usb-uhci1","masterbus":"usb.0","firstport":0,"bus":"pci.0","multifunction":true,"addr":"0x5"}
        -device {"driver":"ich9-usb-uhci2","masterbus":"usb.0","firstport":2,"bus":"pci.0","addr":"0x5.0x1"}
        -device {"driver":"ich9-usb-uhci3","masterbus":"usb.0","firstport":4,"bus":"pci.0","addr":"0x5.0x2"}
        -device {"driver":"virtio-serial-pci","id":"virtio-serial0","bus":"pci.0","addr":"0x6"}
        -blockdev {"driver":"file","filename":"/var/lib/libvirt/images/fedora-coreos-testing.img","node-name":"libvirt-2-storage","auto-read-only":true,"discard":"unmap"}
        -blockdev {"node-name":"libvirt-2-format","read-only":false,"discard":"unmap","driver":"raw","file":"libvirt-2-storage"}
        -device {"driver":"virtio-blk-pci","bus":"pci.0","addr":"0x7","drive":"libvirt-2-format","id":"virtio-disk0","bootindex":1}
        -device {"driver":"ide-cd","bus":"ide.0","unit":0,"id":"ide0-0-0"}
        -netdev tap,fd=35,vhost=on,vhostfd=37,id=hostnet0
        -device {"driver":"virtio-net-pci","netdev":"hostnet0","id":"net0","mac":"52:54:00:c2:3c:c1","bus":"pci.0","addr":"0x3"}
        -chardev pty,id=charserial0
        -device {"driver":"isa-serial","chardev":"charserial0","id":"serial0","index":0}
        -chardev socket,id=charchannel0,fd=33,server=on,wait=off
        -device {"driver":"virtserialport","bus":"virtio-serial0.0","nr":1,"chardev":"charchannel0","id":"channel0","name":"org.qemu.guest_agent.0"}
        -chardev spicevmc,id=charchannel1,name=vdagent
        -device {"driver":"virtserialport","bus":"virtio-serial0.0","nr":2,"chardev":"charchannel1","id":"channel1","name":"com.redhat.spice.0"}
        -device {"driver":"usb-tablet","id":"input0","bus":"usb.0","port":"1"}
        -audiodev {"id":"audio1","driver":"spice"}
        -spice port=5900,addr=127.0.0.1,disable-ticketing=on,image-compression=off,seamless-migration=on
        -device {"driver":"virtio-vga","id":"video0","max_outputs":1,"bus":"pci.0","addr":"0x2"}
        -device {"driver":"intel-hda","id":"sound0","bus":"pci.0","addr":"0x4"}
        -device {"driver":"hda-duplex","id":"sound0-codec0","bus":"sound0.0","cad":0,"audiodev":"audio1"}
        -chardev spicevmc,id=charredir0,name=usbredir
        -device {"driver":"usb-redir","chardev":"charredir0","id":"redir0","bus":"usb.0","port":"2"}
        -chardev spicevmc,id=charredir1,name=usbredir
        -device {"driver":"usb-redir","chardev":"charredir1","id":"redir1","bus":"usb.0","port":"3"}
        -device {"driver":"virtio-balloon-pci","id":"balloon0","bus":"pci.0","addr":"0x8"}
        -object {"qom-type":"rng-random","id":"objrng0","filename":"/dev/urandom"}
        -device {"driver":"virtio-rng-pci","rng":"objrng0","id":"rng0","bus":"pci.0","addr":"0x9"}
        -sandbox on,obsolete=deny,elevateprivileges=deny,spawn=deny,resourcecontrol=deny
        -msg timestamp=on
/usr/bin/qemu-system-x86_64
        -name guest=ubuntu22.04,debug-threads=on
        -S
        -object {"qom-type":"secret","id":"masterKey0","format":"raw","file":"/var/lib/libvirt/qemu/domain-2-ubuntu22.04/master-key.aes"}
        -blockdev {"driver":"file","filename":"/usr/share/edk2-ovmf/x64/OVMF_CODE.secboot.fd","node-name":"libvirt-pflash0-storage","auto-read-only":true,"discard":"unmap"}
        -blockdev {"node-name":"libvirt-pflash0-format","read-only":true,"driver":"raw","file":"libvirt-pflash0-storage"}
        -blockdev {"driver":"file","filename":"/var/lib/libvirt/qemu/nvram/ubuntu22.04_VARS.fd","node-name":"libvirt-pflash1-storage","auto-read-only":true,"discard":"unmap"}
        -blockdev {"node-name":"libvirt-pflash1-format","read-only":false,"driver":"raw","file":"libvirt-pflash1-storage"}
        -machine pc-q35-7.0,usb=off,vmport=off,smm=on,dump-guest-core=off,pflash0=libvirt-pflash0-format,pflash1=libvirt-pflash1-format,memory-backend=pc.ram
        -accel kvm
        -cpu host,migratable=on
        -m 4096
        -object {"qom-type":"memory-backend-ram","id":"pc.ram","size":4294967296}
        -overcommit mem-lock=off
        -smp 4,sockets=4,cores=1,threads=1
        -uuid d85fa81c-9ec5-42fc-b91a-f1895f6ab5ad
        -no-user-config
        -nodefaults
        -chardev socket,id=charmonitor,fd=38,server=on,wait=off
        -mon chardev=charmonitor,id=monitor,mode=control
        -rtc base=utc,driftfix=slew
        -global kvm-pit.lost_tick_policy=delay
        -no-hpet
        -no-shutdown
        -global ICH9-LPC.disable_s3=1
        -global ICH9-LPC.disable_s4=1
        -boot strict=on
        -device {"driver":"pcie-root-port","port":16,"chassis":1,"id":"pci.1","bus":"pcie.0","multifunction":true,"addr":"0x2"}
        -device {"driver":"pcie-root-port","port":17,"chassis":2,"id":"pci.2","bus":"pcie.0","addr":"0x2.0x1"}
        -device {"driver":"pcie-root-port","port":18,"chassis":3,"id":"pci.3","bus":"pcie.0","addr":"0x2.0x2"}
        -device {"driver":"pcie-root-port","port":19,"chassis":4,"id":"pci.4","bus":"pcie.0","addr":"0x2.0x3"}
        -device {"driver":"pcie-root-port","port":20,"chassis":5,"id":"pci.5","bus":"pcie.0","addr":"0x2.0x4"}
        -device {"driver":"pcie-root-port","port":21,"chassis":6,"id":"pci.6","bus":"pcie.0","addr":"0x2.0x5"}
        -device {"driver":"pcie-root-port","port":22,"chassis":7,"id":"pci.7","bus":"pcie.0","addr":"0x2.0x6"}
        -device {"driver":"pcie-root-port","port":23,"chassis":8,"id":"pci.8","bus":"pcie.0","addr":"0x2.0x7"}
        -device {"driver":"pcie-root-port","port":24,"chassis":9,"id":"pci.9","bus":"pcie.0","multifunction":true,"addr":"0x3"}
        -device {"driver":"pcie-root-port","port":25,"chassis":10,"id":"pci.10","bus":"pcie.0","addr":"0x3.0x1"}
        -device {"driver":"pcie-root-port","port":26,"chassis":11,"id":"pci.11","bus":"pcie.0","addr":"0x3.0x2"}
        -device {"driver":"pcie-root-port","port":27,"chassis":12,"id":"pci.12","bus":"pcie.0","addr":"0x3.0x3"}
        -device {"driver":"pcie-root-port","port":28,"chassis":13,"id":"pci.13","bus":"pcie.0","addr":"0x3.0x4"}
        -device {"driver":"pcie-root-port","port":29,"chassis":14,"id":"pci.14","bus":"pcie.0","addr":"0x3.0x5"}
        -device {"driver":"qemu-xhci","p2":15,"p3":15,"id":"usb","bus":"pci.2","addr":"0x0"}
        -device {"driver":"virtio-serial-pci","id":"virtio-serial0","bus":"pci.3","addr":"0x0"}
        -blockdev {"driver":"file","filename":"/var/lib/libvirt/images/ubuntu22.04.qcow2","node-name":"libvirt-2-storage","auto-read-only":true,"discard":"unmap"}
        -blockdev {"node-name":"libvirt-2-format","read-only":false,"discard":"unmap","driver":"qcow2","file":"libvirt-2-storage","backing":null}
        -device {"driver":"virtio-blk-pci","bus":"pci.4","addr":"0x0","drive":"libvirt-2-format","id":"virtio-disk0","bootindex":1}
        -device {"driver":"ide-cd","bus":"ide.0","id":"sata0-0-0"}
        -netdev tap,fd=39,vhost=on,vhostfd=41,id=hostnet0
        -device {"driver":"virtio-net-pci","netdev":"hostnet0","id":"net0","mac":"52:54:00:46:67:f8","bus":"pci.1","addr":"0x0"}
        -chardev pty,id=charserial0
        -device {"driver":"isa-serial","chardev":"charserial0","id":"serial0","index":0}
        -chardev socket,id=charchannel0,fd=36,server=on,wait=off
        -device {"driver":"virtserialport","bus":"virtio-serial0.0","nr":1,"chardev":"charchannel0","id":"channel0","name":"org.qemu.guest_agent.0"}
        -chardev spicevmc,id=charchannel1,name=vdagent
        -device {"driver":"virtserialport","bus":"virtio-serial0.0","nr":2,"chardev":"charchannel1","id":"channel1","name":"com.redhat.spice.0"}
        -device {"driver":"usb-tablet","id":"input0","bus":"usb.0","port":"1"}
        -audiodev {"id":"audio1","driver":"spice"}
        -spice port=5901,addr=127.0.0.1,disable-ticketing=on,image-compression=off,seamless-migration=on
        -device {"driver":"qxl-vga","id":"video0","max_outputs":1,"ram_size":67108864,"vram_size":67108864,"vram64_size_mb":0,"vgamem_mb":16,"bus":"pcie.0","addr":"0x1"}
        -device {"driver":"ich9-intel-hda","id":"sound0","bus":"pcie.0","addr":"0x1b"}
        -device {"driver":"hda-duplex","id":"sound0-codec0","bus":"sound0.0","cad":0,"audiodev":"audio1"}
        -chardev spicevmc,id=charredir0,name=usbredir
        -device {"driver":"usb-redir","chardev":"charredir0","id":"redir0","bus":"usb.0","port":"2"}
        -chardev spicevmc,id=charredir1,name=usbredir
        -device {"driver":"usb-redir","chardev":"charredir1","id":"redir1","bus":"usb.0","port":"3"}
        -device {"driver":"virtio-balloon-pci","id":"balloon0","bus":"pci.5","addr":"0x0"}
        -object {"qom-type":"rng-random","id":"objrng0","filename":"/dev/urandom"}
        -device {"driver":"virtio-rng-pci","rng":"objrng0","id":"rng0","bus":"pci.6","addr":"0x0"}
        -sandbox on,obsolete=deny,elevateprivileges=deny,spawn=deny,resourcecontrol=deny
        -msg timestamp=on


```
Have Fun

---

