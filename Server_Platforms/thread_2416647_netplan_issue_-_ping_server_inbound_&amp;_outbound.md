---
title: "netplan issue? - ping server inbound &amp; outbound not working"
date: 2019-04-12
forum: Server Platforms
---

### Post by aljames2 on 2019-04-12
New 18.04.2 server install.  Probably something simple.  Netplan file here:

```
network:
version: 2
renderer: networkd
ethernets:
  enp0s3:
    addresses: [[COLOR=red]192.168.104.245/24[/COLOR]]
    gateway4: [COLOR=red]192.168.104.1
[/COLOR]    nameservers:
      addresses: [[COLOR=red]192.168.104.1[/COLOR]]
```

I have a Windows 10 desktop on same LAN subnet as the Ubuntu server.  Both connected to a switch, which is connected to my pfSense router/firewall's interface.  pfSense is configured in Unbound DNS resolver mode to handle all DNS requests.  I don't "think" it's a router/firewall problem.  The Windows machine can ping external and can ping the interface/gateway, but times out when pinging the Ubuntu IP.  The Ubuntu cannot ping anything...except sometimes it does ping outbound but only after rebooting the server.

after ```
ifconfig
```
only the Loopback info is returning.  The server IP, mask, MAC, etc. section is not showing.

Could it be my nameserver address?  I know normally you would have 2 internals, & 2 external addresses but in my case with the router handling the DNS I figured that I only needed to point the DNS to the interface gateway?

---

### Post by aljames2 on 2019-04-13
UPDATE:

After ```
shutdown -P now
```

From a cold boot, the server has no network connection.  But then after ```
reboot now
``` it connects and everything works.

I guess the question now is why doesn't the server connect to the network from a cold boot.

---

### Post by aljames2 on 2019-04-13
LATEST:

This is not a dual boot system.  Ubuntu Server only.

I've narrowed it down to the server box itself.  An issue in the boot priority order.  The only time the server boots with a connection is when UEFI OS is the default boot.

both efibootmgr & my UEFI Bios show this:

BootCurrent:  0000
BootOrder:  0000.0002,0003
Boot0000* Ubuntu
Boot0002* UEFI OS
Boot0003* Ubuntu

If I change the boot order it lasts for 1 boot-up and works, but upon shutdown and restart the system reverts back to this boot order which doesn't work.  Ive tried to reset the boot order using both efibootmgr & the firmware UEFI bios but neither sticks.  I need the system to boot up using UEFI OS in order for the network connection to initialize.

NOTE: In the above boot order, you might be wondering what happened to 0001.  I had 3 Ubuntu's in the list but removed one using ```
efibootmgr -b 4 -B
```

I tried to remove all 3 leaving only UEFI OS boot option but that didn't stick.  So this is what I'm left with.

---

### Post by aljames2 on 2019-04-13
POSSIBLE FIX..

As mentioned at start my current netplan is this:
```
network:
version: 2
renderer: networkd
ethernets:
  enp0s3:
    addresses: [[COLOR=red]192.168.104.245/24[/COLOR]]
    gateway4: [COLOR=red]192.168.104.1
[/COLOR]    nameservers:
      addresses: [[COLOR=red]192.168.104.1[/COLOR]]
```
I may have discovered something but would like a comment if the following could possibly work?

I have only 1 Intel NIC port on PCIe card.  I have an onboard Realtek port but disabled.
As noted above my ethernet is enp0s3.

I ran this command: ```
sudo lshw -C network
```
and found that on cold boot, the ethernet port is named differently as enp5s0.

Not sure why the the port would be initialized with different names depending on how I boot.  I'm guessing it has something to do with bootloading because there are grubx64 & shimx64 contained in my folder ```
/boot/efi/EFI/Ubuntu
``` and there is BOOTX64 in my folder ```
/boot/efi/EFI/BOOT
```

My thought to fix is edit my netplan to account for the other name given to the same NIC port.  My NIC port has 2 names, depending on whether I cold boot or warm reboot.  I propose this: ...could this work?

```
network:
version: 2
renderer: networkd
ethernets:
  enp0s3:
    addresses: [[COLOR=red]192.168.104.245/24[/COLOR]]
    gateway4: [COLOR=red]192.168.104.1
[/COLOR]    nameservers:
      addresses: [[COLOR=red]192.168.104.1[/COLOR]]
  enp5s0:
    addresses: [[COLOR=red]192.168.104.245/24[/COLOR]]
    gateway4: [COLOR=red]192.168.104.1
[/COLOR]    nameservers:
      addresses: [[COLOR=red]192.168.104.1[/COLOR]]
```

---

### Post by aljames2 on 2019-04-14
SOLVED:

The netplan can be configured to match a specific interface name to a MAC address.  This way the interface is sure to initialize using netplan settings no matter how bootup processes might try to rename your NIC interface.

```
network:
version: 2
renderer: networkd
ethernets:
  enp0s3:
    match:
      macaddress: [COLOR=#ff0000]00:11:22:33:44:55[/COLOR]
    set-name: enp0s3
    addresses: [[COLOR=red]192.168.104.245/24[/COLOR]]
    gateway4: [COLOR=red]192.168.104.1
[/COLOR]    nameservers:
      addresses: [[COLOR=red]192.168.104.1[/COLOR]]

```

Ubuntu Server Guide from here was a big help:  [https://help.ubuntu.com/lts/serverguide/network-configuration.html.en](https://help.ubuntu.com/lts/serverguide/network-configuration.html.en)

Hopefully, my pain will be someone else's gain on this issue. :D

---

