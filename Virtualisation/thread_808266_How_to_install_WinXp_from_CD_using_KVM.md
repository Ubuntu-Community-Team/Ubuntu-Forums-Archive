---
title: "How to install WinXp from CD using KVM"
date: 2008-05-26
forum: Virtualisation
---

### Post by jambalaya on 2008-05-26
Hi.
To begin with, I looked through a lot of material in this forum and google, but I sort of can't find anything to guide me (or I can't deal with the information I found properly, which is very possible).
I have a running 64-bit Kubuntu 8.04 installation, and I have kvm installed, along with qemu. I also have a windows xp CD in the drive, I am able to load the kvm and kvm-intel module (I have a Core 2 Duo). I created an image file:
"qemu-img create -f qcow xpsp2.img 3G" in my home directory, and I'm stuck now - I don't know what to do because all the windows xp howtos seemed to be working with *.iso images, and I have an ordinary cd. Could anyone help me find some information on how to install that correctly?
Also, the guest OS is 32-bit, will this work properly on a 64-bit host?
Thanks.

---

### Post by jambalaya on 2008-05-26
Hi.
I managed to install it at last, the line to boot from cd is (in case anyone reads that later):
sudo qemu-system-x86_64 -hda xpsp2.img -boot d -cdrom /dev/cdrom -m 512 -localtime

However, now when I start qemu, the console says:
Could not open '/dev/kqemu' - QEMU acceleration layer not activated: No such device or address

It works without it, but I read this could speed things up dramatically. I installed kqemu-common, but I don't know if this is enough. Does anyone know how to deal with this?
Thanks.

---

### Post by ericy on 2008-05-26
1. make sure you add your id to group 'kvm'
(or you if you want to do it quick, run as root for now)

2. An easy command would be:
kvm -m 512 -cdrom /dev/cdrom -hda <path to your image file>/xpsp2.img -boot d


Or just type kvm, and it'll give you a list of options.

---

### Post by jambalaya on 2008-05-26
Thank you, I didn't know I had to run it with the kvm command.
Now I don't get any error message, and the guest os boots and runs quicker, it really makes the difference.
Thanks!

---

### Post by link0315 on 2011-10-08
> **ericy said:**
> 1. make sure you add your id to group 'kvm'
(or you if you want to do it quick, run as root for now)

2. An easy command would be:
kvm -m 512 -cdrom /dev/cdrom -hda <path to your image file>/xpsp2.img -boot d


Or just type kvm, and it'll give you a list of options.

How to write the configure XML file? My XML is :
...
<os>
    <type arch='i686' machine='pc-0.11'>hvm</type>
    <boot dev='cdrom'/>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
...
But error occurs:
Error launching details: Domain not found: no domain with matching uuid '3e53142a-7243-0a12-2b8a-3946653516a0'
When I change it:
...
<os>
    <type arch='i686' machine='pc-0.11'>hvm</type>
    <boot dev='hd'/>
  </os>
...
It works!

---

### Post by matthew.mattoon on 2011-10-12
Hi link0315,

A while back I wrote an article on using XML for libvirt guest creation, which will help you understand how the XML is defined.

[http://blog.allanglesit.com/2011/03/kvm-guests-manipulating-libvirt-xml-for-guest-creation/](http://blog.allanglesit.com/2011/03/kvm-guests-manipulating-libvirt-xml-for-guest-creation/)

That said the easiest way is to take an existing XML and modify it, the original can come from another VM:
# virsh dumpxml vm1 > vm2.xml
And then be edited with vi to suit the new VMs needs before defining it.  Or you could use Virt-Manager to define the VM (which will create the XML) and then edit the VM configuration:
# virsh edit vm2

-matt

---

