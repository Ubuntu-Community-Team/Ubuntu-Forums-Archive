---
title: "VGA passthrough"
date: 2015-03-01
forum: Virtualisation
---

### Post by KillerKelvUK on 2015-03-01
Still leaning all about this so I likely have incorrect expectations or bad understanding of the various requirements so would appreciate a sense check and recommendations for achieving pass-through...My aspiration is to have the Intel IGD for host only and pass through the Nvidia card to the Win8.1 guest.

My host environment is an Intel i7 4790S, ASRock Z97 Extreme 6, Palit Nvidia GTX 650, 32GB RAM & lots of storage, the host os is Ubuntu 14.10 server (kernel 3.16.0-31) with stock installations of KVM, Qemu, Libvirt, Virt-Manager and I've used Gerd Hoffmann's OVMF repo for the pure-efi.fd.

I'm aware of the ACS Overide and i915 Arbiter patches but I *believe* I don't require them...my reasoning is below.

VT-x and VT-d capable and enabled in BIOS, modules are loading in the host and the various checks to confirm all pass.  I've added kernel options to enable Intel IOMMU as as well as assigning the Nvidia devices to the PCI-Stub.

IOMMU Groups:  My Nvidia card (video & audio) is in IOMMU Group1, the only other device in this group is a PCIe Controller (I've tried adding the PCIe controller into the PCI-Stub, this doesn't seem to do anything).  My *belief* is that as I'm working only within a single IOMMU group I do not require the ACS Overide patch...is that right?

OVMF+VGA:  I've confirmed the VBIOS of the Nvidia card is EFI capable and have also confirmed that the Windows guest is booting in EFI mode.  Again my *belief* is that because of this combination i do not require the i915 Arbiter patch?  To take this one step further I've tried pass-through to both a Windows7 guest and a Windows8.1 guest...with Windows 7 I've not been able to get any desktop display from the Nvidia card, if I add a virtual display adapter to get a session the Nvidia card is shown, the drivers install but Code 43 which I am unable to resolve even with the kvm=off and hyperv adjustments (think this is all related to bad EFI implementation in Win7 which results in hitting the VGA arbitration bug?).  In Windows8.1 however I get a much better result (I *believe* this is because of a better EFI implementation)...the Win8 reports the hardware (pre driver install) as fully functional and I get basic display performance.  I then install the Nvidia drivers and Code 43...again I've tried the kvm=off and hyperv adjustments but I cannot fix this problem.

My aim here is to use Virt-Manager and so I've been doing all my testing via that GUI plus manual editing of the Libvirt xml via the cli.  I've confirmed that even through I'm using Virt-Manager the pass-through is with VFIO...below is my libvirt xml and the qemu line as its run by Virt-Manager...

Libvirt XML..

```

<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>blackwindows8</name>
  <uuid>e6f8bb1e-5b39-46b6-825f-7002057d00b3</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-utopic'>hvm</type>
    <loader>OVMF.fd</loader>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell</model>
    <vendor>Intel</vendor>
    <feature policy='require' name='vme'/>
    <feature policy='require' name='dtes64'/>
    <feature policy='require' name='vmx'/>
    <feature policy='require' name='xtpr'/>
    <feature policy='require' name='est'/>
    <feature policy='require' name='monitor'/>
    <feature policy='require' name='smx'/>
    <feature policy='require' name='abm'/>
    <feature policy='require' name='tm'/>
    <feature policy='require' name='acpi'/>
    <feature policy='require' name='osxsave'/>
    <feature policy='require' name='ht'/>
    <feature policy='require' name='pdcm'/>
    <feature policy='require' name='pdpe1gb'/>
    <feature policy='require' name='f16c'/>
    <feature policy='require' name='ds'/>
    <feature policy='require' name='invtsc'/>
    <feature policy='require' name='tm2'/>
    <feature policy='require' name='ss'/>
    <feature policy='require' name='pbe'/>
    <feature policy='require' name='ds_cpl'/>
    <feature policy='require' name='rdrand'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='hypervclock' present='yes'/>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
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
      <source file='/mnt/vms/blackwindows8.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:03:e7:d8'/>
      <source bridge='br0'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
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
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </sound>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
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
  <qemu:commandline>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5901,disable-ticketing'/>
  </qemu:commandline>
</domain>

```

The qemu command run by Virt-Manager... (have added the CR's to make this easier to read but more to scroll)

```

qemu-system-x86_64 
-enable-kvm 
-name blackwindows8 
-S 
-machine pc-i440fx-utopic,accel=kvm,usb=off 
-cpu Haswell,+invtsc,+abm,+pdpe1gb,+rdrand,+f16c,+osxsave,+pdcm,+xtpr,+tm2,+est,+smx,+vmx,+ds_cpl,+monitor,+dtes64,+pbe,+tm,+ht,+ss,+acpi,+ds,+vme,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1000,kvm=off 
-bios OVMF.fd 
-m 8192 
-realtime mlock=off 
-smp 4,sockets=4,cores=1,threads=1 
-uuid e6f8bb1e-5b39-46b6-825f-7002057d00b3 
-nographic 
-no-user-config 
-nodefaults 
-chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/blackwindows8.monitor,server,nowait 
-mon chardev=charmonitor,id=monitor,mode=control 
-rtc base=localtime,driftfix=slew 
-global kvm-pit.lost_tick_policy=discard 
-no-hpet 
-no-shutdown 
-global PIIX4_PM.disable_s3=1 
-global PIIX4_PM.disable_s4=1 
-boot strict=on 
-device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x4.0x7 
-device ich9-usb-uhci1,masterbus=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x4 
-device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x4.0x1 
-device ich9-usb-uhci3,masterbus=usb.0,firstport=4,bus=pci.0,addr=0x4.0x2 
-device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x5 
-drive file=/mnt/vms/blackwindows8.qcow2,if=none,id=drive-virtio-disk0,format=qcow2 
-device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x6,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 
-netdev tap,fd=25,id=hostnet0 
-device rtl8139,netdev=hostnet0,id=net0,mac=52:54:00:03:e7:d8,bus=pci.0,addr=0xa 
-chardev pty,id=charserial0 
-device isa-serial,chardev=charserial0,id=serial0 
-chardev spicevmc,id=charchannel0,name=vdagent 
-device virtserialport,bus=virtio-serial0.0,nr=1,chardev=charchannel0,id=channel0,name=com.redhat.spice.0 
-device usb-tablet,id=input0 
-device intel-hda,id=sound0,bus=pci.0,addr=0x3 
-device hda-duplex,id=sound0-codec0,bus=sound0.0,cad=0 
-chardev spicevmc,id=charredir0,name=usbredir 
-device usb-redir,chardev=charredir0,id=redir0 
-chardev spicevmc,id=charredir1,name=usbredir 
-device usb-redir,chardev=charredir1,id=redir1 
-chardev spicevmc,id=charredir2,name=usbredir 
-device usb-redir,chardev=charredir2,id=redir2 
-chardev spicevmc,id=charredir3,name=usbredir 
-device usb-redir,chardev=charredir3,id=redir3 
-device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x8 
-device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0x9 
-device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x7 
-spice port=5901,disable-ticketing -msg timestamp=on

```

There is a dmesg spew of errors when the guest is run, my googling hasn't found anything conclusive yet but some posts relate this to the i915 arbiter issue...can this be confirmed?

```
[ 9731.055088] dmar: DRHD: handling fault status reg 3
[ 9731.055098] dmar: DMAR:[DMA Read] Request device [01:00.1] fault addr 2231b8000 
DMAR:[fault reason 12] non-zero reserved fields in PTE

```

My grub boot has the following...

```
GRUB_CMDLINE_LINUX_DEFAULT="intremap=no_x2apic_optout intel_iommu=on,igfx_off pci-stub.ids=10de:11c8,10de:0e0b"
```

---

### Post by redger on 2015-03-01
your probably most likely relates to setting all the HyperV enlightenments ON ..... unfortunately you need to turn them OFF of NVidia cards. NVIDIA have created drivers which react badly to these options.

remove the following and try again
[LIST]
[*]```
   <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
    </hyperv>
```
[*]```
    <timer name='hypervclock' present='yes'/>
```
[/LIST]


I think you're ok with this one, but you may try without
```
    <timer name='hpet' present='no'/>
```

You might also want to change your NIC to use virtio - it'll perform much better (not sure if Windows will complain about the change - hopefully not, but it will certainly need the drivers)

You're correct that the arbiter patch is unnecessary when using UEFI boot with OVMF

---

### Post by KillerKelvUK on 2015-03-01
Hey redger, so your post was 50% of the answer...the other 50% was the kernel flag 'intel_iommu=on,igfx_off'...

I've only just purchased this hardware and noticed almost immediately that when I passed just 'intel_iommu=on' I lost audio on the host (HDMI audio).  A bit of googling landed me on a known bug which covered a multitude of issues, the resolution of which was to append 'igfx_off' to the parameter...this fixed the host HDMI audio out but was seemingly also the source of the dmar errors in my dmesg output when I ran the VMs.  I removed the 'igfx_off' from the kernel parameter and the code 43 issue vanished provided I corrected the guest XML as per your post above.

So as it stands now I can successfully boot both a Windows 7 and Windows 8.1 guest with GTX 650 drivers loading however guest audio is flaky and I've lost all host audio! :-/

---

### Post by redger on 2015-03-01
ouch, odd that you lose host audio. Is it in the same IOMMU group as the graphics card ?

what sort of guest audio are you using ? Presumably there's no point in directing the guest to use ALSA on the host .. because there's no sound on the host ......

you can go back and use an "old" NVidia driver prior to the change which prevents use of HyperV enlightenments (not sure which one ... go back a year or so eg. prior to 337.88) and try it with the HyperV options .... who knows it *might* work

here's discussion of a patch [http://lists.gnu.org/archive/html/qemu-devel/2014-06/msg00319.html]("http://lists.gnu.org/archive/html/qemu-devel/2014-06/msg00319.html") that seems to mark the beginning of a minor arms race with NVidia

---

### Post by KillerKelvUK on 2015-03-01
No, the analogue and HDMI audio controllers are in separate IOMMU groups and neither is in the same IOMMU as the Nvidia card!  Quick bodge is to use the analogue out for the host which still works, oddly then the HDMI audio out for the VM's using Nvidia now works without a hitch!?

Might have a look at trying an old Nvidia driver to see if that makes a difference, thanks for the suggestion.

One other quick and related questions...should I be able to get a 2nd graphics adapter working in the VM...I tried adding in one of the virtual options but Windows reported a driver issue saying the driver that POSTed isn't valid for this hardware.  The reason I want to is sothat I can also use SPICE as a remote desktop client, most of my day-to-day windows effort doesn't need the grunt of the Nvidia card and so SPICE works fine.  I know I can just modify the hardware with Virt-Manager as and when with no issue, was just curious to understand this?

```

kelvin@blackserver:~$ sh ./iommu.sh 
### Group 0 ###
    00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
### Group 1 ###
    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
    01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 650 OEM] (rev a1)
    01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
### Group 2 ###
    00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
### Group 3 ###
    00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
### Group 4 ###
    00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
### Group 5 ###
    00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
### Group 6 ###
    00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
### Group 7 ###
    00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
### Group 8 ###
    00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
### Group 9 ###
    00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
    00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
    00:1c.6 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 7 (rev d0)
    03:00.0 PCI bridge: ASMedia Technology Inc. Device 1184
    04:01.0 PCI bridge: ASMedia Technology Inc. Device 1184
    04:03.0 PCI bridge: ASMedia Technology Inc. Device 1184
    04:05.0 PCI bridge: ASMedia Technology Inc. Device 1184
    04:07.0 PCI bridge: ASMedia Technology Inc. Device 1184
    06:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
    08:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
    09:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller
### Group 10 ###
    00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
### Group 11 ###
    00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
    00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
    00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller

```

---

### Post by redger on 2015-03-01
you appear to have 3 audio controllers ("sound cards")
[LIST]
[*]The NVidia graphics card audio 01:00.1 is in group 1 along with the video card
[*]Device 00:03.0 in group 3 which looks like it might be the audio controller for the Intel video function ie. the Intel "HDMI" output
[*]Device 00:1b.0 in group 8 which is probably a separate audio device (SPDIF and analogue ?)
[/LIST]
You should pass the NVidia device through and it will probably work

You can direct the VM sound output to a host device. I experienced best outcomes using ALSA and the qemu "HDA" audio device, better than Pulseaudio but not as good as a USB sound device attached to a passed through USB controller. You could modify your xml like this
```
  <qemu:commandline>
    <qemu:env name='QEMU_ALSA_DAC_BUFFER_SIZE' value='512'/>
    <qemu:env name='QEMU_ALSA_DAC_PERIOD_SIZE' value='170'/>
    <qemu:env name='QEMU_AUDIO_DRV' value='alsa'/>
    <qemu:arg value='-spice'/>
    <qemu:arg value='port=5901,disable-ticketing'/>
  </qemu:commandline>
```
Pulseaudio is better for sharing ... but is very "laggy". ALSA access suffers "less" lag but doesn't share very well

as for a second graphics adapater ... I assume you mean you want access to a remote session when you're not in front of the VMs monitor for some reason. I Install TightVNC for WIndows to achieve this outcome. It runs on Windows startup so I can always see the screen "remotely" without being in front of the VMs monitors

---

### Post by KillerKelvUK on 2015-03-02
So I believe I found the culprit for my audio issues, all related to IOMMU...see here [https://bugzilla.kernel.org/show_bug.cgi?id=76331](https://bugzilla.kernel.org/show_bug.cgi?id=76331).

Will looking guest audio redirection if I can't work out how to apply the fix mention in the bug.  Really wanted to avoid any modifications to stock but unless the fix was put in the upstream kernel and ubuntu have wrapped that into release schedules I'm looking at having to build my own kernel to resolve this.

:-(

---

