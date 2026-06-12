---
title: "Gateway Server 8.04 Setup Help Needed"
date: 2008-04-25
forum: Server Platforms
---

### Post by sparkieman on 2008-04-25
Hello all you smart people. I have a PC I've build to act as a Linux Gateway/Server/Router etc.
I need some help getting everything running.I would really appreciate your help. Maybe I could send you guys freshed baked cookies or some cold beer..

I have installed Ubuntu 8.04 Server onto the Machine. I am competent with Ubuntu, but linux is still new to me. I am familiar with sudo nano commands etc..

Here are the Ubuntu Server Machine specs:
Intel pentium 4500 Dual Core
Gigabyte EP35-DS3R Motherboard
1 GB RAM
250 GB Hardrive
1 Onboard realtek Nic
1 Intel Pro PCI-E Gigabit NIC

Here is what I've done so far:
1)Installed Ubuntu Server 8.04 onto clean partition
2)Installed all default apps.. LAMP,SSH,File Printer...everything except PostgreSQL
3)Changed repositories to retrieve and install the latest Webmin
4)Installed webmin
5)Installed DHCP-Server

I have read many guides on the internet and am getting familiar with things but none have been clear. Please start slowly with me...

To start, I would like the Ubuntu Server to Protect my home network with a firewall, assign DHCP to PC's that want to connect to internet.

So far I selected the Realtek (eth0) as the primary NIC. I will plug that one into the cable modem.
I will then plug the Intel Nic into a Gigabit Switch to server the rest of the network.

Okay...so where do i go from here. what are the first things I should do?

Mark

---

### Post by terazen on 2008-04-25
I used to use IpFilter for this years back.  I'm using a monowall now (which uses ipfilter) so I know it's still out there.

---

### Post by terazen on 2008-04-25
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Brazen on 2008-04-26
> **terazen said:**
> I used to use IpFilter for this years back.  I'm using a monowall now (which uses ipfilter) so I know it's still out there.

Monowall uses pf.  Ipfilter has been replaced by netfilter (also referred to by the name of its management tool: iptables).

---

### Post by sparkieman on 2008-04-26
Thank you for the suggestions, I am getting closer.
Progress has been made.

I have DHCP server running now. 
From the Servers command line (External nic eth0) I am able to ping google.ca.
The PC's connected to the internal NIC (eth1) are able to ping the Server.
The server is assigning IP's to the computers connected to the Internal NIC.
The computers  are not able to connect to the internet.
I believe that webmin isn't configuring IPTables correctly.

I believe that Webmin isn't doing it properly for 8.04

How do I go about configuring the IPtables for the NAT?

---

### Post by tim356 on 2008-04-28
Look up routing - this is your problem now.

---

### Post by gekkio on 2008-04-28
If you don't fear the command line, I recommend trying Shorewall, it simplifies configuring iptables a lot (especially NAT is very quick to configure).

And it seems that there is a Shorewall module for Webmin too.

If you still want to use plain iptables, make sure you have forwarding enabled (I'm pretty sure it's needed for NAT).

Running
```
sysctl net.ipv4.ip_forward
```
should return
```
net.ipv4.ip_forward = 1
```

If not, edit /etc/sysctl.conf and reboot

---

### Post by markymarknz on 2008-04-28
I would recommend looking into a custom distro called Smoothwall Express.
I use this at home and it works a treat.
It is designed to be a firewall and it also runs DHCP, NTP, web/im proxy and a whole lot more.
It is all run through a web interface or ssh.

---

### Post by foolano on 2008-04-28
Hi,

Your scenario fits perfectly with the one depicted in [here]("http://trac.ebox-platform.com/wiki/Document/HowTo/SetUpNetworkScenario") in [eBox]("http://ebox-platform.com").

eBox is packaged in Hardy, so you won't need to install anything else. It also has a web interface.

---

### Post by venzen on 2008-04-28
Firstly, welcome to the Linux community. If you are using Ubuntu then you are using Linux ;) Well done on getting DHCP working.

Next up, I would agree with Gekkio above and suggest shorewall as the iptables/netfilter configuration utility of choice. No need to leave the safety of Ubuntu Linux. Just do 

```
sudo apt-get install shorewall
```

However, it seems you are new to the command line (which is the traditionally pure interface to Linux which you should grow accustomed to asap) and you may feel more comfortable with smoothwall

```
sudo apt-get install smoothwall
```

I've never used it but believe it is newbie friendly.

However, shorewall has great resources at [http://shorewall.net](http://shorewall.net) - read the Two-interface guide at that site and get cooking. All your requirements will be answered there. Patience is the key and has its rich rewards in the Linux environment. Ask lots of questions and remain descriptive as you are doing and soon you will know enough to help others.

Tim356 is totally right. Your problem now is routing - a fundamental networking concept which the shorewall documentation and two-interface guide will help you understand. Using smoothwall might make it easier but will not improve your understanding of what you're actually doing, so, another reason to choose shorewall.

report your progress here.

regards,
venzen

---

