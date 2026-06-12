---
title: "Waiting for network configuration &amp; Waiting 60 more seconds for network configuration"
date: 2017-01-06
forum: Server Platforms
---

### Post by slkamath on 2017-01-06
Hi,

We are using Ubuntu 14.04.5 Server and every time while restarting it is taking time and showing message stating that 
Waiting for network configuration  
Waiting 60 more seconds for network configuration

I am not getting what mistake I have did. 

Can someone please suggest.

```
/etc/rc.local

/sbin/ifconfig etho:0 xxx.xxx.xx.36 netmask 255.255.255.248 broadcast xxx.xxx.xx.39
/sbin/ifconfig eth1:1 xxx.xxx.0.1 netmask 255.255.255.0 broadcast xxx.xxx.0.255

/etc/network/interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Primary Network Interface INTERNET
auto eth0
iface eth0 inet static
        address xxx.xxx.xx.36
        netmask 255.255.255.248
        network xxx.xxx.xx.32
        broadcast xxx.xxx.xx.39
        dns-nameservers xxx.xxx.xxx.151 xxx.xxx.xxx.152 8.8.8.8
        dns-search laxmielectronics.com
        gateway xxx.xxx.xx.33
        # dns-* options are implemented by the resolvconf package, if installed

# Secondary Network Interface LAN
auto eth1
iface eth1 inet static
        address xxx.xxx.0.1
        netmask 255.255.255.0
        network xxx.xxx.0.0
        broadcast xxx.xxx.0.255
        up ip route add xxx.xxx.1.0/24 via xxx.xxx.0.254
        up ip route add xxx.xxx.0.0/24 via xxx.xxx.0.1
```

Thanks in advance.

Lokesh Kamath

---

### Post by darkod on 2017-01-06
1. Why do you have ifconfig command in /etc/rc.local? The /etc/network/interfaces parameters are enough for networking to be configured correctly. I would disable the commands in rc.local

2. In /etc/network/interfaces you don't need to use the 'network' and 'broadcast' parameters. They are calculated automatically from address and netmask. Using network and broadcast can create issues if you get them wrong, so I prefer to not use them.

---

### Post by slkamath on 2017-01-06
Thanks for your immediate response Darkod.

I changed few things as per your suggestion.
**_/etc/rc.local_**

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#/sbin/ifconfig etho:0 180.151.39.36 netmask 255.255.255.248 broadcast 180.151.39.39
#/sbin/ifconfig eth1:1 192.192.0.1 netmask 255.255.255.0 broadcast 192.192.0.255

shorewall start 

exit 0



_**/etc/network/interfaces**_


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Primary Network Interface INTERNET
auto eth0
iface eth0 inet static
        address xxx.xxx.xx.36
        netmask 255.255.255.248
        #network xxx.xxx.xx.32
        #broadcast xxx.xxx.xx.39
        dns-nameservers xxx.xxx.xxx.151 xxx.xxx.xxx.152 8.8.8.8
        dns-search laxmielectronics.com
        gateway xxx.xxx.xx.33
        # dns-* options are implemented by the resolvconf package, if installed

# Secondary Network Interface LAN
auto eth1
iface eth1 inet static
        address xxx.xxx.0.1
        netmask 255.255.255.0
        #network xxx.xxx.0.0
        #broadcast xxx.xxx.0.255
        up ip route add xxx.xxx.1.0/24 via xxx.xxx.0.254
        up ip route add xxx.xxx.0.0/24 via xxx.xxx.0.1


after this also while booting I am getting 

Waiting for network configuration
Waiting 60 more seconds for network configuration

Lokesh Kamath

---

### Post by slkamath on 2017-01-12
Can anyone help me to solve the issue?

---

### Post by darkod on 2017-01-12
Sorry, I'm out of ideas. It all looks good in the config. Maybe some log messages can give you some info.

Also, do you need the 'shorewall start' in rc.local? Doesn't it start automatically?

---

### Post by slkamath on 2017-02-05
Darko Thanks for your response.

I was out of office from 3 weeks, sorry for delayed response.

**/etc/rc.local**
   Shorewall is already running

Still it is not starting automatically. :(


**> cat /var/log/boot.log**
 * Starting Read required files in advance[122G[ OK ]
 * Stopping Send an event to indicate plymouth is up[122G[ OK ]
 * Starting Mount filesystems on boot[122G[ OK ]
 * Starting Fix-up sensitive /proc filesystem entries[122G[ OK ]
 * Starting Populate /dev filesystem[122G[ OK ]
 * Starting Populate and link to /run filesystem[122G[ OK ]
 * Stopping Fix-up sensitive /proc filesystem entries[122G[ OK ]
 * Stopping Populate /dev filesystem[122G[ OK ]
 * Stopping Populate and link to /run filesystem[122G[ OK ]
 * Stopping Track if upstart is running in a container[122G[ OK ]
 * Starting Initialize or finalize resolvconf[122G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[122G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[122G[ OK ]
 * Starting Bridge udev events into upstart[122G[ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted[122G[ OK ]
 * Starting Signal sysvinit that the rootfs is mounted[122G[ OK ]
 * Starting device node and kernel event manager[122G[ OK ]
 * Starting load modules from /etc/modules[122G[ OK ]
 * Starting cold plug devices[122G[ OK ]
 * Starting log initial device creation[122G[ OK ]
 * Starting Clean /tmp directory[122G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[122G[ OK ]
 * Stopping load modules from /etc/modules[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Stopping Clean /tmp directory[122G[ OK ]
 * Starting Signal sysvinit that local filesystems are mounted[122G[ OK ]
 * Starting flush early job output to logs[122G[ OK ]
 * Stopping Mount filesystems on boot[122G[ OK ]
 * Stopping flush early job output to logs[122G[ OK ]
 * Starting D-Bus system message bus[122G[ OK ]
 * Starting Mount network filesystems[122G[ OK ]
 * Starting SMB/CIFS File Server[122G[ OK ]
 * Starting Failsafe Boot Delay[122G[ OK ]
 * Stopping Mount network filesystems[122G[ OK ]
 * Starting Bridge file events into upstart[122G[ OK ]
 * Starting Bridge socket events into upstart[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting SystemD login management service[122G[ OK ]
 * Starting system logging daemon[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting Mount network filesystems[122G[ OK ]
 * Starting Samba Winbind[122G[ OK ]
 * Stopping Mount network filesystems[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[122G[ OK ]
 * Starting NetBIOS name server[122G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[122G[[31mfail[39;49m]
 * Stopping cold plug devices[122G[ OK ]
 * Stopping log initial device creation[122G[ OK ]
 * Starting load fallback graphics devices[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Stopping load fallback graphics devices[122G[ OK ]
 * Starting set console font[122G[ OK ]
 * Stopping set console font[122G[ OK ]
 * Starting userspace bootsplash[122G[ OK ]
 * Starting Send an event to indicate plymouth is up[122G[ OK ]
 * Stopping Send an event to indicate plymouth is up[122G[ OK ]
 * Starting configure virtual network devices[122G[ OK ]
 * Stopping userspace bootsplash[122G[ OK ]
 * Stopping Failsafe Boot Delay[122G[ OK ]
 * Starting System V initialisation compatibility[122G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Skipping profile in /etc/apparmor.d/disable: usr.sbin.squid3
 * Starting AppArmor profiles       [128G 
[122G[ OK ]
Starting "Shorewall firewall": done.
 * Stopping System V initialisation compatibility[122G[ OK ]
 * Starting System V runlevel compatibility[122G[ OK ]
 * Starting deferred execution scheduler[122G[ OK ]
 * Starting regular background program processing daemon[122G[ OK ]
 * Starting automatic crash report generation[122G[ OK ]
 * Starting ACPI daemon[122G[ OK ]
 * Starting HTTP proxy-cache[122G[ OK ]
To enable c-icap, edit /etc/default/c-icap and set START=yes
 * Starting OpenSSH server[122G[ OK ]
 * Starting CPU interrupts balancing daemon[122G[ OK ]
 * Starting MySQL Server[122G[ OK ]
 * Starting ClamAV daemon clamd       [128G 
[122G[ OK ]
 * Starting ClamAV virus database updater freshclam       [128G 
[122G[ OK ]
 * Starting DansGuardian dansguardian       [128G 
[122G[ OK ]
 * Starting ftp server proftpd       [128G 
[122G[ OK ]
 * Restoring resolver state...       [128G 
[122G[ OK ]
 * 
   Shorewall is already running
Starting "Shorewall firewall": done.
 * Stopping System V runlevel compatibility[122G[ OK ]

Lokesh Kamath

---

