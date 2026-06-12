---
title: "Cant get Heartbeat to work with iSCSI server with HA"
date: 2013-01-14
forum: Server Platforms
---

### Post by optimuslobo on 2013-01-14
Hi I have been looking on the internet for information regarding this and I really need help, so far the best I got are this guides:

1 - [http://www.howtoforge.com/setting-up-network-raid1-with-drbd-on-ubuntu-11.10](http://www.howtoforge.com/setting-up-network-raid1-with-drbd-on-ubuntu-11.10)
2 - [http://ubuntuforums.org/showthread.php?t=1189523](http://ubuntuforums.org/showthread.php?t=1189523)
3 - [http://samcaldwell.net/index.php/technical-articles/3-how-to-articles/108-iscsi-cluster-setup-guide](http://samcaldwell.net/index.php/technical-articles/3-how-to-articles/108-iscsi-cluster-setup-guide)
4 - [http://0wned.it/geek-bits/guides/high-availability-iscsi-target-using-linux/](http://0wned.it/geek-bits/guides/high-availability-iscsi-target-using-linux/)

for now Im not bonding network cards just trying to get an ISCSI target with fail over and replication, I get to work the replication with drbd and the iscsi target but for some reason cant get heartbeat to work for the fail over feature, I have try several distros

Ubuntu 10.04
Ubuntu 11.10
Ubuntu 12.04

hear are the the config files Im using for this project

Packets I'm installing to start

apt-get install ntp iscsitarget drbd8-utils heartbeat


1) Host configuration: 

nano /etc/hosts
=========================
127.0.0.1    localhost
10.10.204.240   nod1 nod1

10.10.204.250   nod1_eth1 nod1_eth1

10.10.204.254   nod2 nod2 nod2

10.10.204.251   nod2_eth1 nod2_eth1

2) Ethernet setup:

nano /etc/network/interfaces
============================
auto eth0
iface eth0 inet static
    address 10.10.204.240
    netmask 255.255.255.0
    network 10.10.204.0
    broadcast 10.10.204.255
    gateway 10.10.204.254
    dns-namerservers 8.8.8.8

auto eth1
iface eth1 inet static
    address 10.10.204.250
    netmask 255.255.255.0
    network 10.10.204.0

*same config for node2, just replace ip .240 with .241 and .250 with .251
==============================    

3) Install ntp - sudo apt-get install ntp


4) Install drbd8-utils & hearbeat 

sudo apt-get install drbd8-utils heartbeat

Set Permissions for DRBD

chgrp haclient /sbin/drbdsetup
chmod o-x /sbin/drbdsetup
chmod u+s /sbin/drbdsetup
chgrp haclient /sbin/drbdmeta
chmod o-x /sbin/drbdmeta
chmod u+s /sbin/drbdmeta

==================================
DRBD file configuration:
nano /etc/drbd.conf
==================================
resource lun1 {

        protocol C;
 
        handlers {
        pri-on-incon-degr "echo o > /proc/sysrq-trigger ; halt -f";
        pri-lost-after-sb "echo o > /proc/sysrq-trigger ; halt -f";
        local-io-error "echo o > /proc/sysrq-trigger ; halt -f";
        outdate-peer "/usr/lib/heartbeat/drbd-peer-outdater -t 5";      
        }

        startup {
        degr-wfc-timeout 120;
        }

        disk {
        on-io-error detach;
        }

        net {
        cram-hmac-alg sha1;
        shared-secret "password";
        after-sb-0pri disconnect;
        after-sb-1pri disconnect;
        after-sb-2pri disconnect;
        rr-conflict disconnect;
        }

        syncer {
        rate 100M;
        verify-alg sha1;
        al-extents 257;
        }

        on nod1 {
        device  /dev/drbd0;
        disk    /dev/sdb1;
        address 10.10.204.240:7788;
        meta-disk internal;
        }

        on nod2 {
        device  /dev/drbd0;
        disk    /dev/sdb1;
        address 10.10.204.241:7788;
        meta-disk internal;
        }
}

====================================

Duplicate the DRBD configuration to the other server.

scp /etc/drbd.conf root@10.10.204.241:/etc/

Initialize meta-data 

[node1]drbdadm create-md all
[node2]drbdadm create-md all

Start the drbd service

[node1]/etc/init.d/drbd start
[node2]/etc/init.d/drbd start

Set nod1 as primary:
drbdadm -- --overwrite-data-of-peer primary all

After initial sync is complete then mount and format /dev/drbd0

[node1]mkfs.ext3 /dev/drbd0
[node1]mkdir -p /srv/data
[node1[mount /dev/drbd0 /srv/data
=====================================

5) Install iSCSI target on both nodes

 a) [node1]apt-get -y install iscsitarget
    [node2]apt-get -y install iscsitarget

 b) Edit /etc/defaults/iscsitarget and set ISCSITARGET_ENABLE to true.

 c) Heartbeat will be used to control the iscsitarget service so remove it from init:

  update-rc.d -f iscsitarget remove

 d) Relocate the iSCSI configuration to the DRBD device

[node1]mv /etc/ietd.conf /srv/data
[node1]ln -s /srv/data/ietd.conf /etc/ietd.conf
[node2]rm /etc/ietd.conf
[node2]ln -s /srv/data/ietd.conf /etc/ietd.conf

 e) Define iSCSI target

nano /srv/data/ietd.conf

Target iqn.2013-01.local.pride:lun1.disk0
        Lun 0 Path=/srv/data/storlun0.bin,Type=blockio

 f) Create file .bin to store data
dd if=/dev/zero of=/srv/data/storlun0.bin count=0 obs=1 seek=100G

 g) Allow connections to target

nano /etc/initiators.allow 

uncomment everythin and set to ALL ALL so I can connect to the target 

6) Finally, configure heartbeat to control a Virtual IP address and failover iSCSI in case a node fails, this is the part that i cant get to work for some reason


On node1, define the cluster within /etc/heartbeat/ha.cf. 

logfacility     local0

autojoin        none
auto_failback   no

keepalive       2
deadtime        10
warntime        5
initdead        120

mcast           eth0 239.0.0.1 694 1 0 
bcast           eth1

node            san01-n1
node            san01-n2

respawn         hacluster /usr/lib/heartbeat/ipfail
ping            10.10.204.245

=================================
I read the Ubuntu manuals for the definition of each part of ha.cf 
[http://manpages.ubuntu.com/manpages/lucid/man5/ha.cf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/ha.cf.5.html)

On node1, define the authentication mechanism within /etc/heartbeat/authkeys the cluster will use. 
nano /etc/heartbeat/authkeys

auth 3
3 md5 password

****Change the permissions of /etc/heartbeat/authkeys.
chmod 600 /etc/heartbeat/authkeys

=====================
On node1, define the resources that will run on the cluster within /etc/heartbeat/haresources

nano /etc/hearbeat/haresources

IPaddr2::10.10.204.245/24/eth0 drbddisk::lun1 Filesystem::/dev/drbd0::/srv/data::ext3

=====================
Copy the cluster configuration files to the second node

scp /etc/heartbeat/ha.cf root@10.10.204.241:/etc/heartbeat/
scp /etc/heartbeat/authkeys root@10.10.204.241:/etc/heartbeat/
scp /etc/heartbeat/haresources root@10.10.204.241:/etc/heartbeat/



After all those steps then I just unmount /srv/data at nod1 reboot the server and then connect to the target from a windows 7 computer, it can connect to the target because the IQN comes up and it says connected but the drive wont show up under disk management, under another virtual machine I setup a regular iSCSI target without drbd and heartbeat and it works so I dont know what is affecting the target and besides that if I reboot node1 then I cant connect anymore to the target, I do know that data replication is working because if I swap servers between each other I, set nod1 as primary and backwards, I can see the data on both nodes, this took me some time to write down so please I need help with this, I dont have money to buy a SAN solution like Equialogic and I have put effort on this project, already have 5 days trying to get this done

---

### Post by Verbeke on 2013-03-29
[FONT=arial]What does your log file say?

First of all, you have to make sure that your iscsi is working correctly.  
[/FONT][FONT=arial]  On newer systems (since Maverick) you have to install some additional packets:
  [/FONT][FONT=arial]This compiles the required module automatically.[/FONT][FONT=arial]
  **$ sudo aptitude install iscsitarget iscsitarget-source iscsitarget-dkms **

  On Lucid you have to compile yourself:
[/FONT]
[FONT=arial][B]  $ sudo aptitude install iscsitarget iscsitarget-source   
[/B]# compile with module-assitant   [B]
$ sudo m-a a-i iscsitarget[/B]


Heartbeat will not work if the service started by heartbeat gives an error. I think in your case that your iscsitarget is giving an error. [/FONT]
[FONT=arial]

[/FONT]
[FONT=arial]
[/FONT]

---

