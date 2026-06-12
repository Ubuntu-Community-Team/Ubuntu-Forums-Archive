---
title: "Zenity GUI to start SSH VPN"
date: 2008-11-05
forum: Security
---

### Post by benanzo on 2008-11-05
Hello,

I've set up a script to start/stop an SSH VPN with the -w option in OpenSSH dynamically.  Works great.  However, I just got my girlfriend a slick new Dell Mini Inspiron that she will use on-the-go.  I would like to set up a simple dialog-based GUI to this script so she can be on the encrypted VPN whenever on public wifi.  Basically, I need a dialog to ask her for the passphrase to the VPN RSA key (no way I'm letting the root SSH login key go without a passphrase!) without passing it on the cl.  Any way to do this with a combo of zenity + ssh-askpass or something similar?  This really needs to be as easy as possible or she wont ever use it.  If it works reliably then I'm considering implementing some iptables rules to block any and all outbound except for ssh to the vpn gateway so she can't even accidentally go unencrypted on the network.

I've considered other VPN solutions but 1) I don't want another daemon since SSH is already listening and can accomplish the same task with ease 2) SSH is completely dynamic and simple == very little overhead and complexity making for stronger security.

Your thoughts are welcome!

Thanks,

Ben

---

### Post by hardkaare on 2008-11-10
Hi there, i have been trying to setup such a ssh vpn tunnel but the tun0 devices nver shows up.

could you maybe explain how you did?

Thx. :-)

---

### Post by kevdog on 2008-11-10
Don't you just want to tunnel your ssh traffic through your home router?  Do you really need a VPN for this or do you want to only tunnel firefox through the tunnel with dns requests?

---

### Post by benanzo on 2008-11-11
Everything aside from a single TCP connection (to the VPN host) should go through the VPN.  When I look at a tcpdump of the local lan traffic, I should only see encrypted TCP from the laptop to the VPN gateway -- no DNS, no NTP, no APT checking for updates etc.  The VPN works as it should, I just can't figure out a scriptable GUI option to pass the SSH key passphrase without it being on the commandline.

The idea being to attempt to thwart most of those easy wlan attacks with dsniff, webmitm, arpspoof etc.

From start to finish, this is what happens:

1) pre-up: randomize local adapter's MAC addr, disable avahi.

2) Associate to gateway (this is a vulnerability given the possibility for evil twins)

3) Broadcast for DHCP (this is a vulnerability given the possibility for DHCP spoofing/racing.)

4) ARP Security: After locking an IP address, I make the gateway's ether addr permanent in the ARP table and use arptables to block any and all Requests/Replies except from/to the gateway.  There is a vulnerability here as well (ARP racing) but this at least reduces the risk of arp spoofing against my machine, but not against the gateway.  So someone could still do a DoS by telling the gateway that my IP is at 00:00:00:00:00:01 or something.  But at least *I* wont be spoofed into thinking the gateway is somewhere that it isn't.

5) IP Security: Use iptables to drop all inbound/outbound on the wlan interface except DNS to/from a predefined DNS server (not whatever I got from DHCP.)  Do a single domain lookup to find the IP of my VPN gateway (unless I already know it, but I usually don't since it's dynamic.)  After getting the IP, drop the DNS traffic as well and allow TCP in/out to the VPN gateway IP and associated SSH port.

6) Start the VPN tunnel, modifying the routing table accordingly.  After this, the only traffic to/from my IP on the wlan will be encrypted TCP to/from my VPN gateway.


It's all scripted nicely.  Basically the idea is that the only way another machine on the wlan will be able to contact me is if they manually add my ether addr to their arp table (since I wont respond) and they wont be able to change my default route, so little risk of mitm, and even if they did, they wont see anything but an opaque blob of 0s and 1s since literally every single packet (save the initial DHCP and DNS) is encrypted.

Going these extra steps (with ARP security etc.) is important because 99% of corporate warriors are more than willing to get their SSL VPN mitmed because they just click through the warnings and don't know what's going on and they just want to check their email.

---

### Post by hardkaare on 2008-11-14
im getting the following error :-(

test@test-laptop:~$ ssh -w 0:0 baastrup@10.0.0.3
Tunnel device open failed.
Could not request tunnel forwarding.

I have modprobeed tun.

---

### Post by benanzo on 2008-11-14
Have a look at these two guides:
[http://www.debian-administration.org/articles/539](http://www.debian-administration.org/articles/539)
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

That should get you pointed in the right direction.

Good Luck!

Ben

---

### Post by nmobix on 2010-03-01
Would you mind sharing your script with the forum, so that I (or someone else) can help you with setting up zenity?


> **benanzo said:**
> Everything aside from a single TCP connection (to the VPN host) should go through the VPN.  When I look at a tcpdump of the local lan traffic, I should only see encrypted TCP from the laptop to the VPN gateway -- no DNS, no NTP, no APT checking for updates etc.  The VPN works as it should, I just can't figure out a scriptable GUI option to pass the SSH key passphrase without it being on the commandline.

The idea being to attempt to thwart most of those easy wlan attacks with dsniff, webmitm, arpspoof etc.

From start to finish, this is what happens:

1) pre-up: randomize local adapter's MAC addr, disable avahi.

2) Associate to gateway (this is a vulnerability given the possibility for evil twins)

3) Broadcast for DHCP (this is a vulnerability given the possibility for DHCP spoofing/racing.)

4) ARP Security: After locking an IP address, I make the gateway's ether addr permanent in the ARP table and use arptables to block any and all Requests/Replies except from/to the gateway.  There is a vulnerability here as well (ARP racing) but this at least reduces the risk of arp spoofing against my machine, but not against the gateway.  So someone could still do a DoS by telling the gateway that my IP is at 00:00:00:00:00:01 or something.  But at least *I* wont be spoofed into thinking the gateway is somewhere that it isn't.

5) IP Security: Use iptables to drop all inbound/outbound on the wlan interface except DNS to/from a predefined DNS server (not whatever I got from DHCP.)  Do a single domain lookup to find the IP of my VPN gateway (unless I already know it, but I usually don't since it's dynamic.)  After getting the IP, drop the DNS traffic as well and allow TCP in/out to the VPN gateway IP and associated SSH port.

6) Start the VPN tunnel, modifying the routing table accordingly.  After this, the only traffic to/from my IP on the wlan will be encrypted TCP to/from my VPN gateway.


It's all scripted nicely.  Basically the idea is that the only way another machine on the wlan will be able to contact me is if they manually add my ether addr to their arp table (since I wont respond) and they wont be able to change my default route, so little risk of mitm, and even if they did, they wont see anything but an opaque blob of 0s and 1s since literally every single packet (save the initial DHCP and DNS) is encrypted.

Going these extra steps (with ARP security etc.) is important because 99% of corporate warriors are more than willing to get their SSL VPN mitmed because they just click through the warnings and don't know what's going on and they just want to check their email.

---

