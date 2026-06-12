---
title: "VGA Passthrough with KVM - Guest/Host crash during AMD driver install into Guest"
date: 2015-10-22
forum: Virtualisation
---

### Post by ryan-flagler on 2015-10-22
tldr; VGA passthrough seems fully functional and stable with either Win7 or Win8.1 UNTIL I attempt to install the AMD video drivers into the Guest OS. Almost immediately the VM will hang and at the same time my Host OS hangs as well. I have to reboot to recover from it.

Software Configuration
Ubuntu 14.04.3
Default unmodified kernel 3.19.0-31-generic
qemu 2.1.2 from the default repo

Hardware Configuration
HP Proliant ML10 socket 1155 Motherboard (732594-001) with onboard Matrox G200EH GPU/IPMI
Intel Xeon E3-1245v2 CPU
24GB Kingston DDR3 ECC Memory
3x LSI 9240-8i Raid Controllers
XFX Radeon 7850 1GB GPU (FX-785A-ZNBR) (No EUFI GOP support)

KVM Configuration
iommu groups```

### Group 0 ###
    00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/Ivy Bridge DRAM Controller (rev 09)
### Group 1 ###
    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
    04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn PRO [Radeon HD 7850]
    04:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
### Group 2 ###
    00:06.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
    07:00.0 Serial Attached SCSI controller: LSI Logic / Symbios Logic SAS2008 PCI-Express Fusion-MPT SAS-2 [Falcon] (rev 02)
### Group 3 ###
    00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
### Group 4 ###
    00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
### Group 5 ###
    00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
### Group 6 ###
    00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
### Group 7 ###
    00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
### Group 8 ###
    00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
### Group 9 ###
    00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
### Group 10 ###
    00:1f.0 ISA bridge: Intel Corporation C204 Chipset Family LPC Controller (rev 05)
    00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
### Group 11 ###
    0a:00.0 Serial Attached SCSI controller: LSI Logic / Symbios Logic SAS2008 PCI-Express Fusion-MPT SAS-2 [Falcon] (rev 03)
### Group 12 ###
    02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
### Group 13 ###
    0d:00.0 Serial Attached SCSI controller: LSI Logic / Symbios Logic SAS2008 PCI-Express Fusion-MPT SAS-2 [Falcon] (rev 03)
### Group 14 ###
    01:00.0 System peripheral: Hewlett-Packard Company Integrated Lights-Out Standard Slave Instrumentation & System Support (rev 05)
    01:00.1 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200EH
    01:00.2 System peripheral: Hewlett-Packard Company Integrated Lights-Out Standard Management Processor Support and Messaging (rev 05)
    01:00.4 USB controller: Hewlett-Packard Company Integrated Lights-Out Standard Virtual USB Controller (rev 02)

```/etc/modules #Has the following appended
```

pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm 
kvm_intel 
```

/etc/default/grub #Has the following appended
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"
```

lspci -nn | grep AMD
```
04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn PRO [Radeon HD 7850] [1002:6819]
04:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
```

/etc/initramfs-tools/modules #Contains the following
```
pci_stub ids=1002:6819,1002:aab0
```

dmesg | greppci-stub #Displays the following
```
[    0.569662] pci-stub: add 1002:6819 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    0.569674] pci-stub 0000:04:00.0: claimed by stub
[    0.569682] pci-stub: add 1002:AAB0 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    0.569690] pci-stub 0000:04:00.1: claimed by stub

```

VM startup script and config
```

#!/bin/bash
 
logFile=$(basename $0).log
 
#Define each of our pci-stub devices
pcistub[0]=0000:04:00.0
pcistub[1]=0000:04:00.1
 
vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
 
}
 
modprobe vfio-pci
 
i=0
while [[ $i -lt ${#pcistub
[*]} ]]
do
vfiobind ${pcistub[$i]}
((i+=1))
done
 
nohup qemu-system-x86_64 -enable-kvm -M q35 -m 8094 -cpu host \
-smp 4,sockets=1,cores=2,threads=2 \
-bios /usr/share/qemu/bios.bin \
-device virtio-scsi-pci,id=scsi \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on,romfile=/usr/local/bin/XFX.HD7850.1024.120508.rom -nographic \
-device vfio-pci,host=04:00.1,bus=root.1,addr=00.1 \
-usb -usbdevice host:045e:00db -usbdevice host:045e:0039 \
-drive file=/dev/sdk,id=disk,format=raw,if=none -device scsi-hd,drive=disk \
-drive file=/mpool00/Uploads/Windows8.1ProNx64.iso,id=isocd -device ide-cd,bus=ide.0,drive=isocd \
-drive file=/mpool00/Uploads/virtio-win-0.1.102.iso,id=virtiocd,if=none -device ide-cd,bus=ide.1,drive=virtiocd \
-net bridge,br=br0 -net nic,macaddr=52:54:00:81:08:ab,model=virtio \
-boot menu=on \
-vga none >> $logFile 2>&1 &
 
exit 0

```

Issue Description
My VM properly launches, passes through my VGA card, USB keyboard and Mouse, Audio from the VGA card, network adapter is configured, mounts all ISO's and my disk. I can install the virtio nic and scsi drivers during windows install and fully install windows. I can load windows and access the internet and my local network. When I download the latest AMD drivers, I can begin the install but the following happens.

WIndows 8.1
As soon as the driver is installed and the machine tries to apply it, both the Guest and Host OS lock up. I must reboot them to recover. After this, the VM will randomly lock up on me even though the driver isn't applied to the GPU.

Windows 7
After the driver install it asks me to reboot. Upon reboot, once the graphics driver is initialized both the Guest and Host OS lockup. I must reboot them to recover; however the OS will never fully load for me after this point. (Safe mode may work, but I have not tried it)

It is my understanding that since the GPU is successfully passing through, I don't need the ACS or i915 patches. I think I don't need the i915 patch because i'm not using Intel integraded graphics for the host but and onboard Matrox GPU, which is kind of like a discrete adapter. I don't think I need ACS because my GPU passes through initially without a problem. My only concern is the PCI Root Bus that is shown in the same IOMMU Group.

Does anyone have any ideas? Is there a way to see a kernel dump or errors for this? I'm not sure where to even start honestly.




I crossed a few items of my list of things to try tonight.

I modified my VM for only 1024mb of memory.
I made sure my memory wasn't running faster than 1333mhz.
I compiled my kernel with the ACS and i915 patches.

None of these things had any effect on the stability of the Guest VM. I'll keep poking around, but if anyone has any ideas, I'm open ears.


** 2015-10-24 ** Update
I pulled the HDD of my system and threw a fresh one in and reinstalled 14.04.03 Server from scratch. I built qemu-kvm from 2.4 source. This time, although my system hung, I got a kernel message on the screen!

```
[ 541.688505]NMI: PCI system error (SERR) for reason b1 on CPU 0[ 541.703459]Dazed and confused, but trying to continue

```

Unfortunately, after some quick searching, this may be an issue with my HP motherboard and their BIOS. I tried setting the following kernel param.

pcie_aspm=off

This would prevent my host OS from crashing, but the VM would hang at this point. (Or, I think the VM is hanging, I'm not getting any video, but maybe it's continuing without my video card)

So, unless anyone has some ideas, I'm out of them. :(

---

### Post by asymptonic on 2015-11-26
I'm having this exact problem on 15.10, on an ASRock Z170 Extreme 4+ with Skylake 6700K.  Did you get anywhere with this?  Here are my relevant details:


```
 GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on pci-stub.ids=1002:7300,1002:aae8"
```

Libvirt XML:

```
<domain type='kvm'>
  <name>Windows</name>
  <uuid>20a11b91-11e4-4cb1-ba90-4dafae864c41</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-vivid'>hvm</type>
    <loader type='rom'>/usr/share/qemu/OVMF-win10.fd</loader>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Broadwell</model>
    <topology sockets='1' cores='4' threads='1'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/home/scott/Windows.img'/>
      <target dev='vdb' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/home/scott/Downloads/virtio-win-0.1.110.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <boot order='2'/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:c1:d3:f1'/>
      <source network='default'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0c' function='0x0'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

---

### Post by KillerKelvUK on 2015-11-29
@ryan-flagler - what's the reason your attempting this with q35? (most) of the pass-thru's I've seen successful are i440fx's but I guess that doesn't preclude the q35 case.  Maybe re-tool any try i440fx...you could also consider OVMF as a 2nd step.  Based on your output ACS patching isn't necessary and i915 is intel based which you aren't.

@asymptonic - not sure you're problem is the same, little to go on from your post but from your guest config you have both the virtual qxl video card configured as well as your pass-thru card...this will cause issues.  Remember when using libvirt & virt-manager you need to pass qemu-args for the spice connection else libvirt/virt-manager auto adds the display adapter as well i.e. the qxl!

---

### Post by asymptonic on 2015-11-29
> **KillerKelvUK said:**
> 
@asymptonic - not sure you're problem is the same, little to go on from your post but from your guest config you have both the virtual qxl video card configured as well as your pass-thru card...this will cause issues.  Remember when using libvirt & virt-manager you need to pass qemu-args for the spice connection else libvirt/virt-manager auto adds the display adapter as well i.e. the qxl!

Thanks.  Tried that, and that did get me graphics on the dedicated card, but still hard hangs the host and guest as soon as I try installing the graphics driver.  Here's the resulting QEMU command line from my libvirt config.  What else whould help diagnose this problem?

```

/usr/bin/qemu-system-x86_64 -name Windows -S -machine pc-i440fx-vivid,accel=kvm,usb=off,mem-merge=off -cpu Broadwell,hv_time,kvm=off -bios /usr/share/qemu/OVMF-win10.fd -m 1024 -mem-prealloc -mem-path /dev/hugepages/libvirt/qemu -realtime mlock=off -smp 4,sockets=1,cores=4,threads=1 -uuid 20a11b91-11e4-4cb1-ba90-4dafae864c41 -nographic -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/Windows.monitor,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot menu=off,strict=on -device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x6.0x7 -device ich9-usb-uhci1,masterbus=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x6 -device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x6.0x1 -device ich9-usb-uhci3,masterbus=usb.0,firstport=4,bus=pci.0,addr=0x6.0x2 -device ahci,id=sata0,bus=pci.0,addr=0x8 -device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x5 -drive file=/home/scott/VMs/Windows.img,if=none,id=drive-virtio-disk1,format=qcow2 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0xa,drive=drive-virtio-disk1,id=virtio-disk1,bootindex=1 -drive file=/home/scott/Downloads/virtio-win-0.1.110.iso,if=none,id=drive-ide0-1-0,readonly=on,format=raw -device ide-cd,bus=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 -netdev tap,fd=24,id=hostnet0,vhost=on,vhostfd=25 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:c1:d3:f1,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -chardev spicevmc,id=charchannel0,name=vdagent -device virtserialport,bus=virtio-serial0.0,nr=1,chardev=charchannel0,id=channel0,name=com.redhat.spice.0 -device usb-tablet,id=input0 -device intel-hda,id=sound0,bus=pci.0,addr=0x4 -device hda-duplex,id=sound0-codec0,bus=sound0.0,cad=0 -chardev spicevmc,id=charredir0,name=usbredir -device usb-redir,chardev=charredir0,id=redir0 -chardev spicevmc,id=charredir1,name=usbredir -device usb-redir,chardev=charredir1,id=redir1 -chardev spicevmc,id=charredir2,name=usbredir -device usb-redir,chardev=charredir2,id=redir2 -chardev spicevmc,id=charredir3,name=usbredir -device usb-redir,chardev=charredir3,id=redir3 -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0xb -device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0xc -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x7 -spice port=5905,disable-ticketing -msg timestamp=on

```

---

### Post by KillerKelvUK on 2015-11-30
> **asymptonic said:**
> Thanks.  Tried that, and that did get me graphics on the dedicated card, but still hard hangs the host and guest as soon as I try installing the graphics driver.  Here's the resulting QEMU command line from my libvirt config.  What else whould help diagnose this problem?

Any error or debug msg output to syslog or by libvirt in /var/log/libvirt/qemu/name-of-guest.log?

From your qemu line I have a couple of questions...

[LIST=1]
[*]Why only give the guest 1 GB of RAM?
[*]If this is an AMD passthrough why are you turning KVM off?
[*]Which version of OVMF are you using, stock or Gerd's lastest build?
[*]Have you tried paring this back to the bare minimums to get functional first and then improve performance i.e. strip out mem-preall, huge pages, spice channel redirection?
[/LIST]

---

### Post by asymptonic on 2015-12-05
> **KillerKelvUK said:**
> Any error or debug msg output to syslog or by libvirt in /var/log/libvirt/qemu/name-of-guest.log?

From your qemu line I have a couple of questions...

[LIST=1]
[*]Why only give the guest 1 GB of RAM? 
[*]If this is an AMD passthrough why are you turning KVM off? 
[*]Which version of OVMF are you using, stock or Gerd's lastest build? 
[*]Have you tried paring this back to the bare minimums to get functional first and then improve performance i.e. strip out mem-preall, huge pages, spice channel redirection? 
[/LIST]


No errors are present because the system hangs so hard it has no time to log or flush logs to disk.

1.  I'd read in some threads that too much RAM could cause problems.  Had no effect on me, 8G or 1G are the same.
2. Another thing I'd tried.  KVM on or off makes no difference
3. Gerd's latest.
4. Yes, I've tried all of that.  The guest runs perfectly fine right up until it tries to initialize the passthrough VGA card in anything other than VESA mode it seems.  This happens during installation of the video drivers.

---

### Post by KillerKelvUK on 2015-12-05
> **asymptonic said:**
> No errors are present because the system hangs so hard it has no time to log or flush logs to disk.

1.  I'd read in some threads that too much RAM could cause problems.  Had no effect on me, 8G or 1G are the same.
2. Another thing I'd tried.  KVM on or off makes no difference
3. Gerd's latest.
4. Yes, I've tried all of that.  The guest runs perfectly fine right up until it tries to initialize the passthrough VGA card in anything other than VESA mode it seems.  This happens during installation of the video drivers.

Whats your hardware and host software?

Any errors in any logs, syslog; libvirt?

have you cleaned the graphics drivers from the guest...thinking if you've had lots of problems maybe there is something underlying the guest rather than the host confit?

---

### Post by T.J. on 2015-12-05
> **KillerKelvUK said:**
> @ryan-flagler - what's the reason your attempting this with q35? (most) of the pass-thru's I've seen successful are i440fx's but I guess that doesn't preclude the q35 case.  Maybe re-tool any try i440fx...you could also consider OVMF as a 2nd step.  Based on your output ACS patching isn't necessary and i915 is intel based which you aren't.!

I have a working Q35 setup, although I do not use libvirt/virt-manager.  ACS patching should not be necessary as long as you pass the entire IOMMU group.  

In order to get it to work, I've had to reserve my card to either pci-stub or vfio-pci on boot.  This includes blocking the loading of the snd_intel driver for the card's HDMI port, by blacklisting the device in the sound driver.  Then I have to bind both the video and the HDMI sound to vfio-pci during the script phase. If you do not do this, passthrough WILL crash. 

I've heard - not tested - that if you are attempting an AMD pass-through, you should not install the Catalyst suite, but the driver only - anything else has been known to crash Windows as in BSOD..

---

### Post by T.J. on 2015-12-05
Perhaps this will help someone.  I do not use Libvirt or Virt-manager as they cause the video driver to crash or strange DirectX behaviour.


sudo /usr/bin/qemu-system-x86_64 -enable-kvm -m 8192 -cpu host,kvm=off \
-smp 3,sockets=1,cores=3,threads=1 \
-machine q35,accel=kvm \
-device qxl \
-usb \
-device usb-mouse \
-device usb-kbd \
-soundhw hda \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=***[your card]***,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=***[HDMI port on card]***,bus=root.1,addr=00.1 \
-device virtio-blk-pci,scsi=off,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=0 \
-drive file=***[file name]***,if=none,id=drive-virtio-disk0,format=qcow2,media=disk \
-netdev tap,id=user.0 \
-device virtio-net-pci,netdev=user.0,mac=***[B][your chosen MAC address]**[/B]* \
-boot order=c \
-rtc base=localtime,driftfix=slew


It is important that if you are going to launch this from X11 that you alter your X11 host restrictions first or it will not connect to the display, since you have to give it direct access to the hardware via sudo. (I suppose you could alter the VFIO permissions, but I would rather not risk issues.)

---

### Post by asymptonic on 2015-12-08
> **KillerKelvUK said:**
> Whats your hardware and host software?

ASRock Z170 Extreme4+ motherboard (with IOMMU enabled).  Intel Core i7-6700k (Skylake).  Ubuntu 15.10 with whatever the latest libvirt is on that. 

> **KillerKelvUK said:**
> 
Any errors in any logs, syslog; libvirt?


Not that I haven't seen in other successful peoples traces.  I don't have them handy but I'll reply tonight with whatever I get prior to installing the driver.  Like I've said, when the machine freezes its instantaneous and I get no logging.  Magic SysRQ won't reboot it, I have to hard power off.

> **KillerKelvUK said:**
>  have you cleaned the graphics drivers from the guest...thinking if you've had lots of problems maybe there is something underlying the guest rather than the host confit?

I've tried it on fresh installs of the OS too, so apparently not.  Also, I wouldn't expect that to crash the host.

---

