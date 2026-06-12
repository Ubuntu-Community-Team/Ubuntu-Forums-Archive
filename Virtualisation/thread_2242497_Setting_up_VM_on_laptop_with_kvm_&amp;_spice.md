---
title: "Setting up VM on laptop with kvm &amp; spice?"
date: 2014-09-02
forum: Virtualisation
---

### Post by Remten on 2014-09-02
I'd like to host a linux VM on a laptop with a linux host running kvm and spice. I've found lots of info on the internet from 2011 & 2012, but not as much from more recently. I've also seen plenty of articles discussing Windows guests, remote servers, Centos OS/Fedora/Arch, but very little on the specific scenario I'm most interested in (single machine and Ubuntu family) -- and even then, most of what I've found has been written at a level a bit beyond my comprehension.
So I'm hoping I can get some help here.

Thus far I've managed to successfully set up a VM with virt-manager, with qxl, virtio, and spice options selected, and I've even managed to make a few edits to the dumpxml file and re-define the VM settings.
I can run the VM and connect to the internet with it, viewing the VM desktop in virt-manager's console window.

What do I now need to do to take full advantage of spice? (Or is there no real advantage to spice in this scenario in which the host and guest are on the same physical machine?)

The dumpxml is:

```
<domain type='kvm'>
  <name>AlphaOS</name>
  <uuid>cfaafa3c-cc21-89bf-3f49-4685e9933672</uuid>
  <memory unit='KiB'>1048576</memory>
  <currentMemory unit='KiB'>1048576</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/AlphaOS.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='35:54:00:77:be:d2'/>
      <source network='default'/>
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
      <address type='virtio-serial' controller='0' bus='0' port='2'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'/>
    <sound model='ac97'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

I've installed spice-vdagent on the guest (using Synaptic), in an attempt to follow instructions here:
[http://www.linux-kvm.org/page/SPICE](http://www.linux-kvm.org/page/SPICE)
which says to do
```
# yum install spice-vdagent
# chkconfig --add spice-vdagent
# service start spice-vdagentd
(. . . log out of X, and log back in, verify agent is running . . . And you're done)
```
but I don't know what the current equivalent of chkconfig is, and I'm not quite sure how to log out of X and log back in and verify the agent is running (in Linux Mint 17 Mate).

I also don't know the steps for using SSH for the connection (or would that not even be appropriate, since the host and guest are on the same machine?).

---

### Post by TheFu on 2014-09-02
I wouldn't use spice on the same machine. Local connections are faster.

It has been awhile since I bothered with spice - [my notes]("http://blog.jdpfu.com/2013/10/27/ubuntu-13-10-under-kvm-with-spice").  It was fine for LAN use, but I never got the security working where it was useful over the internet.  I use x2go for that anyway from all over the world and don't plan to change.  With that setup, spice just isn't necessary.  BTW - audio streaming thru the ssh tunnel works great - even over the WAN, provided bandwidth is there.

BTW - never solved the non-working keys issue. THAT was really the show-stopper for me.

Haven't bothered with Spice on 14.04.

---

### Post by KillerKelvUK on 2014-09-03
I run a similar setup but my guest is Win7, tried VNC, RDP but settled on spice for the good mix of graphical and audio performance.

You're XML looks fine, have expanded mine to allow spice connections to the guest from other clients on my network i.e. laptop, desktop, smartphone as well as external.

```

<graphics type='spice' autoport='yes' listen='0.0.0.0'>
      <listen type='address' address='0.0.0.0'/>
</graphics>

```

In terms of connecting to the Spice server which is running on the host I simply use the package 'remote-viewer'...so once your guest has been started the spice connection is immediately available.  You'll need to check which port has been assigned...usually 5900+ and the URL format for the remote-viewer package is simply "spice://x.x.x.x: port" where x.x.x.x is the IP address of the HOST.  If you're running remote-viewer on the host itself you can use the loop-back address 127.0.0.1 vs. if you're accessing from another device on your LAN then it would be the HOSTs LAN IP e.g. 192.168.1.x

---

### Post by TheFu on 2014-09-03
> **KillerKelvUK said:**
> I run a similar setup but my guest is Win7, tried VNC, RDP but settled on spice for the good mix of graphical and audio performance.

You're XML looks fine, have expanded mine to allow spice connections to the guest from other clients on my network i.e. laptop, desktop, smartphone as well as external.

Did you get the SSL stuff working for all the different SPICE channels, using a full-VPN or are you "free-balling" it?

Also - no issue with keymappings?

---

### Post by KillerKelvUK on 2014-09-03
> **TheFu said:**
> Did you get the SSL stuff working for all the different SPICE channels, using a full-VPN or are you "free-balling" it?

Also - no issue with keymappings?

"free-balling" it bud, no real need for access across WAN just internal network so not attempted SSL stuff (firewall ports closed obviously).  Although just switched jobs and got mac for remote so might be tempted to see what I can get working in this regard.

Keymapping is fine, locale on my host is en-gb, the config is all default 14.04 from a clean install...never had an issue.

---

### Post by Remten on 2014-09-08
> **KillerKelvUK said:**
> I run a similar setup but my guest is Win7, tried VNC, RDP but settled on spice for the good mix of graphical and audio performance.

You're XML looks fine, have expanded mine to allow spice connections to the guest from other clients on my network i.e. laptop, desktop, smartphone as well as external.

```

<graphics type='spice' autoport='yes' listen='0.0.0.0'>
      <listen type='address' address='0.0.0.0'/>
</graphics>

```

In terms of connecting to the Spice server which is running on the host I simply use the package 'remote-viewer'...so once your guest has been started the spice connection is immediately available.  You'll need to check which port has been assigned...usually 5900+ and the URL format for the remote-viewer package is simply "spice://x.x.x.x: port" where x.x.x.x is the IP address of the HOST.  If you're running remote-viewer on the host itself you can use the loop-back address 127.0.0.1 vs. if you're accessing from another device on your LAN then it would be the HOSTs LAN IP e.g. 192.168.1.x

Just to clarify: By remote-viewer, do you mean "virt-viewer"? I can't find "remote-viewer" specifically, in the repositories I checked with Synaptic.
[http://manpages.ubuntu.com/manpages/trusty/en/man1/remote-viewer.1.html](http://manpages.ubuntu.com/manpages/trusty/en/man1/remote-viewer.1.html)

---

### Post by KillerKelvUK on 2014-09-08
Sorry yes, you're correct...

```

dpkg -S /usr/bin/remote-viewer 
virt-viewer: /usr/bin/remote-viewer

```

---

