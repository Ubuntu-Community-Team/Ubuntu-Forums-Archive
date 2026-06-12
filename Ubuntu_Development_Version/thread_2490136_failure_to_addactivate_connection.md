---
title: "failure to add/activate connection"
date: 2023-08-23
forum: Ubuntu Development Version
---

### Post by rolfbruge on 2023-08-23
After update intermittent message when clicking desired wifi connection: failure to add/activate connection....message recipient disconnected from message bus without replying

Distributor ID:    Ubuntu
Description:    Ubuntu Mantic Minotaur (development branch)
Release:    23.10
Codename:    mantic

Anyone experiencing this issue?

---

### Post by jeremy31 on 2023-08-23
Moved to Ubuntu Dev Version, see the wireless script link in my signature and post results

---

### Post by rolfbruge on 2023-08-25
Only reverting to lunar versions of packages appears to have resolved this issue.

libnm0:amd64                                  
wpasupplicant                                          
libnma0:amd64                                     
networkd-dispatcher                     
netbase                                                                               
network-manager                                                     
network-manager-gnome                                        
network-manager-pptp    

Attempting to upgrade involving:

netplan-generator                                       
netplan.io            
 
appears to produce a failure to write to /etc/netplan with corresponding message "failure to add/activate connection".

grep: /etc/netplan/90-NM-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.yaml: Permission denied

---

### Post by corradoventu on 2023-08-28
I had a similar problem, solved by installing iwd [https://discourse.ubuntu.com/t/call-for-testing-improved-wifi-via-iwd/17795](https://discourse.ubuntu.com/t/call-for-testing-improved-wifi-via-iwd/17795)

---

### Post by elguaposghost on 2023-08-29
Has anyone reported the bug?

---

### Post by rolfbruge on 2023-09-10
Issue was reported here with recent revision as of September 10, 2023:
[https://bugs.launchpad.net/ubuntu/+source/libasyncns/+bug/2031186](https://bugs.launchpad.net/ubuntu/+source/libasyncns/+bug/2031186)

Issue persists with failure to migrate connections to netplan during installation. All connections fail to migrate and display terminal message referencing message recipient was disconnected from message bus without replying.

Issue persists as of September 10, 2023 with the following packages:

ii netbase 6.4 all Basic TCP/IP networking system
ii netplan-generator 0.107-4 amd64 YAML network configuration abstraction systemd-generator
ii netplan.io 0.107-4 amd64 YAML network configuration abstraction for various backends
ii network-manager 1.44.0-1ubuntu2 amd64 network management framework (daemon and userspace tools)
hi network-manager-gnome 1.30.0-2ubuntu1 amd64 network management framework (GNOME frontend)
hi network-manager-pptp 1.2.12-1 amd64 network management framework (PPTP plugin core)
hi networkd-dispatcher 2.2.3-1 all Dispatcher service for systemd-networkd connection status changes
ii openvpn 2.6.5-0ubuntu1 amd64 virtual private network daemon
ii python-netifaces 0.10.4-1ubuntu6 amd64 portable network interface information - Python 2.x
ii python3-netifaces:amd64 0.11.0-2build1 amd64 portable network interface information - Python 3.x
ii python3-netplan 0.107-4 amd64 YAML network configuration abstraction Python bindings
ii dirmngr 2.2.40-1.1ubuntu1 amd64 GNU privacy guard - network certificate management service
ii glib-networking:amd64 2.76.1-2 amd64 network-related giomodules for GLib
ii glib-networking:i386 2.76.1-2 i386 network-related giomodules for GLib
ii glib-networking-common 2.76.1-2 all network-related giomodules for GLib - data files
ii glib-networking-services 2.76.1-2 amd64 network-related giomodules for GLib - D-Bus services

---

