---
title: "virsh export vm for backups"
date: 2018-01-27
forum: Virtualisation
---

### Post by juraj-papic on 2018-01-27
hi all,


I have my sever with virsh and im running a few vms, what I would like to do is backup / export the hold vm (with all its configuration) so I can have it in a external backup.

Is that possible?

thanks.

---

### Post by KillerKelvUK on 2018-01-27
Home users answer to this...

[LIST]
[*]Shutdown the running vm
[*]virsh dumpxml *guest-name *> guest-name.xml
[*]cp *guest-img-file.xxx /path/to/external/storage*
[/LIST]
Clearly if this is a production server a shutdown might not be feasible.  However with the above you can use virsh to define a new guest using the xml file (virsh define guest-name.xml), all that would then be needed is to edit the guest config so that the disk arguments point to the guest-img-file you have stored elsewhere.

---

### Post by juraj-papic on 2018-01-27
hello,


but what will happend with the internal configuration of the vm?  what I need is to save that config also.


thanks.

---

### Post by KillerKelvUK on 2018-01-27
That's what is contained in the xml file.  You can execute 'virsh dumpxml' on a running guest without issue and it will output the configuration for the vm so you can see this for yourself.

---

### Post by juraj-papic on 2018-01-27
thanks i will test it

---

### Post by mwray on 2018-10-13
Um...I have tried this virsh tool, and it basically ignores a vm I have running (qemu). I'm trying to import one that currently launches from a script that is using video and usb passthrough. The vm is running Windows 10 Pro. I can use the vm all day. How do I import it into virt-manager? I have seen virsh domxml-from-native, but that doesn't work as my vm is not already in virtmanager. Nor is it available in "aqemu". I didn't know it was going to be such a pain to get it into a graphical manager later.... Host is ubuntu based on xenial. 

Command line is: 
```
qemu-system-x86_64 -name windows10vm,process=windows10vm -machine type=q35,accel=kvm -cpu host,kvm=off -smp 4,sockets=1,cores=2,threads=2 -m 12G -mem-path /run/hugepages/kvm -mem-prealloc -balloon none -rtc clock=host,base=localtime -vga none -nographic -serial none -parallel none -soundhw hda -device vfio-pci,host=04:00.0,multifunction=on -device vfio-pci,host=04:00.1 -drive if=pflash,format=raw,readonly,file=/usr/share/OVMF/OVMF_CODE.fd -drive if=pflash,format=raw,file=/tmp/my_vars.fd -boot order=c -drive id=disk0,if=virtio,cache=none,format=raw,file=/vm2/win.img -netdev type=tap,id=net0,ifname=vmtap0,vhost=on -device virtio-net-pci,netdev=net0,mac=00:16:3e:00:01:01
```


Bash file is:
```
#!/bin/bash

vmname="windows10vm"

if ps -A | grep -q $vmname; then
echo "$vmname is already running." &
exit 1

else

# use pulseaudio
#export QEMU_AUDIO_DRV=pa
#export QEMU_PA_SAMPLES=8192
#export QEMU_AUDIO_TIMER_PERIOD=99
#export QEMU_PA_SERVER=/run/user/1000/pulse/native
#
export QEMU_AUDIO_DRV=pa
export QEMU_PA_SAMPLES=1024
export QEMU_AUDIO_TIMER_PERIOD=150
export QEMU_PA_SERVER=/run/user/1000/pulse/native

cp /usr/share/OVMF/OVMF_VARS.fd /tmp/my_vars.fd

qemu-system-x86_64 \
-name $vmname,process=$vmname \
-machine type=q35,accel=kvm \
-cpu host,kvm=off \
-smp 4,sockets=1,cores=2,threads=2 \
-m 12G \
-mem-path /run/hugepages/kvm \
-mem-prealloc \
-balloon none \
-rtc clock=host,base=localtime \
-vga none \
-nographic \
-serial none \
-parallel none \
-soundhw hda \
-device vfio-pci,host=04:00.0,multifunction=on \
-device vfio-pci,host=04:00.1 \
-drive if=pflash,format=raw,readonly,file=/usr/share/OVMF/OVMF_CODE.fd \
-drive if=pflash,format=raw,file=/tmp/my_vars.fd \
-boot order=c \
-drive id=disk0,if=virtio,cache=none,format=raw,file=/vm2/win.img \
-netdev type=tap,id=net0,ifname=vmtap0,vhost=on \
-device virtio-net-pci,netdev=net0,mac=00:16:3e:00:01:01

exit 0
fi

#-drive file=/vm2/ISOs/Win10.iso,index=1,media=cdrom \
#-drive file=/vm2/ISOs/virtio-win.iso,index=2,media=cdrom \
#-usb -usbdevice host:046d:c05a -usbdevice host:046d:c31c \
```

This post looks relevant to what I am looking for, but may not be, apolgies if not. I have been digging on this for weeks, and so far the only thing I came up with that looked close was this thread, and a thread on Red-Hat about virsh and domxml-from-native. [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-domain_commands-converting_qemu_arguments_to_domain_xml](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-domain_commands-converting_qemu_arguments_to_domain_xml) which didn't work, as virsh doesn't know about my vm.

---

