---
title: "Can't get containers to talk to bridged network"
date: 2010-10-03
forum: Virtualisation
---

### Post by Nighthog on 2010-10-03
Hi all,

not sure if this is the right forum but what I'm trying to do is get a Centos 5.5 container with a fixed IP address running under host 10.04.1 (desktop)  talking to the Wibbly Wobbly Way.  I understand (perhaps incorrectly) that you can't bridge a wireless network so my plan is to bridge eth0 so I can talk to the web when I have a cabled link to my home wireless router.  I had a lot of trouble with talking to eth0 at all but dumping network-manager in favour of wicd certainly helped.

Anyway, having spent far too many hours going round in circles I'm pleading for help!  Here's what I've done so far:

  	 	 	 	p { margin-bottom: 0.21cm; }code.cjk { font-family: "DejaVu Sans",monospace; } Create a directory for Control Groups and ensure it mounts on system startup:
 

 mkdir /cgroup
 

 edit /etc/fstab to include this line:
 

 none /cgroup cgroup defaults 0 0
 

 Configure bridge networking.  Create bridge interface br0, assign it IP address 192.168.1.10, reset it to 0.0.0.0 but it's bound to the bridge interface so it responds to  192.168.1.10 anyway.  Add a route for br0 which will be used by the containers to connect to the network:
 

 brctl addbr br0
 brctl setfd br0 0
 ifconfig br0 192.168.1.10 promisc up
 brctl addif br0 eth0
 ifconfig eth0 0.0.0.0 up
    	 	 	 	p { margin-bottom: 0.21cm; }  

 Specify the nameserver for the bridged network.  Ensure this line is in /etc/resolv.conf:
 

 nameserver 192.168.1.1
 

 Edit /etc/sysctl.conf for network pass-thru:
 

 [INDENT]Uncomment net.ipv4.ip_forward=1 and add the following lines:  
net.ipv4.conf.default.proxy_arp = 0  
net.ipv4.conf.all.rp_filter = 1  
kernel.sysrq = 1  
net.ipv4.conf.default.send_redirects = 0  
net.ipv4.icmp_echo_ignore_broadcasts = 1  
net.ipv4.conf.default.forwarding = 1
[/INDENT]          	 	 	 	p { margin-bottom: 0.21cm; }code.cjk { font-family: "DejaVu Sans",monospace; }  Create a home for all lxc resources (config files, root filesystems etc.):
 

 mkdir /var/lxc
 mkdir /var/lxc/rootfs                (for the containers' root filesystems)
 mkdir /var/lxc/ovz_templates  (and copy my OpenVZ templates here)
 

 **Create a 32-bit container to be called ve101**.  Start by tweaking an OpenVZ template:   
 

 Create the root filesystem from an OpenVZ template:
 

 cd /var/lxc/rootfs
 mkdir ve101
 cd ve01
 tar -zxvf ../../ovz_templates/centos-5-x86.tar.gz
 

 Set up the networking within the Centos container.  Create file /var/lxc/rootfs/ve101/etc/sysconfig/network-scripts/ifcfg-eth0:
 

 [SIZE=2]DEVICE=eth0[/SIZE]
 [SIZE=2]BOOTPROTO=static	[/SIZE]
 [SIZE=2]ONBOOT=yes[/SIZE]
 [SIZE=2]IPADDR=192.168.1.101[/SIZE]
 [SIZE=2]NETMASK=255.255.255.0[/SIZE]
 [SIZE=2]BROADCAST=192.168.1.255[/SIZE]
 

 edit /var/lxc/rootfs/ve101/etc/rc.d/rc.sysinit to clean up old pid files and not start udev (what that?):
 

 # get rid of any lurking daemon/service process pids from the container 
 rm -f $(find /var/run/ -name '*pid')  
 rm -f /var/lock/apache/*
 .
 .
 .
 # /sbin/start_udev
 

 create /var/lxc/rootfs/ve101/etc/modprobe.d/blacklist:
 

 blacklist ipv6  
 blacklist net-pf-10
 

 create /var/lxc/rootfs/ve101/etc/sysconfig/network:
 

 NETWORKING_IPV6=no
 

 edit /var/lxc/rootfs/ve101/etc/sysconfig/iptables-config:
 

 IPTABLES_MODULES_UNLOAD="no"
 

 Create the container's config file /var/lxc/config.ve101:
 

 # The hostname for the container  
 lxc.utsname = ve101  
 # need to find out about ttys !!  
 lxc.tty = 4  
 #  
 lxc.network.type = veth  
 lxc.network.flags = up  
 lxc.network.link = br0  
 # the name of the network interface within the container  
 lxc.network.name = eth0  
 lxc.network.mtu = 1500  
 lxc.network.ipv4 = 192.168.1.101/24  
 # full path to the root file system of the container  
 lxc.rootfs = /var/lxc/rootfs/ve101  
 # full path to the fstab file of the container  
 lxc.mount = /var/lxc/fstab.ve101  
 # deny access to all devices then add accesses in  
 lxc.cgroup.devices.deny = a  
 # /dev/null and zero  
 lxc.cgroup.devices.allow = c 1:3 rwm  
 lxc.cgroup.devices.allow = c 1:5 rwm  
 # consoles  
 lxc.cgroup.devices.allow = c 5:1 rwm  
 lxc.cgroup.devices.allow = c 5:0 rwm  
 lxc.cgroup.devices.allow = c 4:0 rwm  
 lxc.cgroup.devices.allow = c 4:1 rwm  
 # /dev/{,u}random  
 lxc.cgroup.devices.allow = c 1:9 rwm  
 lxc.cgroup.devices.allow = c 1:8 rwm  
 # /dev/pts/* pts namespaces (not implemented yet)  
 lxc.cgroup.devices.allow = c 136:* rwm  
 lxc.cgroup.devices.allow = c 5:2 rwm  
 # rtc  
 lxc.cgroup.devices.allow = c 254:0 rwm
 

 Create an fstab file to define the container's mount points.  Create fstab.ve101:
 

 none /var/lxc/rootfs/ve101/dev/pts  devpts defaults 0 0  
 none /var/lxc/rootfs/ve101/proc  proc defaults 0 0  
 none /var/lxc/rootfs/ve101/sys  sysfs defaults 0 0  
 

 Initialise the container:
 

 cd /var/lxc
  lxc-create -f ./config.ve101 -n ve101
 

 Set the root password for the container:
 

 lxc-start -n ve101 passwd
 

 Start the container:
 

 lxc-start -n ve101 -d
 

 
  	 	 	 	p { margin-bottom: 0.21cm; }  Hooray!  I can Putty into the container and have a look around.  I can ping 192.168.1.1 and 192.168.1.4 (the host IP address) from the container.  BUT I can't talk to the outside world (eg. can't ping [www.bbc.co.uk](www.bbc.co.uk) and yum update doesn't resolve the server).

 
However .... setting up br0 worked first time but did not after a reboot.  Br0 had disappeared.  Putting these commands in a file and running them then made eth0 stop working too. 

So, after rebooting for the umpteenth time my wireless and wired work from the host but my container is still in the dark.  And no sign of br0.  Can anyone please give me a steer?  I know there are folk out there doing something similar.  Maybe bridged networking is the wrong way to go?  I'm an applications man and now squat about networks so please offer advice in simple terms! 

Many thanks in advance...

---

### Post by andysq on 2010-10-04
had a similar issue, was expecting the bridge I created as br0 to work properly but found "brctl show" showed virbr0 instead; changed the container bridge and things started working. I also discovered the containers had no default gateway to begin with, which didn't help. Container is now SSH-able from other hosts on LAN, can apt-get update and so on. This is on Lucid, with Intrepid containers. I haven't managed to get a Fedora container running on Lucid yet, but tbh haven't tried that hard as the Lucid/Intrepid combination is good enough.

---

### Post by Nighthog on 2010-10-04
Thanks, busy tonight but I'll have another go asap.  From memory though I don't remember seeing vibr0 or anything similar with brctl show ... I'll get some more details!

Feel like I'm so nearly there, it's very frustrating.

---

