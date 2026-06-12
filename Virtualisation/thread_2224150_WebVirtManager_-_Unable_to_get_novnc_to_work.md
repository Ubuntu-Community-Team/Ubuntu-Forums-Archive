---
title: "WebVirtManager - Unable to get novnc to work"
date: 2014-05-14
forum: Virtualisation
---

### Post by nick112 on 2014-05-14
I am running a virtual server (KVM) with webvirtmanager. When I startup my virtual machine and I try to acceess to console via noNVC, it begins a handshake process, but hangs. The clients web browser just says "Starting VNC handshake" at the top in a yellow bar and does nothing. 

I admin I am a complete noob when it comes to setting up noVNC. I have the contents of the log and the nova.conf file below. Any help is greatly appreciated!!

I am running Ubuntu 14.04 as my base OS and I installed novnc and then nova-novncproxy. The instructions I used to install webvirtmanager are in the below link. They may be outdated, as they just advise to install novnc.
[https://github.com/retspen/webvirtmgr/wiki/Install-WebVirtMgr](https://github.com/retspen/webvirtmgr/wiki/Install-WebVirtMgr)

The errors I am seeing in my nova-novncproxy.log are as follows:
No handlers could be found for logger "oslo.messaging._drivers.impl_rabbit"
 10: 192.168.1.106: new handler Process
 10: 192.168.1.106: Plain non-SSL (ws://) WebSocket connection
 10: 192.168.1.106: Version hybi-13, base64: 'False'
No handlers could be found for logger "oslo.messaging._drivers.impl_rabbit"


nova.conf file ( I have not modified this file, it contains the default values).

[DEFAULT]
dhcpbridge_flagfile=/etc/nova/nova.conf
dhcpbridge=/usr/bin/nova-dhcpbridge
logdir=/var/log/nova
state_path=/var/lib/nova
lock_path=/var/lock/nova
force_dhcp_release=True
iscsi_helper=tgtadm
libvirt_use_virtio_for_bridges=True
connection_type=libvirt
root_helper=sudo nova-rootwrap /etc/nova/rootwrap.conf
verbose=True
ec2_private_dns_show_ip=True
api_paste_config=/etc/nova/api-paste.ini
volumes_path=/var/lib/nova/volumes
enabled_apis=ec2,osapi_compute,metadata

---

