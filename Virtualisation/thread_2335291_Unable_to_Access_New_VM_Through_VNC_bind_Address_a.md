---
title: "Unable to Access New VM Through VNC: bind: Address already in use"
date: 2016-08-27
forum: Virtualisation
---

### Post by damo12 on 2016-08-27
Hi,

I am trying to experiment with virtualization but have hit a stumbling block at pretty much the first hurdle.

I am running a headless server running Ubuntu 16.04.1 which is accessed through Putty and Webmin.  I have created a kvm virtual machine using the guide at [http://www.cyberciti.biz/faq/how-to-install-kvm-on-ubuntu-linux-14-04/](http://www.cyberciti.biz/faq/how-to-install-kvm-on-ubuntu-linux-14-04/) as a base.

I created the machine using the code:
```
sudo virt-install \
--virt-type=kvm \
--name guestubuntu \
--ram 512 \
--vcpus=1 \
--os-variant ubuntu16.04 \
--hvm \
--cdrom=/var/lib/libvirt/boot/ubuntu-16.04.1-server-amd64.iso \
--network network=default,model=virtio \
--graphics vnc \
--disk path=/var/lib/libvirt/images/guesutbuntu.img,size=10,bus=virtio
```


Once the machine was created I used the command:
```
sudo virsh dumpxml guestubuntu | grep vnc
```

which gave the output of:
```
<graphics type='vnc' port='5900' autoport='yes' listen='127.0.0.1'>
```

I then used the command:
```
ssh username@servername -L 5900:127.0.0.1:5900
```
but I received a warning message:
```
bind: Address already in use
```

When I try to connect from a Windows machine using a VNC viewer I receive a message that the "Connection was refused by the host computer".

The output of the guestubuntu.xml file is:
```
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit guestubuntu
or other application using the libvirt API.
-->

<domain type='kvm'>
  <name>guestubuntu</name>
  <uuid>005ce974-a999-44fd-a1b4-e92a89538096</uuid>
  <memory unit='KiB'>524288</memory>
  <currentMemory unit='KiB'>524288</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-wily'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>phenom</model>
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
      <source file='/var/lib/libvirt/images/guesutbuntu.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
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
    <interface type='network'>
      <mac address='52:54:00:66:aa:c0'/>
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
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <video>
      <model type='cirrus' vram='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```


Any guidance on where I am going wrong would be greatly appreciated.

---

### Post by KillerKelvUK on 2016-08-27
Think your problem is the remote side of your ssh.  Try something like

```

ssh -L 5900:ip_of_headless_server:5900 username@ip_of_headless_server

```

You could of course allow direct VNC connections by changing the listen address of your guest xml to 0.0.0.0 and just connect vnc directly without SSH tunnelling, if this is a local network I'd suggest the security implications are permissible...remote network then your SSH tunnelling is spot on.

EDIT:

As an alternative to VNC you could try SPICE with TLS configured although I've no experience recommending this, just options to consider.

---

### Post by TheFu on 2016-08-27
putty doesn't work with VNC.  Need to use a VNC client to connect.  I've never used virt-install and I started with Linux virtualization in 2008.

I don't use Windows, so don't know how to make it work from that platform, but on Linux clients, you can install virt-manager on the client machine and everything becomes double-click this-that for installations and remote access.  virt-manager provides "console" access. Console access is generally crap and using ssh or some other remote desktop tool post-install works great. You can use putty (ssh), provided you installed and configured the ssh-server package.  I mostly use ssh to manage servers, but run 1 remote desktop to my primary "desktop" system, which runs headless inside a KVM VM.  x2go is the best, F/LOSS remote desktop that I know. It is 2-3x faster than VNC and uses ssh-tunnels by default. That means ssh-keys work too, so connections don't use passwords. Using passwords 10 minutes after a new server is installed is a complete failure in my mind. Always, always, always, use ssh-keys ASAP and disable password-based authentication for all remote (non-console) access.

Respect to KillerKelvUK, but I think he misread the issue (we all do that sometimes, especially me).  ssh usually listens on port 22. VNC usually listens on 5900. Trying to connect with ssh on 5900 won't work.

---

### Post by KillerKelvUK on 2016-08-27
Hey Fu, not following what I've misunderstood...OP is trying to tunnel port 5900 from Windows client to Ubuntu host as his Windows guest is configured to only allow VNC connections from the localhost and whilst the post doesn't say which vnc client it does mention the use of a vnc client.  I am dubious about my posted ssh tunnelling cmd (definitely not my forte) but I don't see where i've got my wires crossed?

---

### Post by TheFu on 2016-08-27
> **KillerKelvUK said:**
> Hey Fu, not following what I've misunderstood...OP is trying to tunnel port 5900 from Windows client to Ubuntu host as his Windows guest is configured to only allow VNC connections from the localhost and whilst the post doesn't say which vnc client it does mention the use of a vnc client.  I am dubious about my posted ssh tunnelling cmd (definitely not my forte) but I don't see where i've got my wires crossed?

Perhaps I have my wires crossed?  Appears that way on 3rd look. ;) Yep. **I'm definitely wrong.**

Tried to connect to a KVM host (14.04 server) and different clients following:
[http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html) 

It didn't work. My settings are a little different. The OP's settings appear to be correct, so I doubt that is the issue. Got this error 
```
$ ssh -L 5903:localhost:5903 -N -f -l thefu romulus
bind: Cannot assign requested address
channel_setup_fwd_listener_tcpip: cannot listen to port: 5903
Could not request local forwarding.
```

However, using virt-manager ... and connecting to the same client VM works fine over port 5903.  I'm at a loss.
**lsof** (on the KVM host) shows that 5903 is LISTENing.  
Tried gnvcviewer, both directly and through the tunnel. No joy.  I dunno.  It appears that the ssh-tunnel isn't working.

Tried with a few other VMs. No joy.

**virt-manager** is working perfectly. Don't know why, just know that it works. Sadly, don't know of an alternative "console" that works from Windows.  Could just ssh in and use **virsh console** command, I suppose.

---

### Post by damo12 on 2016-08-27
Thanks KillerKelvUK

I tried your suggestion but still had the same problem.  Just to clarify, my initial command to tunnel the access was actually ```
ssh host_server_username@hostserver -L 5900:127.0.0.1:5900
```

I tried uncommenting "vnc_listen = "0.0.0.0"" in /etc/libvirt/qemu.conf but still have the same problem.

For reference, I have tried to access using Tight VNC and VNC Viewer with the server entered as:```
localhost::5900
```or```
127.0.0.1::5900
```

---

### Post by TheFu on 2016-08-27
:: won't help. Try hostname:5900.  [https://superuser.com/questions/391525/vnc-port-numbers](https://superuser.com/questions/391525/vnc-port-numbers) makes me think that using 5901 would be a better choice, at least for testing, today, on Linux. Also, if there is a firewall running, be certain to open these ports for localhost. In theory, localhost should always be able to talk to localhost, but some copy/paste firewall setups don't do that.

Each VM has an XML config file. It must be edited using **virsh edit ....** (or some other tool) - find the 127.0.0.1 VNC line and change that.
```
    <graphics type='vnc' port='5912' autoport='no' listen='0.0.0.0'>

``` My ports are different, don't worry about it.  Using their edit command handles some libvirt behind-the-scenes stuff related to re-registering updates to the config files.  In the old days, we'd just re-"define" the VM using virsh.

---

### Post by KillerKelvUK on 2016-08-27
@TheFu...man you had me scratching my head lol

@damo12, editing /etc/libvirt/qemu.conf after you've created your guest won't alter how qemu starts the vnc server as it will be reading the guests configuration xml. hence why @TheFu is advising you to amend the guest configuration using virsh.

Another sanity check would be to verify that the vnc server has actually started on your host and has opened up a listening connection on port 5900.  Confirm with the following or similar as you desire....

```
 sudo netstat -tulpn 
```

---

### Post by damo12 on 2016-08-27
I have tried changing the xml file using the command:```
sudo virsh edit guestubuntu
```

It now reads:```
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit guestubuntu
or other application using the libvirt API.
-->

<domain type='kvm'>
  <name>guestubuntu</name>
  <uuid>93e54092-048c-4e0c-85cb-148795546a88</uuid>
  <memory unit='KiB'>524288</memory>
  <currentMemory unit='KiB'>524288</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-wily'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>phenom</model>
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
      <source file='/var/lib/libvirt/images/guesutbuntu.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
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
    <interface type='network'>
      <mac address='52:54:00:a5:51:61'/>
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
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='5912' autoport='no' listen='0.0.0.0'>
      <listen type='address' address='0.0.0.0'/>
    </graphics>
    <video>
      <model type='cirrus' vram='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```

When I try:```
sudo virsh dumpxml guestubuntu | grep vnc
```
IThe output is still:```
<graphics type='vnc' port='5900' autoport='yes' listen='127.0.0.1'>
```


I checked the ports and the relevant lines are:```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:5192          0.0.0.0:*               LISTEN      4452/ssh        
tcp        0      0 127.0.0.1:5900          0.0.0.0:*               LISTEN      3546/qemu-system-x8
```


In case the vm was corrupted I destroyed it and created a new one from scratch.  I'm not sure if it's something I'm doing wrong but I found that when I built the machine, Putty seems to stop with the output:```
WARNING  Graphics requested but DISPLAY is not set. Not running virt-viewer.
WARNING  No console to launch for the guest, defaulting to --wait -1

Starting install...

Creating domain...                                          |    0 B  00:02     
Domain installation still in progress. Waiting for installation to complete.
```

I could not do anything from this screen so I started a new Putty session changed the xml file then ran the command:```
ssh host_user_name@host_server_name -L 5192:127.0.0.1:5192
```

The screen refreshed as if I had just logged in and showed the message:```
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-34-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.


Last login: Sat Aug 27 18:36:20 2016 from 192.168.0.11

host_user_name@Host_server:~$
```

---

### Post by KillerKelvUK on 2016-08-27
Result!

Recommend you use caution with sudo, typically you shouldn't need root access to managed vm's using virsh etc, it can cause some complications down the line.

---

