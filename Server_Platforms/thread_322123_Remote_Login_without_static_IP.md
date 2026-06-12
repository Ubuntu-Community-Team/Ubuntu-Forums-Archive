---
title: "Remote Login without static IP"
date: 2006-12-20
forum: Server Platforms
---

### Post by foyf on 2006-12-20
I recently installed Edgy Eft Server onto an old PC. The installation went smoothly and I logged in locally. I plan to put this server into a closet and use it for printer sharing, data backups, music sharing, and possible more. Because it is going to be in a closet I won't be able to use it with a keyboard/monitor. So I want to be able to login remotely.

I downloaded and installed the OpenSSH client and server and they seam to be running.
```
ps -aef | grep ssh
```
Reveals that root is running a process at /usr/sbin/sshd. I have successfully logged in remotely via the Terminal on my mac. 
```
ssh user@192.168.1.104
```
The problem is that my current internet configuration uses DHCP and that IP of the server (192.168.1.104) will be something different tomorrow.

The thing is on my Mac (running Mac OS X 10.4) in the Sharing tab of System Preferences I have Personal Web Sharing turned on. So from my other Mac, but not from the server, I can ssh my first mac. 
```
ssh user@subnet.local
```
I can do that no matter the IP of my first mac.

Is there anything similar to that I can do for the server? Should I look in to having static IP's for the network? I'm not new to Unix/Linux but I am new to Ubuntu and servers in general.

Thanks in advance!

---

### Post by linuchsan on 2006-12-20
Give the server a static ip address, I don't think that you have a gui installed, so try man interfaces

---

### Post by foyf on 2006-12-20
There is no GUI installed. What man interfaces do you mean? The router is the DHCP server so I think I would have to go through it. Well I look into it, thanks for your help.

---

### Post by CyberX on 2006-12-20
Hi.
You can set a static IP address in /etc/network/interfaces:

```
nano /etc/network/interfaces
```

This is my file:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.8.111
        netmask 255.255.255.0
        network 192.168.8.0
        broadcast 192.168.8.255
        gateway 192.168.8.1

```

where 'address' is my server IP address, 'gateway' is my ADSL Router IP address (which also works as DHCP server but only for addresses higher than *.*.*.100 so there is no conflict)

---

### Post by Iowan on 2006-12-20
A server should probably have a static address anyway (or a static lease based on MAC address) but:
[http://ubuntuforums.org/showthread.php?t=247563](http://ubuntuforums.org/showthread.php?t=247563)

---

