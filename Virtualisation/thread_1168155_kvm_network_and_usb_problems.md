---
title: "kvm network and usb problems"
date: 2009-05-23
forum: Virtualisation
---

### Post by thegrimgod on 2009-05-23
Hi all,
I installed kvm recently and have been struggling with 2 things:
networking, and usb connections.
The first problem is the really annoying one, so I will focus on that.

Sadly, I do not really know a lot about bridging, and the howto file at:
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)
isn't really helping me understand it... just some blind steps to follow...
My problem is that I am left without an internet connection if I use my eth0 interface which has been added to the bridge br0. Here is my /etc/network/interfaces file
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

This is pretty much a copy paste from the howto that I referenced in the link above.
Now the odd part, is that after a reboot, both the host machine and the VMs have network connectivity, if the ethernet cable is plugged in. But as soon as I do an /etc/init.d/networking restart, they both lose network connectivity... or sometimes the VM has full connection, while the host has only local area network connection... so :-|
Can somebody please explain to me what I am doing wrong, and help me understand this, or help me debug this problem, in case its a bug...?
I can provide more info as needed, just ask.

The second problem is that my windows xp vm cant see the blackberry that i connect through usb. Any way i can have the vm detect those usb connections? it works fine for my mouse.

Well, thats pretty much it, Id appreciate any help.

---

### Post by yazidarezki on 2009-05-25
When you creaed the VM, did you use USER or SYSTEM. It should be be system
 
Cheers
Yaz

---

### Post by thegrimgod on 2009-05-25
Hey Yaz,
Thx for the reply. The image is on localhost(System).

In addition, I tried some more steps that I found on the net.
When I go to qemu-monitor for the win xp vm that I have, and I do:
(qemu)info usbhost
I get:
Device 5.13, speed 12 Mb/s
 Vendor Specific: USB device 0fca:0001, BlackBerry

If I then do:
(qemu)usb_add host:0fca:0001
I get:
hsub: could not open /sys/bus/usb/devices/4-2/product
and at the terminal , i get:
husb: config #1 need 1
husb: 1 interfaces claimed for configuration 1

EDIT: after sometime... by issuing the same usb_add command, it eventually added it... I have no clue what changed, but now my phone is connected yuppy

I went ahead and did the changes listed here:
[https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/331331](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/331331)
but I do not really know if they made any difference, since I started the machine with the following command:
sudo kvm -m 512 -hda /var/lib/libvirt/images/WinXPsp3work.img -usb -smp 1
which should give me root permissions.

Now if I can figure out the network stuff, and stabilize this part of the usb mayhem, I will have this working beautifully.

Cheers

---

### Post by Pnuts on 2009-05-26
I am not sure if this will help you, but I also had trouble getting the bridge to function in KVM initially. I made a post here: [http://ubuntuforums.org/showpost.php?p=7303855&postcount=2](http://ubuntuforums.org/showpost.php?p=7303855&postcount=2) that pretty much outlines what I do now, step by step, to create a new guest with a working bridge.

---

