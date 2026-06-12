---
title: "KVM doesn't start anymore after update to 10.04"
date: 2010-08-25
forum: Virtualisation
---

### Post by pred2k on 2010-08-25
After i upgraded my Server installation to 10.04, i cant start my kvm vm with virsh anymore:
```
virsh # start xpsp2
error: Failed to start domain xpsp2
error: monitor socket did not show up.: No such file or directory

```

/var/log/libvirt/qemu/xpsp2.log contains:

```
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc -enable-kvm -m 512 -smp 1 -name xpsp2 -uuid f59097a0-ceeb-61f8-2966-c2be69108c1d -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/xpsp2.monitor,server,nowait -monitor chardev:monitor -localtime -boot c -drive file=/home/user/windows.qcow2,if=ide,index=0,boot=on -net nic,macaddr=00:16:36:21:f7:c5,vlan=0,name=nic.0 -net tap,fd=35,vlan=0,name=tap.0 -serial none -parallel none -usb -usbdevice tablet -vnc 0.0.0.0:0 -vga cirrus
libvir: QEMU error : cannot change to '107' group: Operation not permitted
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc -enable-kvm -m 512 -smp 1 -name xpsp2 -uuid f59097a0-ceeb-61f8-2966-c2be69108c1d -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/xpsp2.monitor,server,nowait -monitor chardev:monitor -localtime -boot c -drive file=/home/user/windows.qcow2,if=ide,index=0,boot=on -net nic,macaddr=00:16:36:21:f7:c5,vlan=0,name=nic.0 -net tap,fd=37,vlan=0,name=tap.0 -serial none -parallel none -usb -usbdevice tablet -vnc 0.0.0.0:0 -vga cirrus
libvir: QEMU error : cannot change to '107' group: Operation not permitted
```

What could be the problem?

---

### Post by pred2k on 2010-08-29
Does nobody has an idea?

What could i test or try?

I need to get my VM running

---

### Post by starman5 on 2010-10-25
having upgraded from 8.04lts to 10.04LTS im having the same problem
also all of my vm say that they have no boot disc

---

### Post by aikidd on 2010-12-07
I resolved this by adding the text below to "/etc/libvirt/qemu.conf".  It came from "/etc/libvirt/qemu.conf.dpkg-dist"

```
# The user ID for QEMU processes run by the system instance
#user = "libvirt-qemu"
user = "root"

# The group ID for QEMU processes run by the system instance
#group = "kvm"
group = "root"
```

---

### Post by donh3 on 2010-12-08
starman5, I recently posted something that might be of help:
[http://ubuntuforums.org/showthread.php?t=1638708](http://ubuntuforums.org/showthread.php?t=1638708)

---

