---
title: "Can't remotely access VM - Server 16.04"
date: 2016-12-18
forum: Virtualisation
---

### Post by jeremy21 on 2016-12-18
Greetings all,
  Currently running 16.04 with the latest updates.  I had a year ago got a VM of Server working and was able to VNC, and SSH to it without issue.  Didn't use it for a year and forgot password so I blew it away to spin up another one.  Figured it was easy enough, however I can't VNC to the new VM.  Which makes it impossible for me to finish the OS install since my sever is headless.  I also can't SSH, it just goes to the host.

 Note, I did a dist-upgrade on the host box between then and now.  I also used these instructions, which I used before successfully - [http://xmodulo.com/use-kvm-command-line-debian-ubuntu.html](http://xmodulo.com/use-kvm-command-line-debian-ubuntu.html)

Hardware is a HP Gen 7 Microserver w/ on board, and additional NIC.

Configs - 

XML - ```

<domain type='kvm'>  
<name>webserver</name>
  <uuid>662f06ba-d823-11e5-8def-5f89d10e7a13</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='cdrom'/>
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
    <disk type="file" device="disk">
      <driver name="qemu" type="qcow2"/>
      <source file="/kvm/vms/webserver.img"/>
      <target dev="vda" bus="virtio"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x04" function="0x0"/>
    </disk>
    <disk type="file" device="cdrom">
      <driver name="qemu" type="raw"/>
      <source file="/kvm/iso/ubuntu-15.10-server-amd64.iso"/>
      <target dev="hdc" bus="ide"/>
      <readonly/>
      <address type="drive" controller="0" bus="1" target="0" unit="0"/>
    </disk>
    <interface type='bridge'>
      <source bridge='virbr0'/>
      <mac address="00:00:A3:B0:56:10"/>
    </interface>
    <controller type="ide" index="0">
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x1"/>
    </controller>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport="yes" listen='0.0.0.0'/>
    <console type='pty'>
      <target port='0'/>
    </console>
  </devices>
</domain>

```

/etc/network/interfaces - 
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto em1
iface em1 inet static
  address 192.168.1.3
  netmask 255.255.255.0
  network 192.168.1.0
  gateway 192.168.1.254
  dns-nameservers 192.168.1.2


# NIC addition
auto p2p1
iface p2p1 inet manual


#virtual interface for VM's
auto virbr0
iface virbr0 inet static
    address 192.168.1.4
    netmask 255.255.255.0
    network 192.168.1.0
    gateway 192.168.1.254
    dns-nameservers 192.168.1.2
  bridge_ports p2p1
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0

```

virsh list -
```

Id    Name                           State
----------------------------------------------------
 3     webserver                      running

```

vncdisplay webserver -
```

:0

```

brctl show - 
```

bridge name     bridge id               STP enabled     interfaces
virbr0          8000.00133b0f9359       no              p2p1
                                                        vnet0
```

sudo netstat -nap | egrep '(kvm|qemu)' -
```

tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      2206/qemu-system-x8
unix  2      [ ACC ]     STREAM     LISTENING     21917    2206/qemu-system-x8 /var/lib/libvirt/qemu/domain-webserver/monitor.sock
unix  3      [ ]         STREAM     CONNECTED     22766    2206/qemu-system-x8 /var/lib/libvirt/qemu/domain-webserver/monitor.sock

```

ifconfig -
```

em1       Link encap:Ethernet  HWaddr 38:ea:a7:a9:e7:7e
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3aea:a7ff:fea9:e77e/64 Scope:Link
          inet6 addr: 2602:306:3be1:6ed0:3aea:a7ff:fea9:e77e/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7114940 (7.1 MB)  TX bytes:1926283 (1.9 MB)
          Interrupt:18


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:30226 (30.2 KB)  TX bytes:30226 (30.2 KB)


p2p1      Link encap:Ethernet  HWaddr 00:13:3b:0f:93:59
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86644 errors:0 dropped:60 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6997602 (6.9 MB)  TX bytes:88008 (88.0 KB)


virbr0    Link encap:Ethernet  HWaddr 00:13:3b:0f:93:59
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:3be1:6ed0:213:3bff:fe0f:9359/64 Scope:Global
          inet6 addr: fe80::213:3bff:fe0f:9359/64 Scope:Link
          inet6 addr: 2602:306:3be1:6ed0:ccc0:f58f:145b:652f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4640139 (4.6 MB)  TX bytes:88008 (88.0 KB)


vnet0     Link encap:Ethernet  HWaddr fe:00:a3:b0:56:10
          inet6 addr: fe80::fc00:a3ff:feb0:5610/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:5434816 (5.4 MB)

```

  Thank you for your time.

---

### Post by TheFu on 2016-12-18
headless = use ssh for everything. Problem solved.

---

### Post by jeremy21 on 2016-12-18
I use vnc only for the installation of the OS.  Otherwise I do SSH for everything.  How do I install the OS without VNC?

Just edited main post - I can't SSH or telnet either.  It just connects to the host.

---

### Post by DuckHook on 2016-12-19
I don't use KVM/QEMU, but know how I would try doing this with VirtualBox. I assume you can translate these generalizations into KVM instructions with minimal effort:

[LIST=1]
[*]Create the server VM appliance locally,
[*]Set up appliance with proper authentication credentials, ssh configuration, ssh keys, etc using non-standard ssh port,
[*]Upload appliance to remote server (could take a while depending on your upload bandwidth),
[*]Hash upload to check for transmission integrity,
[*]Using CLI management app (on VB, it is called *vboxmanage*), create vm, attach appliance, start vm
[*]on host open the non-standard ssh port to vm, then ssh into vm.
[/LIST]
Voila: no GUI needed, no VNC. You end up with a more pristine virtual server with much less attack surface.

---

### Post by TheFu on 2016-12-19
> **jeremy21 said:**
> I use vnc only for the installation of the OS.  Otherwise I do SSH for everything.  How do I install the OS without VNC?

Just edited main post - I can't SSH or telnet either.  It just connects to the host.

So, you don't have an OS installed.  There are [a few different ways to accomplish that]("https://help.ubuntu.com/community/KVM/CreateGuests").  virt-install, cobbler, and if you want a GUI, use virt-manager over an ssh tunnel.  I suspect you'd prefer the last option.

The major tricks to using virt-manager are:
* setup ssh between the client and the KVM server. This has NOTHING to do with the VM at this point. The client needs to be some Linux/Unix machine or have access to remote X/Windows into another machine that supports X.
* Your userid on the KVM server needs to be in the libvirtd Unix group. Never use root for this.
* A normal Linux bridge needs to be setup.  I find that a manually created bridge is more stable than using the NAT/automatic created bridge provided with the libvirt install. I don't know why this is. It just works better.
* Run virt-manager from the client. Connect to the KVM server and follow the wizard for setting up a new VM. This will use VNC by default, but only though an encrypted ssh tunnel. VNC outside the tunnel isn't possible. Security. VNC is kinda slow. Plus the default is for VNC ports to move around, but that doesn't matter if you always connect through virt-manager.  If you want more performance - very near native, even of a LAN link, use SPICE as the remote display method. For a desktop Linux VM install, SPICE is easy.  I've never used it on a server. 
* QEMU/KVM storage defaults to qcow2 now and places those files under /var/lib/libvirt/ ... if that area doesn't have sufficient storage, you can add other storage areas or just use a *symbolic link* from there to another partition/LV so the default area is still useable throughout the GUI.  I tend to keep / only 10-20G in size, so /var/ really needs to be mounted from another LV/partition/disk to be much use for VMs.

**Opinion follows:** VirtualBox comes with baggage that I avoid. Corporate-type baggage. Review the license for the "Guest Additions" of vbox.  That company will monetize at some point, just like they are attempting to do with non-base versions of Java, MySQL, previously attempted with OpenOffice and how they killed OpenSolaris off.  vbox core is GPL, but the guest additions ARE NOT. Beware. Review the EULA very carefully. Sadly, if your desktop is Windows, virtualbox is the least *bad* option.   Or just use KVM, libvirt, and all the other GPL tools which work better, more solid, faster, than these commercial offerings.  I ran with vbox and 5 of VMware's products for many years before KVM/qemu was great for desktops, BTW.  

I've seen people running CAD systems over SPICE. Getting SPICE working with Windows clients is something I haven't cracked, but I know people who do it. They only run local VMs and I only run remote VMs, so that could be the different.  For my "productivity app" remote access, x2go works well. Feels about 2-3x faster than either RDP or VNC.  But for servers, like you, I use ssh for everything.  virt-manager is only used when "console" access is required.  That happens about once a year across all my running VMs.

I have never used the **ubuntu-vm-builder** or the Cobbler methods. I've only seen presentations at Linux meetings on each. If I were inside a company that needed to create more than 5 VMs a week, I'd [setup cobbler]("https://help.ubuntu.com/community/Cobbler").

Anyway, there are lots of tutorials and youtube videos about getting KVM working with virt-manager.  It is pretty easy.

Sorry for babbling and I hope this is helpful to someone. We all come from different experiences and I've been burned by some of the commercial VM companies.  Just sayin'.

---

### Post by jeremy21 on 2016-12-19
Thank you for your reply.  I get the feeling that the method I used to start on my server is a little... out of bounds.. of what most people are using on the board.  Agree on your comment on virtualbox.  I run that on my Win10 machine for netsec training, but wouldn't do it on my FOSS stuff since there's comparable and good alternatives.  I'm already encumbered by Win10...what's a little more.

> **TheFu said:**
> 
The major tricks to using virt-manager are:
* setup ssh between the client and the KVM server. This has NOTHING to do with the VM at this point. The client needs to be some Linux/Unix machine or have access to remote X/Windows into another machine that supports X.


Currently SSH in from my Win10 box, but it needs X.  Would my MacBook work?  I could also spin up a ubuntu desktop VM in VBox for work.  Is it worth it that much to have a GUI on the server?

> **TheFu said:**
> 
* Your userid on the KVM server needs to be in the libvirtd Unix group. Never use root for this.


username is both in the "kvm" and "libvertd" groups.  However the folders I made for my VMS are root accessible only.  Wasn't an issue before I don't think.

> **TheFu said:**
> 
 * A normal Linux bridge needs to be setup.  I find that a manually created bridge is more stable than using the NAT/automatic created bridge provided with the libvirt install. I don't know why this is. It just works better.


I believe that's what I had set up now with the config changes to /etc/network/interfaces I posted above.  Is this not the case?  I prefer hard coded/static when possible.

> **TheFu said:**
> 
 * Run virt-manager from the client. Connect to the KVM server and follow the wizard for setting up a new VM. This will use VNC by default, but only though an encrypted ssh tunnel. VNC outside the tunnel isn't possible. Security. VNC is kinda slow. Plus the default is for VNC ports to move around, but that doesn't matter if you always connect through virt-manager.  If you want more performance - very near native, even of a LAN link, use SPICE as the remote display method. For a desktop Linux VM install, SPICE is easy.  I've never used it on a server. 


Thinking about backing up all my data and just re-rolling the server at this point.  I use VNC to connect to my MacBook (Linux ISO torrent box) so I'm aware of the drawbacks, but I'll check into SPICE, thanks for the info.

Do I have to have SSH'd to the server first, then fire up virt-manager on the client?

> **TheFu said:**
> 
 * QEMU/KVM storage defaults to qcow2 now and places those files under /var/lib/libvirt/ ... if that area doesn't have sufficient storage, you can add other storage areas or just use a *symbolic link* from there to another partition/LV so the default area is still useable throughout the GUI.  I tend to keep / only 10-20G in size, so /var/ really needs to be mounted from another LV/partition/disk to be much use for VMs.


Got 95Gb free on the /, so space isn't an issue.

Thanks for the rest of your notes as well.  If you've got any tutorials or videos you trust I'm interested.  I do RTFM and search... this one's just coming up 00000's.

---

### Post by TheFu on 2016-12-19
I don't know anything about Win10 or OSX. Sorry.  Never touched Win10 and used OSX for 2 weeks before giving the machine back. It wasn't for me.

Been doing virtualization since the late 1990s, so don't really use tutorials or videos. Sorry.  Used to give presentations internationally on virtualbox and KVM tuning and optimizations, but haven't done that in a few years.

SPICE isn't useful for a non-GUI install, as in servers. ssh.

"libvertd" is the wrong group name. It must be "libvirtd". Details matter. Posting incorrect data here is not productive. Copy/paste solves much of that.

Your bridge has more entries than needed. If any are wrong, confusion will happen.  Remove the "network" line. It is not necessary.  Also, I'd choose a different name for the bridge, not one that is commonly used and expected by libvirt. Don't know if this matters or not, just what I'd do.

virt-manager is an X/Client.  It needs a local X/Server to work. It can be run local or remote.  Or just use virt-install over ssh. I limit remote access to my VM hosts to the LAN over ssh, but from almost anywhere, I can use x2go (remote desktop) into my LAN, then on that Linux "desktop", run virt-manager if console access is needed or if I need to spin up a quick VM to show something.  On that same Linux desktop, I've used RDP (on the LAN only!!!!) to connect to a Win7 machine to schedule TV recording. Basically, a remote desktop (x2go) into a less efficient (rdp) remote desktop. All of the internet traffic encrypted over ssh using keys, never passwords.

---

### Post by jeremy21 on 2016-12-21
Yea, I mistyped it on here.  The group is correct "libvirtd" on the box.

---

