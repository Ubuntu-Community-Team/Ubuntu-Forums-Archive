---
title: "Nvidia error 43 using kvm and virt-manager"
date: 2015-11-21
forum: Virtualisation
---

### Post by lance12 on 2015-11-21
So I have been at this kvm pci passthrough thing for like 2 weeks now. I've been able to pass a radeon r9 270x and it worked perfectly fine. I was able to play games at max quality and had no issues using windows 7 64 bit. but now i'm trying to pass through an nvidia card and i've tried everything. i've tried the kvm=off. and all kinds of other options to get it working but no luck. if I use the current nvidia drivers i get a BSOD saying system service exception. can some one please help me. I'm not sure what i'm missing. 

I am using debian testing with qemu-kvm and virt-manager. the card i'm trying to pass through is a gtx 970. any help would be much appreciated.

---

### Post by T.J. on 2015-11-21
Firstly, I must stress that you cannot expect stable behavior from Debian Testing.  That said, I have used it many times with reasonable results, but stability varies wildly depending on the last update.


Using Virt-Manager/Libvirt in combination with SeaBIOS causes the Nvidia drivers to system exception. It's quite the pickle and I have not traced down the exact cause yet.  I suspect Libvirt, but to be honest I cannot be sure. The fact that Nvidia has their drivers disable themselves if KVM is detected is not helpful, either.  Feel welcome to blame Nvidia for that part of the problem.   Yes, they know about it.  Whether it was deliberate is a matter of question, but they have not fixed it. 

Realistically, at present, I know of two options (someone else might know more).  The first is if you must use Virt-manager/Libvirt, you can try using Tianocore/OVMF instead of SeaBIOS.  You can install it in Debian Testing with the ovmf package  It seems to work better with Libvirt and Nvidia.  I've had mixed results with it.  Everything works, but some DirectX games do not seem to initialize right.  It is quite possible I might be missing something in my Windows install.   I've yet to debug it completely.  My time is not as available as it once was.  

The second option (and the best IMHO) that always works is to dispense with Libvirt and Virt-manager entirely, and use a native KVM.  In my experience, while virt-manager and libvirt have much to recommend them, they are both somewhat buggy and do not have complete support for all the options of KVM/Qemu. Virt-manager and Libvirt are nothing more than a wrapper anyway.  Virt-manager just slaps an interface on top of Qemu/KVM.

Below you will find an example using SeaBIOS (with a few personal bits removed) of a native KVM (ala Qemu) setup that you can use.  I've used it on Debian 8, and Debian Testing, and it works.  Be sure to bind your card to VFIO before trying to use it. (Yes, I know, I am using qemu instead of qemu-kvm, but qemu-kvm is little more than a wrapper that uses the -enable-kvm switch.)

If you need more information, please let me know.


/usr/bin/qemu-system-x86_64 -enable-kvm -m 8192 -cpu host,kvm=off \
-smp 3,sockets=1,cores=3,threads=1 \
-machine q35,accel=kvm \
-device qxl \
-usb \
-device usb-mouse \
-device usb-kbd \
-soundhw hda \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=04:00.1,bus=root.1,addr=00.1 \
-device virtio-blk-pci,scsi=off,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=0 \
-device virtio-blk-pci,scsi=off,addr=0x8,drive=drive-virtio-disk1,id=virtio-disk1 \
-drive file=/home/VM/Games.img,if=none,id=drive-virtio-disk1,format=raw,media=disk \
-drive file=/home/VM/DevMach.qcow2,if=none,id=drive-virtio-disk0,format=qcow2,media=disk \
-netdev tap,id=user.0 \
-device virtio-net-pci,netdev=user.0 \
-boot order=c \
-drive file=/home/persona/Documents/Archives/HomeBusinessRetail.iso,id=isocd2 \
-device ide-cd,bus=ide.1,drive=isocd2 \
-rtc base=localtime,driftfix=slew"

---

### Post by lance12 on 2015-11-22
Thanks for your advice, I'm currently swamped in homework but I will diffidently try the OVMF thing tonight. I was looking into that anyways. If I have no luck with that then I will try out regular kvm, which is probably what I should be using anyways. thank you so much for your help. I'll update you if there is any progress.

---

### Post by T.J. on 2015-11-23
No problem.  I totally understand being swamped.  

When you have time, just let me know.  If need be, I'll be happy to walk you through the process of getting it setup.  I am using a Nvidia 960 for passthrough successfully on a native KVM every day.  While I would like to have gotten a Virt-manager setup to passthrough with OVMF, I have yet to see it be 100% reliable.  I think it is somewhere in libvirt's control over qemu - that is /etc/libvirt/qemu.conf.  If I find a solution, I'll post it, but it may be some time before I do.

---

### Post by lance12 on 2015-11-23
ok, so I was messing around using just kvm and I have quite a few questions. I'll start by posting my qemu script.

 echo "Starting VM"
sudo \
    qemu-system-x86_64 \
-machine pc-i440fx-2.3
-monitor stdio \
-smp 4 \
-cpu host,kvm=off \
-soundhw pcspk \
-vga qxl \
-enable-kvm \
-m 4069 \
-no-fd-bootchk \
-no-acpi \
-S \
-boot d \
-cdrom /home/lance/Documents/windows_i.iso \
-hda /var/lib/libvirt/images/win7.qcow2 \
-net nic \
-usb  \
-usbdevice mouse \
-usbdevice keyboard \
-name "win7"

so looking at that is there anything that I did wrong. if the whole thing looks wrong then I'm going to need help going through it all. but so far it doesn't seem to be broken except for the part where I can't get it to boot from my windows_l.iso (windows install iso).  it gives me "boot failed: could not read from cdrom (code 0003)". do you have any idea what could be causing this?

thanks in advance, and thank you for all of your help so far.

Edit: 
just kidding, apparently there is quit a bit more broken. I'm getting an error when starting my script. the error is "(process:2504): GLib-WARNING **: /build/glib2.0-ocmJ1Y/glib2.0-2.46.2/./glib/gmem.c:482: custom memory allocation vtable not supported". so that's probably not good.

---

### Post by T.J. on 2015-11-23
I'd imagine that you will have **many** questions, and since this is a complex topic that is very dependent on your hardware setup, that is your particular motherboard, BIOS, etc. I must ask you,** please **be patient, and I will do my very best.  It may take some time to puzzle out because forums can be a slow method, but I believe that we can get it working for you and I would be very pleased to help you do it.  Please understand that I am offering suggestions only.  I hardly know everything. We will have to discover this together.


> &#8220;so looking at that is there anything that I did wrong. if the whole thing looks wrong then I'm going to need help going through it all. but so far it doesn't seem to be broken except for the part where I can't get it to boot from my windows_l.iso (windows install iso). it gives me "boot failed: could not read from cdrom (code 0003)". do you have any idea what could be causing this?&#8221;

I've noticed that too!  I personally have a BD drive and I have seen the -cdrom option act a little odd. Until I take the time to test compile Qemu myself rather than use the default Debian version, my workaround has been to copy the disc into an ISO file and then connect it as an IDE CD-ROM:

-drive file=/home/pers/Documents/Archives/w7.iso,id=isocd2 \
-device ide-cd,bus=ide.1,drive=isocd2 \
-boot order=d \

If you have any questions as to what it means or how to use it, please ask.

> &#8220;apparently there is quit a bit more broken. I'm getting an error when starting my script. the error is "(process:2504): GLib-WARNING **: /build/glib2.0-ocmJ1Y/glib2.0-2.46.2/./glib/gmem.c:482: custom memory allocation vtable not supported". so that's probably not good.&#8221;

I've seen that as well. Glib is a GTK/Gnome library, so it is not necessarily a flaw in Qemu's functionality, but the way it interacts with Gnome.   It has reportedly been fixed upstream in Qemu, but I would drop the &#8220;monitor stdio&#8221; and see if that makes a difference.

As a safeguard, I would limit the -machine setting to "pc-i440fx-2.1" instead of "pc-i440fx-2.3", so that if you decide to use Debian Stable instead of Testing, you can move the image easily without having to backport Qemu from Debian Testing or reauthorizing Windows authentication.  Debian Stable only supports up to -machine pc-i440fx-2.1 out of the box.

---

### Post by lance12 on 2015-11-23
so here is my changed set up

#!/bin/bash


echo "Starting VM"

sudo /usr/bin/qemu-system-x86_64 \
-machine pc-i440fx-2.1 \
-smp 4 \
-cpu host,kvm=off \
-soundhw pcspk \
-vga qxl \
-enable-kvm \
-m 4069 \
-no-fd-bootchk \
-no-acpi \
-drive file=/home/lance/Documents/windows_i.iso,format=raw,id=isocd2 \
-device ide-cd,bus=ide.1,drive=isocd2 \
-boot order=d \
-hda /var/lib/libvirt/images/win7.qcow2 \
-net nic \
-usb  \
-usbdevice mouse \
-usbdevice keyboard \
-name "win7" \

I get an error starting it " qemu-system-x86_64: -hda /var/lib/libvirt/images/win7.qcow2: drive with bus=0, unit=0 (index=0) exists". how do I fix this. so far its not giving me any other errors besides the glib error.

---

### Post by lance12 on 2015-11-23
ok, so I fixed the errors that I was getting by copying some of your script. I'm currently installing windows so when thats done I'll try the pci passthrough. 

Thanks so much for your help so far :)

---

### Post by lance12 on 2015-11-24
quick question, how do I get the networking to work? I get "W: /etc/qemu-ifup: no bridge for guest interface found" when starting up the vm.

---

### Post by lance12 on 2015-11-24
got the drivers working and the usb devices working properly, I just need to figure out the network.

---

### Post by T.J. on 2015-11-25
Awesome-sauce!  Sorry for the late response.  (I've had to work on Windows COM code the last couple of days and my brain is thoroughly fried.  Microsoft has to do everything ass-backward, even C++.)

Are you using Network-manager? I use a tap device, with a manual bridge.  As far as I am aware, it should work on Debian Stable and Testing.  I recommend that you install the bridge-utils package even if you aren't planning on using a bridge specifically. It saves trouble later.

-netdev tap,id=user.0 \
-device virtio-net-pci,netdev=user.0 \

/etc/network/interfaces

auto lo br0
iface lo inet loopback
iface br0 inet dhcp
 bridge_ports eth0

---

### Post by lance12 on 2015-11-29
So if I where using the gui network-manager how would I achieve your network set up with tap? And I have a problem pretty sure its just some setting i have to change, but every game that I run works amazing except for rome total war 2. I was wondering if you have had any problems running any games specifically. 

I would also like to say thank you for all of your help. prior to your help I was bashing my head on my keyboard for like 3 weeks trying to get this to work. so thank you so much.

---

### Post by T.J. on 2015-11-30
> **lance12 said:**
> So if I where using the gui network-manager how would I achieve your network set up with tap? 

That would depend on what desktop environment you are using.  Please let me know, and I'll walk you through the steps.


> And I have a problem pretty sure its just some setting i have to change, but every game that I run works amazing except for rome total war 2. I was wondering if you have had any problems running any games specifically.

When using virt-manager, yes - I have had problems related to hardware access.  Using a native KVM, everything has worked flawlessly so far. I have not tested Rome Total War 2.  Let me know what you are experiencing.  Sometimes DirectX is just plain glitchy and it has nothing to do with the VM.

> I would also like to say thank you for all of your help. prior to your help I was bashing my head on my keyboard for like 3 weeks trying to get this to work. so thank you so much.

No need, but you are very welcome.  I'd like to think that all the time I spent getting it working was not wasted. The payoff is being able to help you and others.

---

### Post by lance12 on 2015-12-08
Thanks for your help, I got the network problem figured out :) it looks like the Rome total war game just has some really bad issues not related to the vm. 

So I think that I'm all set, from here its just messing with settings. Thanks so much and I appreciate all that you did for me and all that you do for the forums. I'll mark this as solved, and I hope that this helps others. 

In conclusion just use native kvm over virt-manager. kvm should have everything that you need :D

---

### Post by T.J. on 2015-12-13
It's been my pleasure, Lance. I hope it works well for you.  If you ever need anything or just want to say "hello," please feel welcome to PM me, here.

As a last offering, I found this.  Some of the optimizations may be of interest to you: [http://nipsy.bitgnome.net/blog/2015/07/15/QEMU,%20KVM,%20and%20GPU%20passthrough%20on%20Debian%20testing/](http://nipsy.bitgnome.net/blog/2015/07/15/QEMU,%20KVM,%20and%20GPU%20passthrough%20on%20Debian%20testing/)

Do take care, and I hope to see you around the forums!

---

