---
title: "How to Detect Duplicate IP Address in LAN connected to Ubuntu ?"
date: 2016-06-04
forum: Server Platforms
---

### Post by soamz on 2016-06-04
How to Detect Duplicate IP Address in LAN connected to Ubuntu ?

I have like 254 Devices with private IP 10.10.12.xx and 10.10.14.xx

Since last few days, the ping to many devices break, so I guess there is a loop or duplicate IP somewhere in the network. 
How to find it out ?

---

### Post by SeijiSensei on 2016-06-04
I'd start by running "arp -vn" on the server which will report back the Ethernet addresses and associated IP addresses for all the nodes it has seen.

```

$ arp -vn
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.100.5            ether   30:05:5c:43:bc:b3   C                     eth0
192.168.100.1            ether   b0:c7:45:6d:5d:c1   C                     eth0
192.168.100.100          ether   00:11:11:30:33:c3   C                     eth0

```

---

### Post by nerdtron on 2016-06-05
You can use arp-scan to scan the network which will show the IP address and MAC address mapping of devices on the network.

Install it by:
```
sudo apt-get install arp-scan
```

Examples on how to use it on this link: [https://www.blackmoreops.com/2015/12/31/use-arp-scan-to-find-hidden-devices-in-your-network/](https://www.blackmoreops.com/2015/12/31/use-arp-scan-to-find-hidden-devices-in-your-network/)

---

### Post by CharlesA on 2016-06-05
I was going to suggest doing a quick ping scan via nmap, but arp-scan would likely accomplish the same thing.

---

### Post by The Cog on 2016-06-05
I didn't know about arp-scan. That's sweet and fast. 
If two or more devices with the same address answer, then it prints two responses. To spot that you will need to pipe the output through sort to get then next to each other as a minimum. 

This line prints the duplicate address on my home LAN:
```
sudo arp-scan 192.168.0.0/24 | cut -f1 | sort | uniq -d
```
It scans my subnet, extracts and sorts the IP addresses into order and prints any repeats.

P.S.
arp-scan doesn't check its own address, so the above won't work if you do it from a PC which has a duplicate.

---

### Post by soamz on 2016-06-05
> **The Cog said:**
> I didn't know about arp-scan. That's sweet and fast. 
If two or more devices with the same address answer, then it prints two responses. To spot that you will need to pipe the output through sort to get then next to each other as a minimum. 

This line prints the duplicate address on my home LAN:
```
sudo arp-scan 192.168.0.0/24 | cut -f1 | sort | uniq -d
```
It scans my subnet, extracts and sorts the IP addresses into order and prints any repeats.

P.S.
arp-scan doesn't check its own address, so the above won't work if you do it from a PC which has a duplicate.


Awesome, this is what I needed.
Let me run and see.

No output after running, arp-scan 10.10.14.0/24 | cut -f1 | sort | uniq -d

---

