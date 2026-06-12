---
title: "KVM host bombed, virt-df confusing me, qcow2 space issue?"
date: 2019-01-06
forum: Virtualisation
---

### Post by trendal.toews on 2019-01-06
I've got a KVM host that spiraled out of control.  I'm trying to salvage it and in the process maybe figure out what went wrong.

I'll try to describe the setup as brief as I can.

Hardware:
Dell Poweredge T 110
2 HDD's in Raid 1 (sda, sdb) <-- These will be ignored as they were just for storage, sdb is currently bad, breaking the array
2 SSD's in Raid 1  (sdc, sdd) <-- Host OS and Guests

Software:
LVM on top of Raid
KVM host
Ubuntu VM guests
    In the beginning I had 3 raw guests and 1 qcow2 guest VM.  2 of the raw vm's were not being used so I removed them.  There may still be traces of them around.

I used Logical Volumes for each guest, including 1 for the qcow2 image file.  As of now the 1 raw image is a file server running Samba and it's working fine.  The qcow2 image is running a custom business web application.  (I brought it over from an old KVM setup)

The qcow2 guest went into a paused state while I was on vacation.  I fiddled with it a bit remotely and couldn't get it to respond and all so I rebooted the host.  Stupid mistake while remote.  The host crashed.  Came up reporting Duplicat MD devices in raid config.  After I got on site, I found the bios had somehow been borked.  Only one SATA port was enabled.  After working through that I found the bad drive in the storage array.  I got the system booting and figured I was back running.  Then the web app vm went into paused state again.  I found if I destroyed it I could start it again and it would run for a random amount of time, sometimes minutes, sometimes hours.  I don't remember what gave me the idea but I got to wondering if there was a drive space issue.  The qcow2 is 100 Gigs but it's only on a 20 Gig lvm.  So I discovered virt-df.  But I can't make sense of it's output.  It does show those partitions as being 100% full but the output seems wrong.

Here is the lsblk output
```
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 931.5G  0 disk  
`-md132                           9:132  0 931.4G  0 raid1 
  `-vg_on_hdd-geoffs_pc_backup  252:4    0   500G  0 lvm   /shares/geoffs_pc_backup
sdb                               8:16   0 931.5G  0 disk  
sdc                               8:32   0 111.8G  0 disk  
|-sdc1                            8:33   0     1K  0 part  
|-sdc2                            8:34   0   953M  0 part  /boot
|-sdc5                            8:37   0   953M  0 part  
| `-md129                         9:129  0 952.4M  0 raid1 [SWAP]
|-sdc6                            8:38   0  16.8G  0 part  
| `-md130                         9:130  0  16.8G  0 raid1 /
`-sdc7                            8:39   0  93.2G  0 part  
  `-md131                         9:131  0  93.1G  0 raid1 
    |-vg_on_ssd-local.ghnut.com 252:0    0    40G  0 lvm   /mnt/local.ghnut.com
    `-vg_on_ssd-fileserver      252:1    0    50G  0 lvm   
sdd                               8:48   0 111.8G  0 disk  
|-sdd1                            8:49   0   953M  0 part  
|-sdd2                            8:50   0     1K  0 part  
|-sdd5                            8:53   0   953M  0 part  
| `-md129                         9:129  0 952.4M  0 raid1 [SWAP]
|-sdd6                            8:54   0  16.8G  0 part  
| `-md130                         9:130  0  16.8G  0 raid1 /
`-sdd7                            8:55   0  93.2G  0 part  
  `-md131                         9:131  0  93.1G  0 raid1 
    |-vg_on_ssd-local.ghnut.com 252:0    0    40G  0 lvm   /mnt/local.ghnut.com
    `-vg_on_ssd-fileserver      252:1    0    50G  0 lvm  
```

Here is the virt-df output
```
Filesystem                           1K-blocks       Used  Available  Use%
ghmf-fileserver:/dev/sda1             50442940   34749636   13107912   69%
local.ghnut.com:/dev/sda1             96887516    6702892   85239984    7%
local.ghnut.com:/dev/sdb1               848896     848896          0  100%
local.ghnut.com:/dev/sdb2                 2410       2390         20  100%

```

Here the virsh dumpxml local.ghnut.com output
```
<domain type='kvm'>
  <name>local.ghnut.com</name>
  <uuid>007b040e-471b-4fab-8e7d-126b7d9c3907</uuid>
  <title>local.ghnut.com</title>
  <description>2017 upgrade to SSD&apos;s on host
Running TimeClock and Huller App</description>
  <memory unit='KiB'>5120000</memory>
  <currentMemory unit='KiB'>5120000</currentMemory>
  <vcpu placement='static'>6</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <boot dev='hd'/>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>SandyBridge</model>
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
      <source file='/var/lib/libvirt/images/ubuntu16.04.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/ubuntu-16.04.2-server-amd64.iso'/>
      <target dev='hda' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </controller>
    <interface type='direct'>
      <mac address='52:54:00:59:20:c4'/>
      <source dev='br0' mode='bridge'/>
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
    <graphics type='vnc' port='-1' autoport='yes' listen='0.0.0.0'>
      <listen type='address' address='0.0.0.0'/>
    </graphics>
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
  <seclabel type='dynamic' model='apparmor' relabel='yes'/>
</domain>

```

The core problem at this point is why does the qcow2 based guest keep going into paused state?  I can't figure out where to look at logs to find that.

Appreciate any pointers here, thank  you.

---

### Post by trendal.toews on 2019-01-07
I think I managed it.

Using this tutorial [https://albertomolina.wordpress.com/2016/12/02/shrinking-qcow2-images/]("https://albertomolina.wordpress.com/2016/12/02/shrinking-qcow2-images/") I was able to convert the qcow2 to raw, resize it, and then I just left it as raw because that is what I wanted anyway.  I believe but am not able to confirm that the reason the qcow2 image was going to paused state is because of a space issue.  But I'm not sure exactly where. 

Time will tell if it's fixed but it's been running for a couple hours now.

---

### Post by trendal.toews on 2019-01-07
I ran badblocks on the "bad" drive and it reported zero errors.  So I went ahead and added it back to the array.

But I'm still puzzled about the virt-df output.  After all the shuffling around, resizing and converting from qcow2 to raw it still shows roughly the same thing.

Running virt-df local.ghnut.com outputs this:
```
Filesystem                           1K-blocks       Used  Available  Use%
local.ghnut.com:/dev/sda1             35993216    6677192   27464632   19%
local.ghnut.com:/dev/sdb1               848896     848896          0  100%
local.ghnut.com:/dev/sdb2                 2410       2390         20  100%
```

I can't figure out what devices that relates to.  I'm assuming by the fact that there is 3 partitions and by their sizes that it is the typical boot, swap, and filesystem partitions.  But is it the hardware on the KVM host?  Inside the guest there is just /dev/vda1 and /dev/vda2.  I don't like just ignoring things I don't understand, for sure when it says it's 100% used.

---

