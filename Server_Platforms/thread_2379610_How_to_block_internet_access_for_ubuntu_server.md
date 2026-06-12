---
title: "How to block internet access for ubuntu server?"
date: 2017-12-07
forum: Server Platforms
---

### Post by bern1 on 2017-12-07
Hi, 
I have ubuntu server (17.10) 086_x64 installed (as host), VirtualBox software and IPFire 086_x64 (running as Virtual Machine/guest).
One of host's/ubuntu ethernet network interface is bridged to IPFire RED/WAN. See my clumsy diagram;)
[IMG]http://drive.google.com/uc?export=view&id=1SPsdLeLqOeRstF2PvQ9JIZpCjCdk7EQi[/IMG]
In this configuration internet access is available for IPFfire and  ubuntu. Ubuntu is not protected and exposed to dangerous actions from  the internet.
I would like to block internet traffic for ubuntu completely and pass it exclusively to IPFire.
Ubuntu (with installed servers) would be connected separately to LAN (e.g. using additional  network interface to ethernet switch connected to IPFire's LAN).
Please advice how could I efficiently and effectively block internet traffic for ubuntu host?
Is it possible to block only ubuntu MAC address for ubuntu-ipfire bridge? If so how?
I've tried to use iptables:
```
sudo iptables -A INPUT -p all -m mac --mac-source 70:85:c2:3d:6b:ba -j DROP
sudo iptables -A FORWARD -p all -m mac --mac-source 70:85:c2:3d:6b:ba -j DROP
```
but this doesn't block and still can access the internet from ubuntu. 
The IPTABLES rules after the change are:
```
ela@akacja:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere             MAC 70:85:C2:3D:6B:BA

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere             MAC 70:85:C2:3D:6B:BA

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
But it doesn't work. I have no expirience with iptables. 
Maybe there are other options?
Regards,

---

### Post by Doug S on 2017-12-07
From your other thread, it appears as though 70:85:c2:3d:6b:ba is the MAC for the interface in the server itself.
You need to use the MAC for your provider, according to your diagram. However, I have a bit of trouble to follow your diagram, and wonder if that is what you really want to do.

You should be able to get the MAC of your provider by looking at your arp table (just type "arp').

---

### Post by darkod on 2017-12-07
Before getting into complex details of firewalling, I think it's worth clearing up something. According to your diagram you get your internet on 192.168.15.23. That's a private subnet and is not routable on the internet. No one can "come in" that way...

Does the ISP forward all traffic to you on that private IP? If yes, and assuming they have more customers, how do they route the traffic to others if everything is going to you?

How experienced are you with these things, in general at least? Do you understand that communication in private LAN 192.168.0.0/16 is not actually reachable and public on the internet, even though the machines do have internet access?

You might actually be protected behind ISP router, which I believe is probably the case, so all of this might be for nothing...

---

### Post by bern1 on 2017-12-07
Thanks guys for prompt replay.
and sorry for my inaccurate diagram...:oops:
> **Doug S said:**
> From your other thread, it appears as though  70:85:c2:3d:6b:ba is the MAC for the interface in the server itself.
You need to use the MAC for your provider, according to your diagram.  However, I have a bit of trouble to follow your diagram, and wonder if  that is what you really want to do.
I would like block internet traffic for ubuntu server on enp1s0 but at the same time passing this traffic to VM (IPFire).
> **Doug S said:**
> You should be able to get the MAC of your provider by looking at your arp table (just type "arp').
arp command:
```
ela@akacja:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
gateway                  ether   00:27:22:35:40:df   C                     enp1s0
```
> **darkod said:**
> Before getting into complex details of firewalling, I think it's worth clearing up something. According to your diagram you get your internet on 192.168.15.23. That's a private subnet and is not routable on the internet. No one can "come in" that way...
I receive 192.168.15.23 from ISP but from outside my IP address is seen as public address 46.xxx.xxx.xxx. 
Configuring IPFire I set static address: 192.168.15.23 and can access my router/firewall (IPFire) from outside/internet on 46.xxx.xxx.xxx using SSH (of course after opening the appropriate port)

---

### Post by Doug S on 2017-12-07
Well, things just don't make sense to me. I have looked at your diagram and all the stuff on your other thread.
In the end, I suspect you will want to achieve your objective via the Ubuntu server IP address rather than MAC addresses. I.E. drop packets to or from the Ubuntu server IP address and allow packets to or from the bridged IP address for "[COLOR="#FF0000"]WAN[/COLOR]".

---

### Post by SeijiSensei on 2017-12-07
Can you even see the VM from the Internet?  It has no public addresses.   Are you forwarding traffic from outside the Internet back to the VM on specific ports?  

Install the program nmap on a machine outside your home.  Perhaps you have a laptop you can take to some external location.  Use nmap to scan the Internet-facing address of your router.  What does it see?

Do you understand that traffic for 192.168.0.0/16 is not routed over the Internet but reserved for private networks?  Your ISP's router uses something called "masquerading" to handle outbound traffic.  Most routers block all inbound traffic.  Where do you see the risk?

If you just want to block **outbound** traffic from the server the Internet (why?), you can use these iptables rules
```

# allow traffic within my local network
/sbin/iptables -A OUTPUT -d 192.168.0.0/24 -j ACCEPT
# block all other outbound traffic
/sbin/iptables -A OUTPUT -j DROP

```

---

### Post by bern1 on 2017-12-08
> **Doug S said:**
>  In the end, I suspect you will want to achieve your objective via the Ubuntu server IP address rather than MAC addresses. I.E. drop packets to or from the Ubuntu server IP address and allow packets to or from the bridged IP address for "[COLOR=#FF0000]WAN[/COLOR]". If I can my objective is to block internet access for Ubuntu server on interface enp1s0 no matter what methods used (MAC, IP, etc) > **SeijiSensei said:**
> Can you even see the VM from the Internet?   It has no public addresses.   Are you forwarding traffic from outside  the Internet back to the VM on specific ports? Yes I see VM from the internet. It has public address 46.xxx.xxx.xxx. I do not use forwarding.  > **SeijiSensei said:**
> Install the program nmap on a machine outside your home.  Perhaps you  have a laptop you can take to some external location.  Use nmap to scan  the Internet-facing address of your router.  What does it see? My router/firewall is IPFire running on Ubuntu server as VM. As I expected I see opened (by myself) port 222: 
```
Starting Nmap 7.60 ( https://nmap.org ) at 2017-12-08 11:55
NSE: Loaded 146 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 11:55
Completed NSE at 11:55, 0.00s elapsed
Initiating NSE at 11:55
Completed NSE at 11:55, 0.00s elapsed
Initiating Ping Scan at 11:55
Scanning 46.xxx.xxx.xxx [4 ports]
Completed Ping Scan at 11:56, 3.92s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:56
Completed Parallel DNS resolution of 1 host. at 11:56, 6.08s elapsed
Initiating SYN Stealth Scan at 11:56
Scanning host-46-xxx-xxx-xxx.aaabbbccc.net (46.xxx.xxx.xxx) [1000 ports]
SYN Stealth Scan Timing: About 13.50% done; ETC: 12:00 (0:03:19 remaining)
Discovered open port 222/tcp on 46.xxx.xxx.xxx
SYN Stealth Scan Timing: About 28.55% done; ETC: 11:59 (0:02:33 remaining)
Completed SYN Stealth Scan at 11:57, 72.98s elapsed (1000 total ports)
Initiating Service scan at 11:57
Scanning 1 service on host-46-xxx-xxx-xxx.aaabbbccc.net (46.xxx.xxx.xxx)
Completed Service scan at 11:57, 0.19s elapsed (1 service on 1 host)
Initiating OS detection (try #1) against host-46-xxx-xxx-xxx.aaabbbccc.net (46.xxx.xxx.xxx)
Retrying OS detection (try #2) against host-46-xxx-xxx-xxx.aaabbbccc.net (46.xxx.xxx.xxx)
Initiating Traceroute at 11:57
Completed Traceroute at 11:57, 3.04s elapsed
Initiating Parallel DNS resolution of 9 hosts. at 11:57
Completed Parallel DNS resolution of 9 hosts. at 11:57, 5.63s elapsed
NSE: Script scanning 46.xxx.xxx.xxx.
Initiating NSE at 11:57
Completed NSE at 11:57, 4.73s elapsed
Initiating NSE at 11:57
Completed NSE at 11:57, 0.00s elapsed
Nmap scan report for host-46-xxx-xxx-xxx.aaabbbccc.net (46.xxx.xxx.xxx)
Host is up (0.090s latency).
Not shown: 999 filtered ports
PORT    STATE SERVICE VERSION
222/tcp open  ssh     OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey: 
|   2048 3d:47:de:xx:dc:8c:3b:3a:08:3f:63:xx:ad:bf:0a:94 (RSA)
|   256 5f:25:05:xx:c9:6e:4e:e1:e6:62:35:4f:9a:11:cf:fd (ECDSA)
|_  256 2d:4e:21:51:31:7e:xx:11:c9:c4:28:xx:6c:74:64:50 (EdDSA)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
OS fingerprint not ideal because: Missing a closed TCP port so results incomplete
No OS matches for host
Uptime guess: 0.003 days (since Fri Dec 08 11:53:06 2017)
Network Distance: 10 hops
TCP Sequence Prediction: Difficulty=248 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE (using port 222/tcp)

HOP RTT       ADDRESS
1   0.00 ms   192.168.42.129
.
.
.
.
.
.
.
.
10  156.00 ms host-46-xxx-xxx-xxx.aaabbbccc.net (46.xxx.xxx.xxx)
NSE: Script Post-scanning.
Initiating NSE at 11:57
Completed NSE at 11:57, 0.02s elapsed
Initiating NSE at 11:57
Completed NSE at 11:57, 0.00s elapsed
Read data files from: C:\Program Files (x86)\Nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 125.24 seconds
           Raw packets sent: 2086 (95.276KB) | Rcvd: 83 (4.824KB)
```
> **SeijiSensei said:**
> Do you understand that traffic for 192.168.0.0/16 is not routed over the  Internet but reserved for private networks?   > **SeijiSensei said:**
> Most  routers block all inbound traffic.  Where do you see the risk?
My ISP do not provide the network protection so I have to protect my net myself. To do that  I installed firewall/router IPFire. For me direct connect ubuntu to internet is dangerous. I would like that ubuntu be a LAN host (after firewall and NAT) and serve other hosts.

---

### Post by bern1 on 2017-12-08
Hi guys, 
Problem solved :)
I've changed the content of netplan file for interface enp1s0 from:
```
network:
    version: 2
    renderer: networkd
    ethernets:
        enp1s0:
            dhcp4: true
```
to:
```
network:
    version: 2
    renderer: networkd
    ethernets:
        enp1s0:
            addresses:
                - 192.168.15.23/24
            dhcp4: no
```
and all works fine. 
I set static address on IPFire router (VM) but forget switch dhcp to static on Ubuntu server. 
Anyway after the change Ubuntu machine is now LAN host of VM and has not direct connection to the Internet
It is interesting because for this I do not need external ethernet switch...
I will investigate this in free time..
Thanks for your posts. :)

---

