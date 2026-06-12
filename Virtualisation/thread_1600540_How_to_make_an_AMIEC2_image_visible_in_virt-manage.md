---
title: "How to make an AMI/EC2 image visible in virt-manager"
date: 2010-10-19
forum: Virtualisation
---

### Post by candlerb on 2010-10-19
I am able to run an Ubuntu AMI/EC2 image from the command line, following the instructions at
[https://help.ubuntu.com/community/UEC/Images#Run%20Images%20locally%20without%20a%20Cloud](https://help.ubuntu.com/community/UEC/Images#Run%20Images%20locally%20without%20a%20Cloud)

Specifically, I have a 10.10 AMI running under 10.04, using this command (*):

```

kvm -drive file=disk.img,if=virtio,boot=on -kernel maverick-server-uec-i386-vmlinuz-virtual \
 -net nic,model=virtio -net "user,hostfwd=tcp::5555-:22" \
 -append "root=/dev/vda ro init=/usr/lib/cloud-init/uncloud-init ds=nocloud ubuntu-pass=ubuntu"

```

However, I would like the image to be visible and controllable through virt-manager, and I can't see how to do this.

If I create a new VM through virt-manager, with disk.img as the disk, when I turn it on it tells me it is not a bootable image. That's obviously correct - the kernel is in a separate file.

So how do I import it? Would I have to write an XML config by hand? Does someone have a template XML that I can copy? Can it only be done if the host is running 10.10 ?

I've looked at virt-image(1) and virt-image(5) but I don't see how to refer to the kernel image from the XML.

Thanks,

Brian.

(*) When I tried it using the floppy boot method, it failed saying "error: no such device: uec-rootfs". I am guessing this is because my host platform is 10.04 instead of 10.10. Unfortunately this host is one I want to keep on an LTS release.

---

### Post by candlerb on 2010-10-19
Answering myself, I've started hacking together a script which generates the XML (below). It seems strange that I have to do this - is there really no simple interface for creating VMs from disk images??

```

#!/bin/sh -e

# Based on instructions from:
# https://help.ubuntu.com/community/UEC/Images#Run%20Images%20locally%20without%20a%20Cloud
# https://help.ubuntu.com/community/KVM/Networking#Configuring%20Bridged%20Networking

NAME="$1"
BASEDIR=/v/build/uec-vm
FLAVOUR=maverick-server-uec-i386
MACADDR="52:54:$(dd if=/dev/urandom bs=1 count=16 2>/dev/null | md5sum | sed 's/^\(..\)\(..\)\(..\)\(..\).*$/\1:\2:\3:\4/')"
UUID=`uuidgen`
XML="/etc/libvirt/qemu/$NAME.xml"
IMAGE="$BASEDIR/$NAME.qcow2"

if [ -z "$NAME" ]; then
  echo "Usage: $0 <name>"
  echo "Then go into virsh, and type:"
  echo "  define /etc/libvirt/qemu/<name>.xml"
  echo "  start <name>"
  echo "  console <name>    -- ^] to exit"
  exit 1
fi
if [ -f "$XML" ]; then
  echo "$XML already exists!"
  exit 1
fi
if [ -f "$IMAGE" ]; then
  echo "$IMAGE already exists!"
  exit 1
fi

qemu-img create -f qcow2 -b "$BASEDIR/$FLAVOUR.img" "$IMAGE"

cat <<EOS >"/etc/libvirt/qemu/$NAME.xml"
<domain type='kvm'>
  <name>$NAME</name>
  <uuid>$UUID</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.12'>hvm</type>
    <loader>$BASEDIR/$FLAVOUR-loader</loader>
    <kernel>$BASEDIR/$FLAVOUR-vmlinuz-virtual</kernel>
    <cmdline>root=/dev/vda ro console=ttyS0 init=/usr/lib/cloud-init/uncloud-init ds=nocloud ubuntu-pass=ubuntu</cmdline>
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
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='$BASEDIR/$NAME.qcow2'/>
      <target dev='vda' bus='virtio'/>
    </disk>
    <interface type='network'>
      <source network='default'/>
    <!--
    <interface type='bridge'>
      <source bridge='br0'/>
    -->
      <mac address='$MACADDR'/>
      <model type='virtio'/>
    </interface>
    <console type='pty'>
      <target port='0'/>
    </console>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>
EOS

```

---

