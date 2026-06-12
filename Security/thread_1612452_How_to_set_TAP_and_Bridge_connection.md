---
title: "How to set TAP and Bridge connection?"
date: 2010-11-03
forum: Security
---

### Post by seekerzf on 2010-11-03
Hi, guys
My host is ubuntu 9.04 and the guest is winxp sp3. I need to use QEMU to monitor the network communication for security researches. But I failed to establish the connection between the host and the guest.
 
To build a TAP connection, I input commands as the following:
```
 
sudo tunctl -t tap0 -u hdzf
sudo ifconfig tap0 192.168.10.1 netmask 255.255.255.0 broadcast 192.168.10.255
sudo qemu winxp.img -net nic, vlan=0 -net tap vlan=0, ifname=tap0

```
After the guest os booting up, I modifed the ip config of winxp as the following:
Guest IPCONFIG
```
 
ip: 192.168.10.2
netmask:255.255.255.0
Gateway:192.168.10.1
DNS: host's ip address

```
 
However, the host cannot ping the guest, and neither the guest ping the host.
 
How should I establish the TAP and Bridge connection in the QEMU?
Thank you very much!
 
Cheers!
Fan Zhang

---

### Post by seekerzf on 2010-11-03
> **seekerzf said:**
> Hi, guys
My host is ubuntu 9.04 and the guest is winxp sp3. I need to use QEMU to monitor the network communication for security researches. But I failed to establish the connection between the host and the guest.
 
To build a TAP connection, I input commands as the following:
```
 
sudo tunctl -t tap0 -u hdzf
sudo ifconfig tap0 192.168.10.1 netmask 255.255.255.0 broadcast 192.168.10.255
sudo qemu winxp.img -net nic, vlan=0 -net tap vlan=0, ifname=tap0

```
After the guest os booting up, I modifed the ip config of winxp as the following:
Guest IPCONFIG
```
 
ip: 192.168.10.2
netmask:255.255.255.0
Gateway:192.168.10.1
DNS: host's ip address

```
 
However, the host cannot ping the guest, and neither the guest ping the host.
 
How should I establish the TAP and Bridge connection in the QEMU?
Thank you very much!
 
Cheers!
Fan Zhang
 
 
 
 
I have solved the problem that I cannot use the TAP connection.
In fact, everything is ok except that the tap0 is created for the user named "hdzf" with the following command:
```
sudo tunctl -t tap0 -u hdzf
```
However, I started the guest OS with the command
```
sudo qemu winxp.img -net ......
```
 
Thus the device tap0 cannot send the ping package from the guest to the host, because the tap0 belongs to user hdzf, not user root.
 
Cheers!
Fan Zhang

---

