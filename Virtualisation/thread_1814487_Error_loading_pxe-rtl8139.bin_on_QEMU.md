---
title: "Error loading pxe-rtl8139.bin on QEMU"
date: 2011-07-29
forum: Virtualisation
---

### Post by josir on 2011-07-29
Hi folks, 

Host: 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 x86_64 GNU/Linux
Guest: 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2008 x86_64 GNU/Linux

after a kernel upgrade, my vm guest started to give the following initialization message:

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/qemu-system-x86_64 -S -M pc-0.11 -enable-kvm -m 1700 -smp 1 -name Linux17 -uuid c6875fe4-68ca-48ed-ede4-3b8f9507a5eb -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/Linux17.monitor,server,nowait -monitor chardev:monitor -boot c -drive file=/srv/Linux17.img,if=ide,index=0,boot=on,format=raw -drive file=/srv/dados/Linux17_1.img,if=ide,index=1,format=raw -drive file=/srv/pool/Linux17_2.img,if=ide,index=2,format=raw -net nic,macaddr=52:54:f2:fd:83:fe,vlan=0,name=nic.0 -net tap,fd=33,vlan=0,name=tap.0 -serial none -parallel none -usb -vnc 127.0.0.1:0 -k pt-br -vga cirrus 
Could not open option rom 'pxe-rtl8139.bin': No such file or directory

Digging around I found this post [1] but it related to another kernel.

The vm guest started but I don't know this error affects network performance.

I tried also with virtio [2] but it didn't find either virtio. 

The guest machine informs that there's a network board and the network is working.

root@linux17:~# lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:01.2 USB Controller: Intel Corporation 82371SB PIIX3 USB [Natoma/Triton II] (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:02.0 VGA compatible controller: Cirrus Logic GD 5446
00:03.0 Ethernet controller: Qumranet, Inc. Unknown device 1000

Does somebody have any suggestion on how to solve this problem ?

Josir.

[1] [http://ubuntuforums.org/showthread.php?t=1500518](http://ubuntuforums.org/showthread.php?t=1500518)
[2] [https://help.ubuntu.com/community/KVM/Networking#virtio](https://help.ubuntu.com/community/KVM/Networking#virtio)

---

### Post by josir on 2011-07-29
Solved based on [1]

sudo apt-get install kvm-pxe

[1] [https://answers.launchpad.net/ubuntu/+source/qemu-kvm/+question/110660](https://answers.launchpad.net/ubuntu/+source/qemu-kvm/+question/110660)

---

