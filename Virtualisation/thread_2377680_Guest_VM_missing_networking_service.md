---
title: "Guest VM missing networking service"
date: 2017-11-15
forum: Virtualisation
---

### Post by fosol on 2017-11-15
I've setup an ubuntu server KVM host.  I've installed a guest ubuntu VM.  I can VNC and SSH into the guest VM through the dynamic IP.  I've  been trying to configure a static IP, however the guest VM does not have a networking service.

The host server has a bridge setup 'br0' which is a static IP on 'eno1' nic device.   

I can edit the /etc/network/interfaces on the guest VM, but it doesn't seem to be used by the OS.

```
# sudo /etc/init.d/networking restart
bash: /etc/init.d/networking: No such file or directory
```

The guest VM has internet access and everything works.  I simply cannot configure a static IP.  All searches on the internet tell me to configure it like a normal server, but it simply doesn't appear to be possible.

The VM configuration 'vm.xml' has the following section.
    
```
<interface type='bridge'>
<mac address='52:54:00:30:9f:d0'/>
<source bridge='br0'/>
<model type='virtio'/>
<address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
</interface>
```

I'm not sure what I'm doing wrong.  I suspect it has something to do with installing the VM.

---

### Post by howefield on 2017-11-15
Thread moved to the "*Virtualisation*" forum.

---

### Post by TheFu on 2017-11-16
Which OS release?

Reboot or try **sudo service networking restart** or **sudo systemctl  restart networking.service**.
I found that systemd gets confused when bridges are part of the networking, so a restart doesn't work.  I have to manually bring down each interface in the correct order, then bring them back up in the reverse order to restart.  If there isn't any errors in the interfaces file(s), then it should work.

Be careful following really old, outdated, how-to guides.  Services have changed between 12.04, 14.04 and 16.04+. The init.d/ scripts are mostly deprecated.

If you need help with the interfaces, post it.  Inaccurate descriptions aren't helpful.
Posting the route and ifconfig for both the host and guest OS would be helpful too.

The VM.xml looks fine, but I'd use virtio instead of rtl8139. Always use virtio for networking and disk drivers for all VMs, if they support it.  Otherwise, use SATA/SCSI and the e1000 driver (intel PRO/1000).

Please use code tags when posting cmds AND output.  Too hard to read otherwise.  Adv Reply (#)
There are lots of tiny details that need to be correct. Facts are necessary to help.  Oh, and be certain to purge network manager once the static IP is working. It isn't installed on servers, so you don't need it.

---

### Post by fosol on 2017-11-16
Found out the problem, but not the resolution.

Did exact same steps with ubuntu 16.04.3 and it works fine.

Something is wrong with the installer/networking with 17.10.

I'll downgrade, already wasted two weeks on this.

---

