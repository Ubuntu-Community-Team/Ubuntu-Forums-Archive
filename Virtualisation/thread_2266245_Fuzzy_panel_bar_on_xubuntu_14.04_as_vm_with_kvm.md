---
title: "Fuzzy panel bar on xubuntu 14.04 as vm with kvm"
date: 2015-02-21
forum: Virtualisation
---

### Post by quiquednst on 2015-02-21
For years I use to work with **kvm** building several virtual machines without any problem.

 Since September I do that with xubuntu 14.04 as host and xubuntu 12.04, 10.04, other ubuntus, xp or w7 as virtual machines.
 Now I tried to build a xubuntu 14.04 vm and I got a problem related with graphics.
 I get a very fuzzy panel bar. However almost any application opens a nice window excluding Terminal emulator which opens a transparent window, useless at all.

 The problem disappears using either **-vga qxl** or **-vga vmware**, but it fails using **-vnc**, **-sdl**, **-vga cirrus** or **-vga std**.

 At least for me the problem is the -vnc failure.
 I attach an image of the strange desktop.
 Is there anything I can do to avoid this problem using vnc?
Thanks in advance for your help

---

### Post by Doug S on 2015-02-21
I have always been able to get rid of the problem by changing this:```
    <video>
      <model type='[COLOR=#ff0000]cirrus[/COLOR]' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
```To this:```
    <video>
      <model type='[COLOR=#ff0000]vmvga[/COLOR]' vram='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
```Using "virsh edit"
Note: the vram size doesn't matter, it actually has no effect.
Or if I am making a new VM something like:```
sudo virt-install -n desk_tt2 -r 8192 --disk path=/home/doug/img/desk_tt2.img,bus=virtio,size=50 -c trusty-desktop-amd64-20140318.iso --network bridge=br0,model=virtio [COLOR=#ff0000]--video=vmvga[/COLOR] --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4 
```There is another thread on this subject in this sub-fourm somewhere, but I didn't find it yet

Edit: [found it]("http://ubuntuforums.org/showthread.php?t=2223520").

---

### Post by quiquednst on 2015-02-22
Thanks, Doug, for your fast answer.
As far as I understand it's a problem related with the 'cirrus' driver I'm trying to avoid it in another way.
In fact I'm using the 'kvm' command directly. So, now it works using this command:
*kvm -m 512 -hda /media/myvm.qcow2 -usb -vga qxl -vnc 127.0.0.1:1 -k es -soundhw es1370*
Thanks for your help

---

