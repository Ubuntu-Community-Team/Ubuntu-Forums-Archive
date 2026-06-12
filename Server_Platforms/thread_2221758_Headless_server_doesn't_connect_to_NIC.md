---
title: "Headless server doesn't connect to NIC"
date: 2014-05-03
forum: Server Platforms
---

### Post by drfox on 2014-05-03
I just upgraded from Precise LTS to Trusty LTS. 
Now, unless i attach a monitor and keyboard and login, the server won't log into my network because eth0 fails.
I get this message as the system loads: "no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory"
And then I cannot ping the server. I cannot SSH into it. If I attach a monitor and keyboard and log in as a user and when I issue the command: "lshw -C network", I only get the configuration of l0
If I "sudo ifup eth0 restart", then I get the "no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory" warning, but eth0 does start.

Is there a workaround for this problem?

---

### Post by Gyokuro on 2014-05-03
Which NIC is it?? You could try to manually load the NIC module:

sudo modeprobe nicdriver (e1000e is for intel GB NIC)

sudo ifconfig eth0 up && dhclient eth0 (to bring up the NIC device and get an IP via DHCP)

ping [www.ubuntu.com]("http://www.ubuntu.com")

if it fails please post the errors.

- HTH

---

### Post by Doug S on 2014-05-03
I think the error message might be unrelated, and due to samba. See [this]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186").

---

### Post by Gyokuro on 2014-05-03
Ah ok - thanks - comment 14 have a workaround: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186/comments/14](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186/comments/14)

---

### Post by drfox on 2014-05-03
> **Gyokuro said:**
> Ah ok - thanks - comment 14 have a workaround: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186/comments/14](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186/comments/14)
Thanks, running "pam-auth-update" and remove "SMB password synchronization" solved the memory leak error, BUT still, in order to get the eth0 (which is an embedded chip on the MB) to work, I have to log in and issue the command "sudo ifup eth0 start".
This is a headless server and should automatically start the network interfaces.

---

### Post by Gyokuro on 2014-05-04
Hi 

Do you have already checked/compared the setting of /etc/network/interfaces as I have already checked bug reports of ifup/ifdown problems but nothing interesting as it seems you are at the moment the only one with this problem. Another try could be that you make a clean install of a 14.04 server install in a VM and compare the usual places like /etc/network/interfaces as I think it's only a small bug in 14.04 which do not bring up your NIC at boot time (either an upstart problem or in the ifup/ifdown scripts).

---

### Post by drfox on 2014-05-04
> **Gyokuro said:**
> Hi 

Do you have already checked/compared the setting of /etc/network/interfaces as I have already checked bug reports of ifup/ifdown problems but nothing interesting as it seems you are at the moment the only one with this problem. Another try could be that you make a clean install of a 14.04 server install in a VM and compare the usual places like /etc/network/interfaces as I think it's only a small bug in 14.04 which do not bring up your NIC at boot time (either an upstart problem or in the ifup/ifdown scripts).

This looks OK, doesn't it?
::::::::::::::
interfaces
::::::::::::::
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
 auto lo
 iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.15.15
        netmask 255.255.255.0
 #      network 192.168.15.0
 #      broadcast 192.168.15.255
        gateway 192.168.15.254
 #      dns-nameservers 8.8.8.8

# This is an autoconfigured IPv6 interface
# iface eth0 inet6 auto

---

### Post by Iowan on 2014-05-04
Add eth0 to the auto line, or add an auto line to eth0 definition. 
```
 auto lo [COLOR="#FF0000"]eth0[/COLOR]
```
or
```

# The primary network interface
[COLOR="#FF0000"]auto eth0[/COLOR]
iface eth0 inet static
```
(not both)

---

### Post by Gyokuro on 2014-05-04
Hi 

As notes by Iowan your lines should look like following:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
address 192.168.15.15
        netmask 255.255.255.0
 #      network 192.168.15.0
 #      broadcast 192.168.15.255
        gateway 192.168.15.254
 #      dns-nameservers 8.8.8.8

# This is an autoconfigured IPv6 interface
# iface eth0 inet6 auto

---

### Post by drfox on 2014-05-04
> **Iowan said:**
> Add eth0 to the auto line, or add an auto line to eth0 definition. 
```
 auto lo [COLOR="#FF0000"]eth0[/COLOR]
``` 

Worked like a charm. Can't believe I screwed that up. Thank you so much!

---

