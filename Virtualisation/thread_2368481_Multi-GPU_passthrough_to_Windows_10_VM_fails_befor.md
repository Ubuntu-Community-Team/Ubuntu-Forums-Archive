---
title: "Multi-GPU passthrough to Windows 10 VM fails before booting."
date: 2017-08-11
forum: Virtualisation
---

### Post by simen.musaeus on 2017-08-11
I've successfully set up Windows 10 VM with 3 x Nvidia 1080Ti cards passed through, using kvm, libvirt, virt-manager and vfio-pci on Ubuntu 16.04. All working fine. **If I attempt to attach more than 3 GPUs, the VM freezes before booting,** this means that I'm not even able to reach the windows boot-loader, there is brief spike on the CPU graph in virt-manager before it returns to idle.

So far:

[LIST]
[*]The Virt-Manager VM console spits out unreadable data if I boot with less than 4 GPUs, with 4 or more GPUs the console stays empty.
[*]WinDbg ([src]("https://www.linux-kvm.org/page/WindowsGuestDrivers/GuestDebugging")) does not detect a client when booting with 4 or more GPUs.
[/LIST]

It makes me think that the issue is not related to the graphics driver, and rather bound to the passing of the PCIe device. I have a Ubuntu VM working with more than 4 GPUs passed through, so I assume the problem is related to the virtualisation of Windows.

I've tried:

[LIST]
[*]Experiementing with different CPU and RAM settings, thinking that it might be related to PCIe lanes as on a physical machine, this cause some different behavior (longer boot times), but no success.
[*]Looking at the libvirt logfiles (they are close to identical booting with 3 or 4 GPUs), no warnings as far as I can see.
[/LIST]

Now I have no clue how to go about trouble-shooting this, so I though I'd ask for hints. What puzzles me is that it only works for a certain number of GPUs, yet I don't know what factors limits this.

---

### Post by heiko_s on 2017-08-23
This isn't much to go on. It might be good to learn about your hardware, and see the config file for the VM. To be honest, I much prefer the simplicity of the qemu-system... command compared to reading xml files with all the crap in them.

My first inclination is to say it's because of virt-manager. You could produce a qemu start script for your Windows VM. Here is an example:

```
#!/bin/bash

configfile=/etc/vfio-pci.cfg
vmname="win10vm"

vfiobind() {
dev="$1"
vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
device=$(cat /sys/bus/pci/devices/$dev/device)
if [ -e /sys/bus/pci/devices/$dev/driver ]; then
echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
fi
echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id

}


if ps -A | grep -q $vmname; then
zenity --info --window-icon=info --timeout=15 --text="$vmname is already running." &
exit 1
else
cat $configfile | while read line;do
echo $line | grep ^# >/dev/null 2>&1 && continue
vfiobind $line
done

export QEMU_AUDIO_DRV=alsa
export QEMU_ALSA_ADC_BUFFER_SIZE=1024 QEMU_ALSA_ADC_PERIOD_SIZE=256
export QEMU_ALSA_DAC_BUFFER_SIZE=1024 QEMU_ALSA_DAC_PERIOD_SIZE=256
export QEMU_AUDIO_DAC_FIXED_SETTINGS=1
export QEMU_AUDIO_DAC_FIXED_FREQ=44100 QEMU_AUDIO_DAC_FIXED_FMT=S16 QEMU_AUDIO_ADC_FIXED_FREQ=44100 QEMU_AUDIO_ADC_FIXED_FMT=S16
export QEMU_AUDIO_DAC_TRY_POLL=1 QEMU_AUDIO_ADC_TRY_POLL=1
export QEMU_AUDIO_TIMER_PERIOD=50

cp /usr/share/OVMF/OVMF_VARS.fd /tmp/my_vars.fd
chown qemu-vga:qemu-vga /tmp/my_vars.fd

#taskset -c 0-9
qemu-system-x86_64 \
-monitor stdio \
-serial none \
-parallel none \
-nodefaults \
-nodefconfig \
-name $vmname,process=$vmname \
-machine q35,accel=kvm,kernel_irqchip=on,mem-merge=off \
-cpu host,kvm=off,hv_vendor_id=1234567890ab,hv_vapic,hv_time,hv_relaxed,hv_spinlocks=0x1fff \
-smp 12,sockets=1,cores=6,threads=2 \
-m 20G \
-mem-path /run/hugepages/kvm \
-mem-prealloc \
-balloon none \
-rtc base=localtime,clock=host \
-vga none \
-nographic \
-soundhw hda \
-device vfio-pci,host=02:00.0,multifunction=on \
-device vfio-pci,host=02:00.1 \
-device vfio-pci,host=00:1a.0 \
-device vfio-pci,host=08:00.0 \
-drive if=pflash,format=raw,readonly,file=/usr/share/OVMF/OVMF_CODE.fd \
-drive if=pflash,format=raw,file=/tmp/my_vars.fd \
-boot order=c \
-drive id=disk0,if=virtio,cache=none,format=raw,aio=native,file=/dev/mapper/lm13-win10 \
-netdev type=tap,id=net0,ifname=vmtap0,vhost=on \
-device virtio-net-pci,netdev=net0,mac=00:16:3e:00:01:01

#EOF

exit 0
fi
```

Adjust to your needs.

---

