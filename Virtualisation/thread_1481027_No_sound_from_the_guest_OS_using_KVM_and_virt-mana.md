---
title: "No sound from the guest OS using KVM and virt-manager"
date: 2010-05-12
forum: Virtualisation
---

### Post by trubshac on 2010-05-12
Hi

My host is a fresh install of 64 bit Ubuntu 10.04 on an Intel dual core E5400 with 4G ram.
I have added KVM and virt-manager (v0.8.2) using synaptic.

My first guest is a fresh install of 64 bit Ubuntu 10.04, allocated 1 core, 1GB ram and the es1370 sound card.
My second quest is a fresh install of Windows XP also allocated 1 core, 1GB ram and es1370.

Sound within the host system works fine.
When I generate a sound from within either of the guests, I hear nothing.

lspci from within the Ubuntu GUEST shows:
00:04.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]

dmesg | grep 1370 within the Ubuntu guest shows:
[    5.274026] ENS1370 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 11 (level,high) -> IRQ 11
[    5.274086] ENS1370 0000:00:04.0 setting latency timer to 64

I have also tried replacing the es1370 sound card with ac97, but had the same result.

Does anyone have any suggestions of how I can get sounds from my guest OS to me ears?
Thanks in anticipation.

---

### Post by maxter on 2010-06-10
Same problem here.
I searched for help on the net, but it seems that there is a lack of informations for non developers about kvm.

no one can help us to try a debug?

Tx

---

### Post by XanKriegor on 2010-06-22
I have a problem with sound in guest created with virt-manager. No sound. But if you create VM without virt-manager:
sudo kvm -cpu  core2duo -name desktop  -vnc :1 -vga std -soundhw es1370 -hda /vm/desktop.img -m 2048 -enable-kvm -net nic

SOUND ON! but network don't work

I saw that virt-manager runs kvm with follow command

 ps -ux | grep kvm
root      5770  109  1.7 2290260 103820 ?      Sl   19:22   0:01 /usr/bin/kvm -S -M pc-0.12 -enable-kvm -m 2048 -smp 2 -name desktop -uuid 892ff5fb-75fc-f146-192a-3384b1f1e4b2 -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/desktop.monitor,server,nowait -monitor chardev:monitor -boot c -drive file=/vm/desktop.img,if=virtio,index=0,boot=on,format=qcow2 -net nic,macaddr=52:54:00:0b:92:6b,vlan=0,model=ne2k_pci,name=ne2k_pci.0 -net tap,fd=43,vlan=0,name=tap.0 -serial none -parallel none -usb -vnc 0.0.0.0:1 -vga std -soundhw es1370

as we see soundhw persist in command but sound nothing

Anybody who decide it ?

P.S. Host lucid x64, guest lucid desktop x64

---

### Post by Tristan Schmelcher on 2010-07-04
See [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/591489](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/591489)

---

### Post by Gunnl on 2011-03-20
Is this problem fixed ?
Because I was using x86 and tried out virt-manager and everything worked out of the box with no problems ... then when I decided to install x86_amd64 (talking about the host environment, ubuntu Desktop) virt-manager guests don't have any sound and I noticed that they also dont immediately recognize usb devices like a webcam.

I've been searching, following and trying several solutions and they all more or less refer to the same (QEMU_AUDIO_DRV and VNC not redirecting sound) but for me that is not working or I am doing something wrong.
Can someone with some expertise in this field guide me on the finding and solving of these problems ?
Thank you.

---

