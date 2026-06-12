---
title: "kvm not able to connect to guest?"
date: 2009-01-01
forum: Virtualisation
---

### Post by eldaria on 2009-01-01
Ok, this might be stupid question.
I have searched google and these forums, but not been able to find a solution.
I Installed Ubuntu 8.10 server, with KVM.
I followed the guide on the Wiki how to set up a guest environment.
[https://help.ubuntu.com/community/JeOSVMBuilder](https://help.ubuntu.com/community/JeOSVMBuilder)

All is well except I can't find a way to connect to it.

The host is headless, wit no gui installed.
Host has IP 192.168.1.2
Guest has IP 192.168.1.200

I tried to connect with VNC, from an external host, but no luck. 
So I tried to change the vnc to listen to localhost and then do an ssh port forwarding, but that did not work either.

So I was thinking perhaps I can connect to it from a console, but using 'virsh -c qemu:///system console lnxsql' but that tells me there is none available.

I also tried ssh to it, but it tells me connection refused.

So what am I doing wrong here?

This is what I used to create the guest:
**lnxsql.cfg**
```

DEFAULT]
dest = lnxsql
arch = amd64
ip = 192.168.1.200
part = vmbuilder.partition
user = user
name = user
pass = user
tmpfs = -
firstboot = boot.sh
firstlogin = login.sh
templates = mytemplates
hostname = lnxsql

[ubuntu]
mirror = http://192.168.1.2:9999/ubuntu
suite = intrepid
flavour = virtual
addpkg = libevent1, libgssglue1, libnfsidmap2, librpcsecgss3, nfs-common, portmap, mysql-client, mysql-server, unattended-upgrades, acpid

[kvm]
libvirt = qemu:///system

```

**boot.sh**
```

apt-get update
apt-get install --qqy --force-yes openssh-server

```

**login.sh**
```

sudo dpkg-reconfigure console-setup
sudo dpkg-reconfigure mysql-server-5.0

```

**libvirt.xml**
```

<domain type='kvm'>
  <name>$hostname</name>
  <memory>#echo $mem * 1024 #</memory>
  <vcpu>1</vcpu>
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
    <interface type='bridge'>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='192.168.1.2'/>
#for $disk in $disks
    <disk type='file' device='disk'>
      <source file='$disk.filename' />
      <target dev='hd$disk.devletters()' />
    </disk>
#end for
  </devices>
</domain>

```

**Some diagnostics on the host**
```

$ netstat -tap
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.2:5900        *:*                     LISTEN      -               

$ virsh -c qemu:///system list
Connecting to uri: qemu:///system
 Id Name                 State
----------------------------------
  5 lnxsql               running

$ ssh 192.168.1.200
ssh: connect to host 192.168.1.200 port 22: Connection refused


$ ping -q -c 4 192.168.1.200
PING 192.168.1.200 (192.168.1.200) 56(84) bytes of data.

--- 192.168.1.200 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.488/0.509/0.519/0.030 ms


```

---

### Post by kasper22 on 2009-01-01
Is your host systems network configured correctly?  what does ifconfig show for your network.

Also try
virsh -c qemu:///system vncdisplay <guest>

That should spit out a number for the display, then do
vncviewer localhost:<output number>

---

### Post by EightBitHustler on 2009-01-01
Do...

```
$ virsh dumpxml nameOfVmHere > nameOfVmHere.xml
```

...and post the resulting XML here. I noticed what's defined in the template XML doesn't alway translate to the finished VM.

I too struggled with this. I managed to connect with virt-manager. My VMs don't use a GUI so installing openssh-server gave me all the access I needed.

---

### Post by eldaria on 2009-01-01
**Output of vncdisplay**

```

irsh -c qemu:///system vncdisplay lnxsql
Connecting to uri: qemu:///system
192.168.1.2:0

```

Then nothing happends.

**Output of ifconfig on host**

```
$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:17:31:bc:6c:c2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:febc:6cc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:349092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:357902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:133310115 (133.3 MB)  TX bytes:168702980 (168.7 MB)

eth0      Link encap:Ethernet  HWaddr 00:17:31:bc:6c:c2  
          inet6 addr: fe80::217:31ff:febc:6cc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:377524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:381081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151387010 (151.3 MB)  TX bytes:177309850 (177.3 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:164992861 (164.9 MB)  TX bytes:164992861 (164.9 MB)

vnet0     Link encap:Ethernet  HWaddr 56:c4:57:16:13:30  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::54c4:57ff:fe16:1330/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

vnet1     Link encap:Ethernet  HWaddr 3e:23:25:e6:26:97  
          inet6 addr: fe80::3c23:25ff:fee6:2697/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:8582 (8.5 KB)  TX bytes:145536 (145.5 KB)

```

**Output of xmldump**

```

'Connecting to uri: qemu:///system
<domain type='kvm' id='5'>
  <name>lnxsql</name>
  <uuid>d070085b-753a-8782-c4b6-65690ed99e6c</uuid>
  <memory>131072</memory>
  <currentMemory>131072</currentMemory>
  <vcpu>1</vcpu>
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
    <disk type='file' device='disk'>
      <source file='/raid/vm/lnxsql/ubuntu-kvm/disk0.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='disk'>
      <source file='/raid/vm/lnxsql/ubuntu-kvm/disk1.qcow2'/>
      <target dev='hdb' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:f3:f3:76'/>
      <source bridge='br0'/>
      <target dev='vnet1'/>
      <model type='virtio'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5900' listen='192.168.1.2'/>
  </devices>
</domain>

```

---

### Post by kasper22 on 2009-01-01
> Output of vncdisplay

Code:

irsh -c qemu:///system vncdisplay lnxsql
Connecting to uri: qemu:///system
192.168.1.2:0

Then nothing happends.

That is what should happen.  Now with that information try:
vncviewer 192.168.1.2:0

---

### Post by eldaria on 2009-01-02
> **kasper22 said:**
> 
vncviewer 192.168.1.2:0

Interesting, I could not get it to work first.

On the server I have no GUI installed, thus the vnc client is not installed there.

When I try to connect with the Mac OSX client that I normaly use to other VNC machines including a Kubuntu box, I get that it is not able to connect, same as when I try to connect to vnc://192.168.1.2:5900.

Then In OSX I booted up Virtual box and launched Kubuntu and installed xvnc4viewer and tried your command and I was able to connect.
Very odd, but it has solved the issue, apperantly the built in vnc viewer in OSX and KVM are not compatible.

Thanks for the help guys.
Brian Levinsen

---

