---
title: "Upgrade to 10.04.3 killed my virtual hosts - HELP!"
date: 2011-10-16
forum: Virtualisation
---

### Post by Mogga on 2011-10-16
I have a virtualized fileserver (virsh/kvm/qemu) that has just started behaving very oddly after the latest apt-get update to host and virtual machine. Inbound network to the virtual machine is not working except on the host and the drive mappings  are completely wrong.


I have 3 or 4 volumes on the host machine that are mounted as so:


```
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/bardot/tools'/>
      <target dev='vdf' bus='virtio'/>
    </disk>
```

 
The data seems intact but the drives are the wrong drives entirely.

I did nothing but apt-get upgrade&#8230; PLEASE HELP!


Update&#8230; any virtual hosts I created before last night are not accessible except by console/vnc to the host. Hosts created afterwards DO work.

---

### Post by thescubadude on 2011-11-15
Did you sort this out. Running home server for development. Updated today and now none of my virtual hosts work. Using desktop version with Apache and have virtual hosts pointing to my /home/user/www folder. Everything was working 100% now if I try load any php page instead of processing the page it wants to download the page. if you fixed your issues and can offer some insight that would be awesome.

---

