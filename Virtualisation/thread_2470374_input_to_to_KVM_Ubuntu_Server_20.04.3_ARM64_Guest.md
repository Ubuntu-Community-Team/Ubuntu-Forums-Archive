---
title: "input to to KVM Ubuntu Server 20.04.3 ARM64 Guest?"
date: 2021-12-28
forum: Virtualisation
---

### Post by MAFoElffen on 2021-12-28
Host is Ubuntu 20.04.3 QEMU/KVM on Intel i7 amd64 hardware.

Guest is Ubuntu 20.04.3 Server arm64 Guest. ARM arch is through AARCH64. Default for ARM64 is EFI boot only, nograhics, serial console text interaction. Origianl install media was Ubuntu Server 18.04.6 ARM64.

Trying to extend the capabilities of the guest VM. Added ramfb video device (manually to the XML) as a framebuffer. Support by QEMU for ramfb came in libvirt version 5.9. Added Spice Graphics, as a display device...

Domain XML:
```

<domain type="qemu">
  <name>ubuntu-2004-aarch64</name>
  <uuid>9b2936fa-ea83-45cc-9366-d3609e195f77</uuid>
  <title>Ubuntu Server 20.04 ARM64</title>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://ubuntu.com/ubuntu/18.04"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit="KiB">4194304</memory>
  <currentMemory unit="KiB">4194304</currentMemory>
  <vcpu placement="static">2</vcpu>
  <os>
    <type arch="aarch64" machine="virt-4.2">hvm</type>
    <loader readonly="yes" type="pflash">/usr/share/AAVMF/AAVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/ubuntu-2004-aarch64_VARS.fd</nvram>
    <boot dev="hd"/>
  </os>
  <features>
    <acpi/>
    <gic version="2"/>
  </features>
  <cpu mode="custom" match="exact" check="none">
    <model fallback="allow">cortex-a57</model>
  </cpu>
  <clock offset="utc"/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-aarch64</emulator>
    <disk type="file" device="disk">
      <driver name="qemu" type="qcow2"/>
      <source file="/var/lib/libvirt/images/ubuntu-2004-aarch64.qcow2"/>
      <target dev="vda" bus="virtio"/>
      <address type="pci" domain="0x0000" bus="0x05" slot="0x00" function="0x0"/>
    </disk>
    <disk type="file" device="cdrom">
      <driver name="qemu" type="raw"/>
      <target dev="sda" bus="scsi"/>
      <readonly/>
      <address type="drive" controller="0" bus="0" target="0" unit="0"/>
    </disk>
    <controller type="usb" index="0" model="qemu-xhci" ports="15">
      <address type="pci" domain="0x0000" bus="0x02" slot="0x00" function="0x0"/>
    </controller>
    <controller type="scsi" index="0" model="virtio-scsi">
      <address type="pci" domain="0x0000" bus="0x03" slot="0x00" function="0x0"/>
    </controller>
    <controller type="pci" index="0" model="pcie-root"/>
    <controller type="pci" index="1" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="1" port="0x8"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x0" multifunction="on"/>
    </controller>
    <controller type="pci" index="2" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="2" port="0x9"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x1"/>
    </controller>
    <controller type="pci" index="3" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="3" port="0xa"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x2"/>
    </controller>
    <controller type="pci" index="4" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="4" port="0xb"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x3"/>
    </controller>
    <controller type="pci" index="5" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="5" port="0xc"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x4"/>
    </controller>
    <controller type="pci" index="6" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="6" port="0xd"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x5"/>
    </controller>
    <controller type="pci" index="7" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="7" port="0xe"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x6"/>
    </controller>
    <controller type="pci" index="8" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="8" port="0xf"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x7"/>
    </controller>
    <controller type="virtio-serial" index="0">
      <address type="pci" domain="0x0000" bus="0x04" slot="0x00" function="0x0"/>
    </controller>
    <interface type="network">
      <mac address="52:54:00:20:8c:99"/>
      <source network="default"/>
      <model type="virtio"/>
      <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
    </interface>
    <serial type="pty">
      <target type="system-serial" port="0">
        <model name="pl011"/>
      </target>
    </serial>
    <console type="pty">
      <target type="serial" port="0"/>
    </console>
    <channel type="unix">
      <target type="virtio" name="org.qemu.guest_agent.0"/>
      <address type="virtio-serial" controller="0" bus="0" port="1"/>
    </channel>
    <graphics type="spice" autoport="yes">
      <listen type="address"/>
      <image compression="off"/>
      <gl enable="no" rendernode="/dev/dri/by-path/pci-0000:00:02.0-render"/>
    </graphics>
    <video>
      <model type="ramfb" heads="1" primary="yes"/>
    </video>
    <memballoon model="virtio">
      <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>
    </memballoon>
    <rng model="virtio">
      <backend model="random">/dev/urandom</backend>
      <address type="pci" domain="0x0000" bus="0x07" slot="0x00" function="0x0"/>
    </rng>
  </devices>
</domain>

```
I don't want to display graphics as a desktop, but just be able to do framebuffer console vtty, instead of serial ttyAMA0... So I can run top, HTOP and such... Text-Based Console utilities.

If you are on a serial display,you see all the serial console messages and boot prompts until the Login, which is on a ttyAMAO session. You can log in and do everything... but of course as being on ttyAMAO, it just scrolls text down the screen.

It does fine displaying the framebuffer, to a point... though a bit cryptic. At  boot, if you view with Spice display, you see the Tiano UEFI framebuffer  of it's logo, then 3 messages saying that it is booting off the efi  stubs... Then is black until it gets to the Login prompt... Which is on a  vtty session. You cannot login, because even though you can select the screen and the input appears that changes focus to the VM... And gives the helper text in the display to press <Cntrl-l> and <Alt-l> to release that focus... There is no Keyboard input to the session(???)

If I remove the ramfb device and Spice Display... Well, serial console still works either way. AARCH64 and ARM has a bug and does not work with VGA type devices.

Any ideas on correcting the input from keyboard to the graphics session of this ARM VM?

---

### Post by MAFoElffen on 2021-12-28
> **MAFoElffen said:**
> Any ideas on correcting the input from keyboard to the graphics session of this ARM VM?
Never mind... I must be tired.

Added this stub to the devices XML section:
```

    <input type="keyboard" bus="usb">
      <address type="usb" bus="0" port="1"/>
    </input>

```
Which is ust a Generic USB Keyboard for Input... (Translation; some type of video hardware,a display 'and' a keyboard.) Now it works fine, and comes up on tty1.

Otherwise it still thought it was headless, and didn't have the correct connections to the VM... I thought I also might need a Spice channel, had added it, but later removed it, and it works the same as when it was there. 

EDIT: Since QEMU/KVM, I could have cheated the video in other ways, specific to QEMU/KVM, but then the VM would not have been transportable to an ARM64 hardware based hardware, nor would not have been an accurate machine emulation to test against...

---

