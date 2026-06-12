---
title: "virt-install an XP system on 8.10"
date: 2008-11-05
forum: Virtualisation
---

### Post by NitroBooster on 2008-11-05
After reading this guide I was sure I could use virt-install to do an XP install, however, I'm getting this error:

```

admin@356835794:/$ sudo virt-install --connect qemu:///system -n xpsp2 -r 512 -f windows.qcow2 -s 8 -c /usr/src/WinXP_CD_Alexis_v1.5.iso --vnc --os-type windows --os-variant winxp
Unsupported virtualization type
admin@356835794:/$ 


```

from this original
[https://help.ubuntu.com/community/KVM#Creating%20virtual%20machines](https://help.ubuntu.com/community/KVM#Creating%20virtual%20machines)
```


sudo virt-install --connect qemu:///system -n xpsp2 -r 512 -f windows.qcow2 -s 12 -c windowsxpsp2.iso --vnc --noautoconsole --os-type windows --os-variant winxp


```

Probably messing up something simple again....

---

### Post by NitroBooster on 2008-11-05
I might as well add this:

$ qemu-img create windows.img -f qcow 8G
$ sudo chmod 777 /dev/kvm
$ kvm -no-acpi -m 384 -cdrom /dev/cdrom -boot d windows.img
$ kvm -no-acpi -m 384 -cdrom /dev/cdrom windows.img

Performing the above works, but I wanted to boot from an .iso instead of the physical drive. But it fails:

```

admin@356835794:/$ kvm -no-acpi -m 384 -cdrom /usr/src/WinXP_CD_Alexis_v1.5.iso -vnc -boot d windows.img
qemu: could not open disk image /usr/src/WinXP_CD_Alexis_v1.5.iso
admin@356835794:/$ 

```

How do I get aroung this please?

---

### Post by NitroBooster on 2008-11-05
Help People...

I started over today, and I can't even get as far as I got yesterday :(
> 
$ sudo apt-get install firestarter
$ sudo apt-get install openvpn

$ sudo apt-get install kvm libvirt-bin
$ sudo adduser $USERNAME libvirtd
$ sudo apt-get install python-virtinst
$ sudo apt-get install virt-manager
$ sudo apt-get install virt-viewer
$ sudo apt-get install qemu

sudo virt-install --connect qemu:///system -n VM1-RUS -r 512 -f windows.qcow2 -s 8 --cdrom /media/KINGSTON/WinXP_CD_Alexis_v1.5.iso --vnc --os-type windows --os-variant winxp

Gets me the "Unsupported Virtualization Type" error
> 
adminuser@0984576786:~$ sudo uname -r
[sudo] password for adminuser: 
2.6.27-7-generic
adminuser@0984576786:~$ sudo virt-install --connect qemu:///system -n VM1-RUS -r 512 -f windows.qcow2 -s 8 --cdrom /media/KINGSTON/WinXP_CD_Alexis_v1.5.iso --vnc --os-type windows --os-variant winxp
Unsupported virtualization type
adminuser@0984576786:~$ sudo virt-install --connect xen -n VM1-RUS -r 512 -f windows.qcow2 -s 8 --cdrom /media/KINGSTON/WinXP_CD_Alexis_v1.5.iso --vnc --os-type windows --os-variant winxp
Wed, 05 Nov 2008 19:04:28 ERROR    virConnectOpen() failed
Traceback (most recent call last):
  File "/usr/bin/virt-install", line 499, in <module>
    main()
  File "/usr/bin/virt-install", line 346, in main
    conn = cli.getConnection(options.connect)
  File "/usr/lib/python2.5/site-packages/virtinst/cli.py", line 92, in getConnection
    return libvirt.open(connect)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 139, in open
    if ret is None:raise libvirtError('virConnectOpen() failed')
libvirtError: virConnectOpen() failed
adminuser@0984576786:~$


So this is something strange!

Does this mean that the supported virtualization type is Xen?? and not qemu??

---

### Post by garystam on 2008-11-05
Are you using Virtual Box??

---

### Post by garystam on 2008-11-05
Try: sudo apt-get install virtualbox-ose
I installed XP on this last night and it works great.

---

### Post by NitroBooster on 2008-11-05
> **garystam said:**
> Try: sudo apt-get install virtualbox-ose
I installed XP on this last night and it works great.

I found what the problem was...

You have to use the -v flag when using virt-install, this works:

> 
sudo virt-install [COLOR="Red"]-v[/COLOR] --connect qemu:///system -n VM1-RUS -r 512 -f windows.qcow2 -s 8 --cdrom /media/KINGSTON/WinXP_CD_Alexis_v1.5.iso --vnc --os-type windows --os-variant winxp



Out of curiosity, what kind of networking/cpu options does virtual box have?
Did you follow a guide?

---

### Post by garystam on 2008-11-05
All inclusive, just need to make them active in the installation. My wireless and hard wired both recognized. It actually runs quite fast. I allocated 1G to memory.

---

### Post by NitroBooster on 2008-11-05
> **garystam said:**
> All inclusive, just need to make them active in the installation. My wireless and hard wired both recognized. It actually runs quite fast. I allocated 1G to memory.


Thank you for the tip Gary, it works very well !

I've been in misery for 2 days, glad it's over...

On to dealing with OpenVPN server problems :confused:

---

### Post by m2.g5ru6y7s on 2008-11-30
> **NitroBooster said:**
> I found what the problem was...

You have to use the -v flag when using virt-install, this works:



Many thanks for sharing this info.
It's sad nobody, noticed this.
Hope this could be mentioned in the Web page of Ubuntu, which is full of attractive and useful information of KVM in combination of Ubuntu.

---

