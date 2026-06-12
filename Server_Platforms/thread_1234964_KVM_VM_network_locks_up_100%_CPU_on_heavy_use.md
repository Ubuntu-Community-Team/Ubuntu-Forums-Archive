---
title: "KVM VM network locks up 100% CPU on heavy use"
date: 2009-08-08
forum: Server Platforms
---

### Post by pootle1 on 2009-08-08
Bit of an ubuntu noob (but running on my laptop for a couple of months now). I'm trying to convert all my windoze based stuff to Linux :)

I have an ubuntu box (with AMD CPU, basically setup as myth server) and am running an ubuntu server VM under KVM on it. (both are Jaunty)

The physical box is fine and I have copied large amounts of data in and out (100's Gb) with no trouble.

With the VM though when I try and copy in a large load of files (photos and MP3s mainly), it hangs with the CPU running at 100% (or 50% with 2 CPUs) at some random point most recently at 20Gb into 50Gb of data(many, many files).  I have changed the vm to use virtio (well rebuilt from scratch as it is easy to do) which hasn't fixed the problem.  I wanted to check if the NIC in the VM was the right thing, but lspci doesn't exist (!).  I think its a network problem rather than something else, but only 'cos I see there have been similar looking issues (supposed to be resolved by using virtio)

I did notice part way through that the CPU utilisation went up to 50%, while the data thoughput (both disk and network ) dropped right off, than after a few minutes it recovered and carried on as normal (normal is about 6Mbytes / second and 20 - 25% CPU as reported by Virtual machine manager

Where do I go from here???

here's the vmbuilder command:
```
vmbuilder kvm ubuntu --suite jaunty --flavour virtual --arch i386 --hostname=new1 --cpus=2 -m 512 --tmpfs - \
         -o --libvirt qemu:///system --part vmbuilder.partition --mirror http://192.168.x.y:3142/ubuntu \
         --security-mirror=http://192.168.x.y:3142/ubuntu --bridge=br0 --addpkg nano \
         --addpkg acpid --domain local --firstboot boot.sh --user iain --name iain --pass password
```and my template file is:
```
<domain type='kvm'>
  <name>$hostname</name>
  <memory>#echo $mem * 1024 #</memory>
  <vcpu>$cpus</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
#if $bridge
    <interface type='bridge'>
      <source bridge='$bridge'/>
      <model type='virtio'/>
#else
    <interface type='network'>
#if $mac
      <mac address='$mac'/>
#end if
      <source network='default'/>
#end if
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
#for $disk in $disks
    <disk type='file' device='disk'>
      <source file='$disk.filename' />
      <target dev='hd$disk.devletters()' />
    </disk>
#end for
  </devices>
</domain>
```

---

### Post by PlaHPoy on 2010-02-11
I am having the same issue on both CPU load and network load. Any suggestions?

---

### Post by mrVince on 2010-03-31
Same for me. KVM hangs with 100% cpu usage on the host machine. System config:
host Ubuntu 9.10 server
guest Debian Lenny

---

### Post by PlaHPoy on 2010-03-31
I fixed it by setting the network type to virtio in the xml config file.  I found a reference to it in the docs, but at the time was using Enamolism2 which didn't allow me to set it.

---

### Post by brianm66 on 2010-09-27
Sorry to dig up an old thread here, but I've had this issue for quite some time and thought I'd go ahead and post my solution.

To fix this issue, edit /etc/default/grub and add clock=pmtmr to the GRUB_CMDLINE_LINUX_DEFAULT= line like this:

/etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clock=pmtmr"
```

Then run

```
sudo update-grub2
```

and reboot

My network interfaces were already set to virtio and I continued to have lockups. After changing the default timer in the bootloader config I haven't had a lockup for a few months.

---

