---
title: "Instance running but empty console.log"
date: 2011-03-04
forum: Ubuntu Cloud and Juju
---

### Post by ajith_kgs on 2011-03-04
Hi all,

I have been trying to setup an UEC. I followed the guide here, [http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf]("http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf"). I followed everything down to the last detail. I am able to get an instance running using the euca-run-instances command.

The instance goes from pending to running and the euca-describe-instace output is:

```
RESERVATION	r-44BC08B3	admin	default
INSTANCE	i-49E30837	emi-ECE11560	192.168.10.200	172.19.1.2	running	mykey	0		m1.small	2011-03-04T06:09:05.309Z	mycluster	eki-35CD1A6A

```

When I tried to ping the instance using:
```
ping 192.168.10.200
```

from my client as well as my clc and i get
```
From 192.168.10.200 icmp_seq=2 Destination Host Unreachable
From 192.168.10.200 icmp_seq=3 Destination Host Unreachable
From 192.168.10.200 icmp_seq=4 Destination Host Unreachable
```

I have added the permissions to the group default for tcp and icmp. Output of euca-describe-groups is:

```
GROUP	admin	default	default group
PERMISSION	admin	default	ALLOWS	tcp	22	22	FROM	CIDR	0.0.0.0/0
PERMISSION	admin	default	ALLOWS	icmp	-1	-1	FROM	CIDR	0.0.0.0/0
```

i checked nc.log in my node and it says:
```
[Fri Mar  4 11:39:06 2011][003583][EUCADEBUG ] doStartNetwork() invoked
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] StartNetwork(): SUCCESS return from vnetStartNetwork 0
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] StartNetwork(): done
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] doRunInstance() invoked (id=i-49E30837 cores=1 disk=2 memory=192)
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ]                          image=emi-ECE11560 at http://192.168.20.1:8773/services/Walrus/mybucket/maverick-server-uec-i386.img.manifest.xml
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ]                          krnel=eki-35CD1A6A at http://192.168.20.1:8773/services/Walrus/mybucket/maverick-server-uec-i386-vmlinuz-virtual.manifest.xml
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ]                          vlan=10 priMAC=D0:0D:49:E3:08:37 privIp=172.19.1.2
[Fri Mar  4 11:39:06 2011][003583][EUCADEBUG ] state change for instance i-49E30837: Unknown -> Staging (Pending)
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] network started for instance i-49E30837
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] retrieving images for instance i-49E30837 (disk limit=2048MB)...
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] verifying cached file in /var/lib/eucalyptus/instances//eucalyptus/cache/eki-35CD1A6A/kernel...
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] walrus_request(): downloading /tmp/walrus-digest-avZ1BX
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ]                   from http://192.168.20.1:8773/services/Walrus/mybucket/maverick-server-uec-i386-vmlinuz-virtual.manifest.xml
[Fri Mar  4 11:39:06 2011][003583][EUCADEBUG ] walrus_request(): writing GET output to /tmp/walrus-digest-avZ1BX on 'Fri Mar  4 11:39:06 2011'
[Fri Mar  4 11:39:06 2011][003583][EUCADEBUG ] walrus_request(): wrote 3513 bytes in 0 writes
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] walrus_request(): saved image in /tmp/walrus-digest-avZ1BX
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//eucalyptus/cache/eki-35CD1A6A/kernel /var/lib/eucalyptus/instances//admin/i-49E30837/kernel]
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] verifying cached file in /var/lib/eucalyptus/instances//eucalyptus/cache/emi-ECE11560/disk...
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] walrus_request(): downloading /tmp/walrus-digest-WN6xra
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ]                   from http://192.168.20.1:8773/services/Walrus/mybucket/maverick-server-uec-i386.img.manifest.xml
[Fri Mar  4 11:39:06 2011][003583][EUCADEBUG ] walrus_request(): writing GET output to /tmp/walrus-digest-WN6xra on 'Fri Mar  4 11:39:06 2011'
[Fri Mar  4 11:39:06 2011][003583][EUCADEBUG ] doDescribeResource() invoked
[Fri Mar  4 11:39:06 2011][003583][EUCADEBUG ] walrus_request(): wrote 5965 bytes in 0 writes
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] walrus_request(): saved image in /tmp/walrus-digest-WN6xra
[Fri Mar  4 11:39:06 2011][003583][EUCAINFO  ] vrun(): [cp -a /var/lib/eucalyptus/instances//eucalyptus/cache/emi-ECE11560/disk /var/lib/eucalyptus/instances//admin/i-49E30837/disk]
[Fri Mar  4 11:39:07 2011][003583][EUCADEBUG ] doDescribeInstances() invoked
[Fri Mar  4 11:39:07 2011][003583][EUCADEBUG ] doDescribeInstances(): instanceId=i-49E30837 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:49:E3:08:37 vlan=10 networkIndex=2 
[Fri Mar  4 11:39:13 2011][003583][EUCADEBUG ] doDescribeResource() invoked
[Fri Mar  4 11:39:13 2011][003583][EUCADEBUG ] doDescribeInstances() invoked
[Fri Mar  4 11:39:13 2011][003583][EUCADEBUG ] doDescribeInstances(): instanceId=i-49E30837 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:49:E3:08:37 vlan=10 networkIndex=2 
[Fri Mar  4 11:39:19 2011][003583][EUCADEBUG ] doDescribeResource() invoked
[Fri Mar  4 11:39:20 2011][003583][EUCADEBUG ] doDescribeInstances() invoked
[Fri Mar  4 11:39:20 2011][003583][EUCADEBUG ] doDescribeInstances(): instanceId=i-49E30837 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:49:E3:08:37 vlan=10 networkIndex=2 
[Fri Mar  4 11:39:26 2011][003583][EUCADEBUG ] doDescribeResource() invoked
[Fri Mar  4 11:39:26 2011][003583][EUCADEBUG ] doDescribeInstances() invoked
[Fri Mar  4 11:39:26 2011][003583][EUCADEBUG ] doDescribeInstances(): instanceId=i-49E30837 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:49:E3:08:37 vlan=10 networkIndex=2 
[Fri Mar  4 11:39:26 2011][003583][EUCAINFO  ] vrun(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/partition2disk /var/lib/eucalyptus/instances//admin/i-49E30837/disk 512 90]
[Fri Mar  4 11:39:29 2011][003583][EUCAERROR ] error: file /var/lib/eucalyptus/instances//admin/i-49E30837/disk not found
[Fri Mar  4 11:39:29 2011][003583][EUCAINFO  ] preparing images for instance i-49E30837...
[Fri Mar  4 11:39:29 2011][003583][EUCAINFO  ] adding key/tmp/sckey.Kctilh to the root file system at /var/lib/eucalyptus/instances//admin/i-49E30837/disk using (//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/add_key.pl //usr/lib/eucalyptus/euca_mountwrap)
[Fri Mar  4 11:39:29 2011][003583][EUCAINFO  ] vrun(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/add_key.pl //usr/lib/eucalyptus/euca_mountwrap 32256 /var/lib/eucalyptus/instances//admin/i-49E30837/disk /tmp/sckey.Kctilh]
[Fri Mar  4 11:39:29 2011][003583][EUCADEBUG ] system_output(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/gen_kvm_libvirt_xml --ephemeral --basepath='/var/lib/eucalyptus/instances//admin/i-49E30837']
[Fri Mar  4 11:39:29 2011][003583][EUCAINFO  ] currently running/booting:  i-49E30837
[Fri Mar  4 11:39:30 2011][003583][EUCAINFO  ] booting VM instance i-49E30837
[Fri Mar  4 11:39:30 2011][003583][EUCADEBUG ] state change for instance i-49E30837: Staging -> Booting (Pending)
[Fri Mar  4 11:39:30 2011][003583][EUCADEBUG ] state change for instance i-49E30837: Booting -> Running (Extant)
[Fri Mar  4 11:39:32 2011][003583][EUCADEBUG ] doDescribeResource() invoked
[Fri Mar  4 11:39:32 2011][003583][EUCADEBUG ] doDescribeInstances() invoked
[Fri Mar  4 11:39:32 2011][003583][EUCADEBUG ] doDescribeInstances(): instanceId=i-49E30837 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:49:E3:08:37 vlan=10 networkIndex=2 
[Fri Mar  4 11:39:38 2011][003583][EUCADEBUG ] doDescribeResource() invoked
[Fri Mar  4 11:39:38 2011][003583][EUCADEBUG ] doDescribeInstances() invoked
[Fri Mar  4 11:39:38 2011][003583][EUCADEBUG ] doDescribeInstances(): instanceId=i-49E30837 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:49:E3:08:37 vlan=10 networkIndex=2 

```

It says publicIp=0.0.0.0. So is it the problem with my eucalyptus network config? 

eucalyptus.conf:
```

# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
CLOUD_OPTS="-Xmx512m"

# Affects: SC
DISABLE_EBS="N"
DISABLE_ISCSI="N"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth1"
VNET_PRIVINTERFACE="eth0"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
DISABLE_TUNNELLING="N"
NODES=""
VNET_ADDRSPERNET="32"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="192.168.10.121"
VNET_PUBLICIPS="192.168.10.200-192.168.10.220"

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"
USE_VIRTIO_DISK="1"
USE_VIRTIO_ROOT="0"
#MAX_MEM=2048
#MAX_CORES="2"
#MAX_DISK="100"

##########################################################################
#
# Administrative overrides and customizations may go below, in accordance
# with the manpage for eucalyptus.conf(5).
#
# However, to modify Eucalyptus parameters, you are advised to use
# euca_conf(8), which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################

```

eucalyptus.local.conf:
```

# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).


# network configuration from the input configuration file
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="192.168.10.121"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="192.168.10.200-192.168.10.220"

```

I checked the console.log in my node and saw that it was empty. 0 bytes in size.. Is this normal? How else can i check if my VM is actually running?

I used a ubuntu maverick i386 image downloaded(manually, not through cloud admin interface) from the uec images site. I published the tarball file using the command

```
uec-publish-tarball maverick-server-uec-i386.tar.gz mybucket i386
```

while publishing the image it said it did not find a ramdisk.

I have been trying to get thing running for a couple of days now. I have searched around a lot. It'll be much appreciated if anyone could help me :)

---

### Post by raymdt on 2011-03-05
ajith_kgs,[B]
[/B]you can use vnc to debug the instance.
Just look at this tutorial  
[http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image](http://open.eucalyptus.com/participate/wiki/using-vnc-debug-image)

[B]
Please use the images from ubuntu-store when you are new to UEC. They are easy to install and you can use them to check if your installation was successful. Only then you can begin to deal with complex topics like NETWORK or selfmade images.[/B]
So this is just my opinion.
[B]
[/B]

---

### Post by pallaire on 2011-03-22
Hello **ajith_kgs**, did you find a solution to this problem ? My logs are 100% the same as yours.

This is happening only on a fresh Ubuntu 10.10 setup :confused: 

From the client, I can't ping the public IP of the instance
From the CLC/CC, I can't ping the public IP of the instance

[COLOR="Red"]From the NC, I can't ping the public IP of the instance
From the NC, I can't ping the **private** IP of the instance (172.19.1.2)[/COLOR]

**@raymdt**, using VNC would be really usefull if we could connect to an instance in anyway ! If I cant ping the running instance from anywhere, how will I be able to connect to its VNC server ? On my setup (fresh UEC 10.10 install) if I add "[I]<graphics type='vnc' port='-1' autoport='yes'
keymap='en-us' listen='0.0.0.0'/>[/I]" to my gen_kvm_libvirt_xml file, the instances will stay in the pending state.

:-k

On a fresh 10.04 install, these pings are working fine !

---

### Post by Rusty au Lait on 2011-03-24
What does the output from the command
euca-get-console-output
show?

---

### Post by pallaire on 2011-03-29
Hello,

I found some problems with 10.10 ... but I was able to debug enough to have a working setup.

[LIST=1]
[*]Images using SCSI are not working! 
[*]qcow2 images are not working in 10.10 ... they were in 10.04 LTS
[*]Splited front end setup is not working in 10.10 ... it was in 10.04 LTS
[/LIST]
**About problem #1 and #2:** 

All my problems were happening with my Windows XP image, it was working fine in 10.04 LTS, but I could not connect to them in 10.10! At first glance, I thought it was an iptables problem, but in fact, the problem was that the instance was never really running. Windows was stuck in its DOS mode telling me it could not boot. This error was not written to the console output, so if I ever did a "euca-get-console-output", I would get nothing. To find that error I had to debug directly on the node. I installed a minimal xorg on the NC and debugged following this procedure: [http://cssoss.wordpress.com/2010/05/04/ueceucalyptus-debugging-instances/](http://cssoss.wordpress.com/2010/05/04/ueceucalyptus-debugging-instances/) so on the NC were my instance was trying to start I would attach vncviewer to the instance! 

**Bug #1** ... they way that eucalyptus/libvirt create the SCSI device in 10.10 ... is really more complicated than any tutorial out there that show you how to create an image. In the tutorial, the scsi drive parameter is: 
```
-drive file=./disk,if=scsi,boot=on,index=1
```

The instance will receive :  
```
-device lsi,id=scsi0,bus=pci.0,addr=0x4 -device scsi-disk,bus=scsi0.0,scsi-id=0,drive=drive-scsi0-0-0,id=scsi0-0-0 -drive file=./disk,if=none,id=drive-scsi0-0-0,boot=on,format=raw 

```
Somewhere in this huge line, Windows Scsi driver is not working, it won’t boot with that, I tried this line manually with kvm, and I can reproduce the bug.

How to go around this bug? Use the IDE interface instead. To do that you will need to modify this file : **/usr/share/eucalyptus/gen_kvm_libvirt_xml**

Change that : ```
<target dev='sda'/>
```
To that :  ```
<target dev='hda'/>
```


**Bug #2** ... After fixing the bug #1, I was still not able to boot, I found the qcow2 format images are not supported in this version of libvirt/qemu/kvm !!!! How to go around that? Convert your image back to raw. 

```
qemu-img -f qcow2 -O raw disk disk.raw
```

Then re-bundle/upload/register your image and it will work!

One way to validate that your cloud is working fine is to use an image created by Ubuntu, you can find them there: [http://uec-images.ubuntu.com/](http://uec-images.ubuntu.com/)  Once you know that the cloud is working you can try to make other images work on it.


**Bug #3** ... I have not found a fix for this bug on 10.10 (this bug does not exist in 10.04), if you put the CLC+Walrus on one server, the CC+SC on another server, then a NC (or many) on another machine ... the instances won’t be able to talk to the walrus to download the files (kernel,boot,image) so the instances will be pending forever! There is something wrong with the way 10.10 Clusters manage the iptables, the NC cannot talk to the walrus, and it can only talk to the CC machine. You won’t see this bug if you follow every tutorials out there, because they are all a copy of the same tutorial that was made using only one machine as the front end (CLC+Walrus+CC+SC on one computer) Since the NC is limited to talk to the CC's computer, in this setup it’s the same machine as the Walrus, so it is working. I will try to contact eucalyptus about that.

---

