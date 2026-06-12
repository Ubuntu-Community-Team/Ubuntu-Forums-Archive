---
title: "KVM - GPU Passthrough From Ubuntu host to Ubuntu Guest (headless)"
date: 2016-08-12
forum: Virtualisation
---

### Post by calerogers on 2016-08-12
[FONT=Verdana]Hi all,[/FONT]

[FONT=Verdana]I Have been a long time lurker and just now registered because I can't seem to find anything that fits what I am trying to do for once. I have verified that my motherboard and processor support IOMMU, vt-d and vt-x.[/FONT]

[FONT=Verdana]My physical machine specs are:[/FONT]
[FONT=Verdana]- GA x99p SLI motherboard[/FONT]
[FONT=Verdana]- Intel i7 5820k[/FONT]
[FONT=Verdana]- 3x Nvidia GTX 1080[/FONT]

[FONT=Verdana]Essentially my setup is a ubuntu 14.04 host (not necessarily tied to this version) and my guest VM is a ubuntu 16.04. My host is headless (though can connect over VNC) and I have 3 GPUs attached to the physical machine, I would just like to pass through one top this one VM. Throughout all the guides and forum posts I have read it seems all of them relate to passing through to a windows VM and using the GPU for gaming or some other monitor need. In my case all I need on my guest VM is access to a shell and for the GPU to be available (meaning the system can use it for computations), basically no monitor, just the GPU in the system. I’ve attempted to follow various guides and forum posts to no tangible success.[/FONT]

[FONT=Verdana]I started going through steps outlined here:[/FONT]
[[FONT=Verdana]https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/[/FONT]]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/")

[FONT=Verdana]My GPUs are blacklisted and have been properly claimed by the pci-stub, but I am reading this is an outdated method as mentioned here [https://ubuntuforums.org/showthread.php?t=2332943](https://ubuntuforums.org/showthread.php?t=2332943) so not really sure if I should try a different method? And I'm not really sure what the differences are or if it really matters?[/FONT]

[FONT=Verdana]The progress I have made so far seems to pass through the GPU to extent as I am able to see the GPU when I run ```
info pci
``` in the qemu monitor. This works when I attempt to start my VM (using a disk.img that already has 16.04 installed on) using this command (modified from the Puget systems tutorial):[/FONT]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]-smp 4,sockets=1,cores=4,threads=1 \[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]-bios /usr/share/qemu/bios.bin -vga none \
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]-device qxl \
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=off \[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]-device vfio-pci,host=04:00.1,bus=root.1,addr=00.1 \[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]-drive file=/home/username/ubuntu-test.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[FONT=Verdana]Notable differences are not specifying an iso. I should also note I am only able to see the qemu monitor console through my VNC screen (obviously) since running this command starts up a QEMU window. Also, when I do specify an .iso file I do get to the ubuntu installation screen but I am unable to install / move around with the keyboard (though this might be an issue with my VNC) however, ideally, I wouldn't be installing via the GUI or installing the OS at all (it would already be a .img disk ready for starting up).[/FONT]

[FONT=Verdana]Ideally, my process would be this:[/FONT]

[LIST=1]
[*=1]virt-install ubuntu 16.04 OS via a script and pressed file to a .img file (which I have done and verified it works)
[*=1]Shutdown VM
[*=1]modify the XML to add passthrough for the GPU / PCI device OR some other means by adding the GPU / PCI device after the VM is created
[*=1]Restart VM
[*=1]ssh into VM and be able to run lspci | grep NVIDIA and see the GPU passed through
[/LIST]

[FONT=Verdana]As I said, most of the guides / forum posts are for passing through to a Windows VM not a linux one, though I don't think this should change anything? Any tips or links pointing me in the right direction would be greatly appreciated! Thanks![/FONT]

---

### Post by KillerKelvUK on 2016-08-12
Hey Cale, so a couple of obvservations...

[LIST]
[*]Ubuntu 14.04/10 I had several problems with, mostly with pass through due to buggy code etc. If you are using the standard repos then I'd recommend you upgrade your host, obviously if your building kvm, qemu, libvirt then okay.
[*]pci-stub vs. vfio-pci... Both work however the latter was only introduced as of kernel 4.1. You could introduce by hand to an earlier kernel if you like and I know others have on this forum...depends of your competence/capabilities. My personal experience is that vfio-pci is better as in stabler and requires less system change to achieve pass through i.e. fewer driver/module changes. However as your gfx cards are successfully being claimed by the pci-stub driver I'd suggest you stick with this for now and only change once you have everything else resolved.
[*]Regards keyboard and mouse access within a guest...the qemu code includes a vnc and spice server and so when you start a guest using a virtual display adapted like QXL your hosts keyboard and mouse are captured by the host side qemu window and redirected to the guest. However in a gfx pass through scenario you shouldn't use a virtual display adapter, as such the internal vnc/spice servers aren't started and therefore you don't have keyboard and mouse control. There are several solutions available i.e. for installation just pass through your actual usb keyboard and mouse, configure the guest with an ssh server, stop the guest and reconfigure it not to pass through your hosts keyboard and mouse. All control is then via ssh from host to guest...if you want a gui in your guest there are other options too but let's not get over complicated.
[*]VGA arbitration...your post suggests that pass through is working so hold this point as a "likely not required but..." but your host and gfx cards are UEFI capable (I've assumed this from the specs you've shared but I'd recommend you confirm this) as such I'd suggest your guest is reconfigured to use OVMF instead of seabios. It maybe once you're a little further forward with your solution this becomes a requirement i.e. you notice your host display gets corrupted whenever you start a guest with a passed through gfx card. For now put this one on the back burner.
[*]Last one is a pointer on your qemu line, you have '-vga none-' and '-device qxl' in the same command, these contradict one another. As I noted above you may want to use the qxl adapter to complete installation and then remove it once you are ready to pass thru the gfx card.
[/LIST]

Hope this helps, obviously shout up if not.

---

### Post by calerogers on 2016-08-12
Thanks for the reply. I'll upgrade my host to 16.04 just because it seems like the best option in this case and I am not tied to 14.04 for any reason. I see, so if I were to not passthrough the GPU then the QEMU window on the host would be usable due to VNC/spice, but since I am passing through a GPU those features become disabled? So should I completely remove -vga none for now?

Passing through a keyboard and mouse sounds like a whole other slew of issues waiting to be troubleshot :P. I was hoping to avoid that, which is why I installed the ubuntu OS on a .img file first with virt-install and then tried passing through the GPU with the qemu command (all while not using an iso image to install), is something like this not possible?

I forgot about switching to OVMF when I tried, as I had read that before, so I will give that a shot over the seabios.

EDIT:

I might end up trying the vfio-pci instead of pci-stub method after all so that I can assign a specific video card to the guest and so I can use one of the video cards on my host. Since they are all the same model they all get claimed by the stub and I can't use one for the host in troubleshooting.

---

### Post by KillerKelvUK on 2016-08-12
Hey so if you're passing thru your gfx then use '-vga none'. When not passing thru a gfx use '-device qxl'. Key point tho for vnc or spice to work you need to assign a virtual display adapter, if you don't specify a virtual display adapter then vnc and spice will not work so you need another means of getting to the desktop or shell of the guest which is where passing through a physical USB K&M comes in. Like you've said using virt-install is cool so provided you've configured SSH access using this method you should be golden.

Understand and agree with your point about using vfio-pci to capture specific cards rather than the whole vendor and product chain so good shout. Have you verified your cards are assigned in separate iommu groups?

---

### Post by calerogers on 2016-08-12
Hey, yes I have virt-install configured to get ssh running. So basically when I run my virt-install command the end result is a ubuntu 16.04 guest that i can find the IP of by using arp -an and then ssh root@ip and then issue the password I provided via the preseed file. However, when I try to run qemu with this .img disk (result of the virt-install command) I don't believe it fully boots as there is no output from arp -an. I am having trouble understanding the difference between starting a VM with the qemu-system-x86_64 and the virt-install commands and the relationship between them?

---

### Post by KillerKelvUK on 2016-08-12
> **calerogers said:**
> Hey, yes I have virt-install configured to get ssh running. So basically when I run my virt-install command the end result is a ubuntu 16.04 guest that i can find the IP of by using arp -an and then ssh root@ip and then issue the password I provided via the preseed file. However, when I try to run qemu with this .img disk (result of the virt-install command) I don't believe it fully boots as there is no output from arp -an. I am having trouble understanding the difference between starting a VM with the qemu-system-x86_64 and the virt-install commands and the relationship between them?

Post back the qemu cmd that you are using to run the guest after its created with virt-install please?

---

### Post by calerogers on 2016-08-13
Well, a bit of an update after following the guide of Alex Williamson (adapting it ubuntu) I seemingly am able to passthrough the GPU to the VM. I installed the VM through virt-manager and just clicked the "Add hardware" as noted in Alex's guide. Here is the output of lspci

```

lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:01.2 USB controller: Intel Corporation 82371SB PIIX3 USB [Natoma/Triton II] (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:02.0 VGA compatible controller: Cirrus Logic GD 5446
00:03.0 Ethernet controller: Red Hat, Inc Virtio network device
00:04.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 01)
00:05.0 SCSI storage controller: Red Hat, Inc Virtio block device
00:06.0 Unclassified device [00ff]: Red Hat, Inc Virtio memory balloon
00:07.0 VGA compatible controller: NVIDIA Corporation Device 1b80 (rev a1)
00:08.0 Audio device: NVIDIA Corporation Device 10f0 (rev a1)

```

However there appears to be some issue getting it to actually work. I installed the proper drivers (this driver worked for the same OS and GPU on my host) using these instructions:
[http://www.askmetutorials.com/2016/06/install-uninstall-nvidia-driver-36727.html](http://www.askmetutorials.com/2016/06/install-uninstall-nvidia-driver-36727.html)

Not really sure what to do next, do you have any tips?

Thanks,
Cale

---

### Post by calerogers on 2016-08-13
Digging in I have found this

```

nvidia-smi
Unable to determine the device handle for GPU 0000:00:07.0: Unknown Error

```

```


dmesg | grep -i nvidia
[    1.666308] **nvidia**: module license '**NVIDIA**' taints kernel.
[    1.669940] **nvidia**: module verification failed: signature and/or required key missing - tainting kernel
[    1.676048] **nvidia**-nvlink: Nvlink Core is being initialized, major device number 248
[    1.676065] NVRM: loading **NVIDIA** UNIX x86_64 Kernel Module  367.27  Thu Jun  9 18:53:27 PDT 2016
[    1.682973] **nvidia**-modeset: Loading **NVIDIA** Kernel Mode Setting Driver for UNIX platforms  367.27  Thu Jun  9 18:24:10 PDT 2016
[    1.683895] [drm] [**nvidia**-drm] [GPU ID 0x00000007] Loading driver
[    5.197503] input: HDA **NVidia** HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:08.0/sound/card1/input5
[    5.197738] input: HDA **NVidia** HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:08.0/sound/card1/input6
[    5.197940] input: HDA **NVidia** HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:08.0/sound/card1/input7
[    5.198116] input: HDA **NVidia** HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:08.0/sound/card1/input8

```

---

### Post by calerogers on 2016-08-13
Here is the XML for my VM

```

<domain type='kvm' id='18'>
  <name>ubuntu-test08</name>
  <uuid>ea6cca2d-a6a3-b0b6-93cc-6ab8a6324160</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <loader>OVMF.fd</loader>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/backprop/ubuntu-test09.img'/>
      <target dev='vda' bus='virtio'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <alias name='ide0-1-0'/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <alias name='usb0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'>
      <alias name='pci.0'/>
    </controller>
    <controller type='ide' index='0'>
      <alias name='ide0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:f8:73:f1'/>
      <source network='default'/>
      <target dev='vnet2'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/19'/>
      <target port='0'/>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/19'>
      <source path='/dev/pts/19'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='5901' autoport='yes' listen='127.0.0.1'>
      <listen type='address' address='127.0.0.1'/>
    </graphics>
    <sound model='ich6'>
      <alias name='sound0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x4b' slot='0x00' function='0x0'/>
      </source>
      <alias name='hostdev0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x4b' slot='0x00' function='0x1'/>
      </source>
      <alias name='hostdev1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </hostdev>
    <memballoon model='virtio'>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='dynamic' model='apparmor' relabel='yes'>
    <label>libvirt-ea6cca2d-a6a3-b0b6-93cc-6ab8a6324160</label>
    <imagelabel>libvirt-ea6cca2d-a6a3-b0b6-93cc-6ab8a6324160</imagelabel>
  </seclabel>
</domain>

```

---

### Post by KillerKelvUK on 2016-08-13
Hey Cale, sorry I haven't replied sooner, I've been on holiday and was travelling back today so only just seen the updates.  So good news/bad news situation from a quick scan of your last few posts.

Did you update your host to 16.04?  The nvidia drivers maybe complaining about an out-of-date kernel?

Are the stock kernel drivers for nVidia (open) not sufficient for your needs?  Just trying to clarify why you need proprietary drivers in the guest if you don't need a desktop?

---

### Post by calerogers on 2016-08-13
No worries, I appreciate the help. I just updated my host to 16.04 in testing and now trying to reinstall the VM through virt-manager. Something strange I noticed is that I can't change the emulator type on step 5 in the setup process, right now it is /usr/bin/kvm-spice and in Alex's guide it is /usr/libexec/qemu-kvm (not sure if that matters).

I think stock drivers would be fine, I guess I am confused why it isn't showing the model number, etc when I lspci in the guest, I assumed it wasn't initializing correctly. Also, trying to get any information about the GPU errors out which is why I thought it was a driver issue.

---

### Post by KillerKelvUK on 2016-08-13
Yeah the emu type is fixed in virt-manager, if you want to change it then use virsh and cut the xml to how you need. However if you follow the path to the binary shown in virt-manager you should find it symlinks back to qemu. AW's guide is relevant to Fedora, as you've prev said, so this difference you can just ignore.

Interesting what you said about it not showing the model numbers via lspci in the guest. I've not tried my GTX 970 in a Linux guest so can't say for sure but I believe my DVB card reports different in guest than in host. If your still stuck tomorrow I'll spin up an Ubuntu guest and throw in my gfx to give you a comparison.

---

### Post by KillerKelvUK on 2016-08-14
Gave this a quick bash today...

Host is 16.04, uses iGDP for host display, Asus GFX 970 I pass through to a Windows and 'other' guests (not at the same time obviously).

```

lspci -d 10de: -v
01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. GM204 [GeForce GTX 970]
    Flags: fast devsel, IRQ 16
    Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at e0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at ef000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci
    Kernel modules: nvidiafb, nouveau


01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. GM204 High Definition Audio Controller
    Flags: fast devsel, IRQ 17
    Memory at ef080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci
    Kernel modules: snd_hda_intel


```

New 16.04 guest configured with q35 and OVMF and passing through my Asus GTX 970.

```

sudo lspci -d 10de: -vv
[sudo] password for kelvin: 
02:02.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. GM204 [GeForce GTX 970]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 32
    Region 0: Memory at a2000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at 90000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at a0000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at c000 [size=128]
    Expansion ROM at a3080000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee02000  Data: 40e2
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau


02:06.0 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. GM204 High Definition Audio Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 20
    Region 0: Memory at a3000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```

Same of the guest dmesg output 

```

dmesg | grep nouveau
[    1.205353] fb: switching to nouveaufb from EFI VGA
[    1.206713] nouveau 0000:02:02.0: NVIDIA GM204 (124020a1)
[    1.291451] nouveau 0000:02:02.0: bios: version 84.04.36.00.5e
[    1.292297] nouveau 0000:02:02.0: gr: using external firmware
[    1.292313] nouveau 0000:02:02.0: Direct firmware load for nvidia/gm204/fecs_inst.bin failed with error -2
[    1.292319] nouveau 0000:02:02.0: gr: failed to load fecs_inst
[    1.292335] nouveau 0000:02:02.0: disp: dcb 15 type 8 unknown
[    1.294194] nouveau 0000:02:02.0: fb: 4096 MiB GDDR5
[    1.295719] nouveau 0000:02:02.0: DRM: VRAM: 4096 MiB
[    1.295722] nouveau 0000:02:02.0: DRM: GART: 1048576 MiB
[    1.295728] nouveau 0000:02:02.0: DRM: TMDS table version 2.0
[    1.295732] nouveau 0000:02:02.0: DRM: DCB version 4.1
[    1.295736] nouveau 0000:02:02.0: DRM: DCB outp 00: 01000f02 00020030
[    1.295741] nouveau 0000:02:02.0: DRM: DCB outp 01: 02000f00 00000000
[    1.295744] nouveau 0000:02:02.0: DRM: DCB outp 02: 04811f82 00020030
[    1.295756] nouveau 0000:02:02.0: DRM: DCB outp 03: 02822f62 00020010
[    1.295758] nouveau 0000:02:02.0: DRM: DCB outp 05: 02833f76 04400020
[    1.295760] nouveau 0000:02:02.0: DRM: DCB outp 06: 02033f72 00020020
[    1.295762] nouveau 0000:02:02.0: DRM: DCB outp 15: 01df4ff8 00000000
[    1.295764] nouveau 0000:02:02.0: DRM: DCB conn 00: 00001030
[    1.295766] nouveau 0000:02:02.0: DRM: DCB conn 01: 01000131
[    1.295768] nouveau 0000:02:02.0: DRM: DCB conn 02: 00010261
[    1.295770] nouveau 0000:02:02.0: DRM: DCB conn 03: 00020346
[    1.295772] nouveau 0000:02:02.0: DRM: DCB conn 04: 00000470
[    1.295774] nouveau 0000:02:02.0: DRM: Pointer to flat panel table invalid
[    1.310633] nouveau 0000:02:02.0: DRM: unknown connector type 70
[    1.310670] nouveau 0000:02:02.0: DRM: failed to create encoder 1/8/0: -19
[    1.310674] nouveau 0000:02:02.0: DRM: Unknown-1 has no encoders, removing
[    1.474941] nouveau 0000:02:02.0: DRM: MM: using COPY for buffer copies
[    1.682840] nouveau 0000:02:02.0: DRM: allocated 1920x1080 fb: 0x60000, bo ffff880034668000
[    1.682926] fbcon: nouveaufb (fb0) is primary device
[    2.224400] nouveau 0000:02:02.0: fb0: nouveaufb frame buffer device
[    2.234069] [drm] Initialized nouveau 1.3.1 20120801 for 0000:02:02.0 on minor 0

```

---

### Post by calerogers on 2016-08-14
Thanks for the help! I think I got it working on my end as well. Nvidia wasn't loading the drivers correctly but after shutting down the VM and adding 
```

<kvm>
  <hidden state='on'/>
</kvm>

```

This made things happier.

---

### Post by KillerKelvUK on 2016-08-15
> **calerogers said:**
> Thanks for the help! I think I got it working on my end as well. Nvidia wasn't loading the drivers correctly but after shutting down the VM and adding 
```

<kvm>
  <hidden state='on'/>
</kvm>

```

This made things happier.

Wow, didn't realised nVidia's trix extended to the linux drivers...this is the hack necessary to get the drivers working in Windows, apols I would have said sooner but I really didn't think it was needed for the linux, my bad.

---

### Post by calerogers on 2016-08-15
Yeah I am not sure :/

I've kinda run into another snag unfortunately. So my system consists of 4x GTX 1080s now. 3 of them work with passthrough with nvidia-smi properly showing. However with the last one I am getting some issues.

When I tail syslog I see
```

Aug 15 08:49:00 ubuntu-host kernel: [  213.475370] NVRM: RmInitAdapter failed! (0x26:0xffff:1172)
Aug 15 08:49:00 ubuntu-host kernel: [  213.475377] NVRM: rm_init_adapter failed for device bearing minor number 0

```

and
```


cat /proc/driver/nvidia/gpus/0000\:02\:03.0/information 
Model:          GeForce GTX 1080
IRQ:            46
GPU UUID:      GPU-????????-????-????-????-????????????
Video BIOS:      ??.??.??.??.??
Bus Type:      PCI
DMA Size:      47 bits
DMA Mask:      0x7fffffffffff
Bus Location:      0000:02:03.0
Device Minor:      0

```

Though I see the card here
```

lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:01.0 PCI bridge: Red Hat, Inc. QEMU PCI-PCI bridge
02:01.0 Ethernet controller: Red Hat, Inc Virtio network device
02:02.0 SCSI storage controller: Red Hat, Inc Virtio block device
02:03.0 VGA compatible controller: NVIDIA Corporation Device 1b80 (rev a1)
02:04.0 Audio device: NVIDIA Corporation Device 10f0 (rev a1)
02:05.0 Unclassified device [00ff]: Red Hat, Inc Virtio memory balloon

```

On the host machine I see this a ton in syslog as well, this the card that isn't working when I am passing it through:
```

[34060.617993] vfio-pci 0000:4e:00.0: BAR 3: can't reserve [mem 0x60000000-0x61ffffff 64bit pref]

```


Note that I used the same VM for each GPU (was just changing which PCI card to passthrough) so it shouldn't be a driver issue. Googling "RmInitAdapter failed!" isn't yielding much info, some forums suggest it might be a power issue. Something else to note, this same issue happened when I had only 3 cards plugged in, with the last one plugged in causing this issue. Is it possible the PCIE slot 4 on my motherboard is bad or something like that?

---

### Post by calerogers on 2016-08-15
I may have found a fix for my earlier issue

---

### Post by KillerKelvUK on 2016-08-15
You fixed it bud? Be interested to know what the issue was.

---

### Post by calerogers on 2016-08-15
Found this option I had to set in the GRUB file, by none other than Alex Williamson :P

[https://www.redhat.com/archives/vfio-users/2016-April/msg00236.html](https://www.redhat.com/archives/vfio-users/2016-April/msg00236.html)

Like the OP of that thread I was seeing efifb in[COLOR=#000000] /proc/iomem on the card that was seeing those BAR 3: can't reserve errors - still not exactly sure what that setting is though. As far as I can tell efifb is specific to Apple computers? (results from googling)[/COLOR]

---

### Post by KillerKelvUK on 2016-08-17
Glad you sorted this :-)

---

### Post by kvasko on 2016-12-08
I am getting the same error with my guest VM

$nvidia-smi
 Unable to determine the device handle for GPU 0000:05:00.0: Unknown Error

But I am not getting the same error you are getting on the host VM. Did you ever run across any other errors that might have fixed it?

---

