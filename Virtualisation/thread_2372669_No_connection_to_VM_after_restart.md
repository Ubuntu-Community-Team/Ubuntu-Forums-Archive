---
title: "No connection to VM after restart"
date: 2017-09-27
forum: Virtualisation
---

### Post by majestixx2 on 2017-09-27
Recently I moved to a new flat and powered down my virtualized system for the first time in a while.
The host was restarting with out any problems and also the client seem to start, but I am not able to connect via ssh or directly to the vm.

Host and clients are both running on Ubuntu 16.04.3.

Starting works:
```
root@serv1:/# virsh create /etc/libvirt/qemu/serv1vm1.xml
Domain serv1vm1 von /etc/libvirt/qemu/serv1vm1.xml erstellt
```

```
root@serv1:/# virsh list
 Id    Name                           Status
----------------------------------------------------
 2     serv1vm1                       running
```

The log also looks good:
```
root@serv1:/# cat /var/log/libvirt/qemu/serv1vm1.log
2017-09-27 20:38:28.878+0000: starting up libvirt version: 1.3.1, package:                  1ubuntu10.14 (Jorge Niedbalski <jorge.niedbalski@canonical.com> Thu, 10 A                 ug 2017 22:50:46 -0400), qemu version: 2.5.0 (Debian 1:2.5+dfsg-5ubuntu10.                 16), hostname: serv1
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin                  QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name serv1vm1 -S -machine pc-i440                 fx-wily,accel=kvm,usb=off -cpu Westmere -m 2048 -realtime mlock=off -smp 4                 ,sockets=4,cores=1,threads=1 -uuid e328ec29-98dd-4955-892e-28ff788ede55 -n                 o-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/lib                 virt/qemu/domain-serv1vm1/monitor.sock,server,nowait -mon chardev=charmoni                 tor,id=monitor,mode=control -rtc base=utc,driftfix=slew -global kvm-pit.lo                 st_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1                  -global PIIX4_PM.disable_s4=1 -boot strict=on -device ich9-usb-ehci1,id=u                 sb,bus=pci.0,addr=0x6.0x7 -device ich9-usb-uhci1,masterbus=usb.0,firstport                 =0,bus=pci.0,multifunction=on,addr=0x6 -device ich9-usb-uhci2,masterbus=us                 b.0,firstport=2,bus=pci.0,addr=0x6.0x1 -device ich9-usb-uhci3,masterbus=us                 b.0,firstport=4,bus=pci.0,addr=0x6.0x2 -device virtio-serial-pci,id=virtio                 -serial0,bus=pci.0,addr=0x5 -drive file=/var/lib/libvirt/images/serv1vm1.q                 cow2,format=qcow2,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scs                 i=off,bus=pci.0,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootinde                 x=1 -drive if=none,id=drive-ide0-0-0,readonly=on -device ide-cd,bus=ide.0,                 unit=0,drive=drive-ide0-0-0,id=ide0-0-0 -netdev tap,fd=26,id=hostnet0,vhos                 t=on,vhostfd=28 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:0                 0:f7:50:53,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-seri                 al,chardev=charserial0,id=serial0 -chardev spicevmc,id=charchannel0,name=v                 dagent -device virtserialport,bus=virtio-serial0.0,nr=1,chardev=charchanne                 l0,id=channel0,name=com.redhat.spice.0 -vnc 127.0.0.1:0 -device qxl-vga,id                 =video0,ram_size=67108864,vram_size=67108864,vgamem_mb=16,bus=pci.0,addr=0                 x2 -device intel-hda,id=sound0,bus=pci.0,addr=0x4 -device hda-duplex,id=so                 und0-codec0,bus=sound0.0,cad=0 -chardev spicevmc,id=charredir0,name=usbred                 ir -device usb-redir,chardev=charredir0,id=redir0 -chardev spicevmc,id=cha                 rredir1,name=usbredir -device usb-redir,chardev=charredir1,id=redir1 -devi                 ce virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8 -msg timestamp=on
char device redirected to /dev/pts/4 (label charserial0)

```

However the machine is not respoding if I try to connect via ssh:
```
root@serv1:/# ssh serv1vm1
ssh: Could not resolve hostname serv1vm1: Name or service not known
```

And it dies when connecting to the console: (I cannot type anything or abort the console)
```
root@serv1:/# virsh console serv1vm1
Verbunden mit der Domain: serv1vm1
Escape-Zeichen ist ^]

```

Virt-top looks good to me:
```
virt-top 23:00:01 - x86_64 4/4CPU 2030MHz 7781MB 0,7%
1 domains, 1 active, 1 running, 0 sleeping, 0 paused, 0 inactive D:0 O:0 X:0
CPU: 0,8%  Mem: 2048 MB (2048 MB by guests)

   ID S RDRQ WRRQ RXBY TXBY %CPU %MEM    TIME   NAME
    2 R              0    0  0,8 26,0   0:30.71 serv1vm1
```


The configuration XML of my vm:
```
root@serv1:/home/server# cat /etc/libvirt/qemu/serv1vm1.xml
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit serv1vm1
or other application using the libvirt API.
-->

<domain type='kvm'>
  <name>serv1vm1</name>
  <uuid>e328ec29-98dd-4955-892e-28ff788ede55</uuid>
  <memory unit='KiB'>2097152</memory>
  <currentMemory unit='KiB'>2097152</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-wily'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Westmere</model>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/serv1vm1.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hda' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:f7:50:53'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```


And also the network configuration seems to be good:
```
server@serv1:/etc/libvirt/qemu$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

## The primary network interface
#auto enp3s0
#iface enp3s0 inet dhcp
## This is an autoconfigured IPv6 interface
#iface enp3s0 inet6 auto


# dhcp bridge configuration
auto br0
iface br0 inet dhcp
        bridge_ports enp3s0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0


## Manual IP bridge configuration
#auto enp3s0
#iface enp3s0 inet manual
```

So I have no clue why I am not able to connect to the vm anymore.
Do you have any ideas?

---

### Post by HermanAB on 2017-09-28
"Could not resolve hostname serv1vm1"
It looks like your IP addresses changed and your DNS isn't working right.

---

### Post by majestixx2 on 2017-09-28
My bridge is configured to run with dhcp.
All my other devices and also the host are receiving their ip so the dhcp server in my router should be working normally (I also did not change any configuration of my router).

The DNS resolving should also work using the default configuration of my router.

I did some searching for the vm in the network using "arp -n". Also without success.

---

