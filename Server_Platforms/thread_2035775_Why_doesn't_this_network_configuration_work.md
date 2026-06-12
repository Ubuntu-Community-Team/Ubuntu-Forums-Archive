---
title: "Why doesn't this network configuration work?"
date: 2012-07-31
forum: Server Platforms
---

### Post by Hashimi on 2012-07-31
I installed ubuntu server 12.04,

I configured my network like this:
```
auto eth0
iface eth0 inet static
address 121.127.36.164
netmask 255.255.255.0
network 121.127.36.0
broadcast 121.127.36.255
gateway 121.127.36.1
dns-nameservers 208.67.222.222 208.67.220.220
```

 with these configurations, I cannot connect to internet. whenever I do ```
ping www.google.com
``` it just waits. and after a minute or more, it returns unknow host error. when I do ```
ping 77.245.149.23 
```or any other IP, it returns unreachable host error.

Could you please help me fix this error?

Edit: I can ping the IP from my network. My modem is set to DHCP enabled dynamic IP.

thanks

---

### Post by Grenage on 2012-07-31
Do you have any routes configured?

For the benefit of the thread, can you post the output of these two commands:

```
ifconfig
route
```

---

### Post by darkod on 2012-07-31
Do you use a modem or a router as an entry point?

If it's a router and it's already changing the public IP into private range, you can't use public IP in the server network config. It will already be behind the router.

On the other hand, you said that the modem is set to DHCP and dynamic IP. If the ISP is giving you a dinamic IP how can you expect it to work with a static IP configured on the server? If the modem is only passing through the connection, you will need to set the server config to dhcp so that it receives IP from the ISP network. You can't just guess your public IP if it's not static.

So, if this is only a modem we are talking about and you expect the public IP on the server, try something like:
auto eth0
iface eth0 inet dhcp

If we are talking about a router doing NAT from public to private, it's a different ball game. You can set a static IP outside the router dhcp range, but private IP not public.

---

### Post by Hashimi on 2012-07-31
Thanks Grenage and darkod for answers. I will provide details in the next post for you request Grenage.

I am using a wireless enabled router, where the router is set to Dynamic IP dhcp enabled. 

I ask static IP from my ISP and they asked me to send them my server mac address. I send them the MAC address and configure my server as above.

Am I doing something wrong? or I must blame my ISP for misconfigurations? 

It is two days I am working over this. Can not find any solutions.

---

### Post by darkod on 2012-07-31
If you are using a wi-fi router, it will probably do NAT translation so you can only have a private IP on the server. The public IP will be allocated to the WAN interface of your router, and in this case the ISP needs the MAC of your router, not your server. This is because from their network they see the router as a device, everything after it is in the private LAN.

Look into the router web interface (or the labels on it) and whether it has a MAC for the WAN port, or Line port or what ever it's called.

The best way to check is to connect another computer to the router. Does the computer receive a private IP, something like 192.168.1.x? If that is the case the router is doing NAT and all machines after it need to work in the 192.168.1.x range.

---

### Post by collisionystm on 2012-07-31
Firstly, I would simplify your config file. You don't need all of that.


auto eth0
iface eth0 inet static
address 121.127.36.164
netmask 255.255.255.0
gateway 121.127.36.1
dns-nameservers 208.67.222.222 208.67.220.220

2nd, make sure to restart your networking services after you change the interface file

sudo /etc/init.d/networking restart


The attempt your ping.

You can also see if its just your DNS servers are not responding.

If you cannot ping google.com

try to ping 8.8.8.8

If you can reach 8.8.8.8 then your IP parameters are good, but your DNS servers wont respond. In that case I suggest you just use 8.8.8.8 as your DNS name server.

*EDIT*

P.S.

I noticed this is an external IP address. Be sure to turn your firewall on.

Cheers!

---

### Post by Hashimi on 2012-07-31
Sorry for my late explanations, but I must firstly explain the scenario:

There is a company with 20 staff. I developed a web application with PHP/CodeIgniter for them. Where they want to use it inside their local network.

I install an Ubuntu server 12.04, and want to make it a local server for this purpose. I need to assign a static IP address for this server, where it musnt changed.

I have a TP-Link Wireless Router, where the internet connection is provided through this router. It is DHCP enabled.

Now for this, what I need? How I must configure my server?

Because I am newbie in this network configuration issues, I will appreciate any help. 

Thanks.

---

### Post by nbetham on 2012-07-31
After making changes to the interfaces file I usually find it is necessary to do a reboot, this may be because i'm accessing it via SSH but i'm not positive. None the less it is a sure fire way to make sure that the new configuration is in use.

---

### Post by collisionystm on 2012-07-31
> **Hashimi said:**
> Sorry for my late explanations, but I must firstly explain the scenario:

There is a company with 20 staff. I developed a web application with PHP/CodeIgniter for them. Where they want to use it inside their local network.

I install an Ubuntu server 12.04, and want to make it a local server for this purpose. I need to assign a static IP address for this server, where it musnt changed.

I have a TP-Link Wireless Router, where the internet connection is provided through this router. It is DHCP enabled.

Now for this, what I need? How I must configure my server?

Because I am newbie in this network configuration issues, I will appreciate any help. 

Thanks.


Well instead of trying to assign your server an external internet accessible address, you should be giving it a local IP.

---

### Post by SeijiSensei on 2012-07-31
The easiest solution is probably to tell the router what IP address you want it to assign to the server.  You can reserve an IP address for a specific "MAC" address, the hardware address assigned to the Ethernet card.  Then you can just let the server configure itself with DHCP at boot time.

If you prefer, you can assign a static address to the machine in /etc/network/interfaces as you tried before.  However the address you use has to be in the local network subnet, like 192.168.1.34.  You cannot assign the machine a number in the public IP space; that's on the other side of your router.  If you take this approach, make sure you coordinate with the router's admin so you assign the server an address outside the range of addresses being assigned to client machines with DHCP.

---

### Post by Hashimi on 2012-07-31
collisionystm; thank you very much.
SeijiSensei; thanks for great explanation. Now I really know what to do :)

I hope I won't face to any problems, otherwise I will update the topic.

Regards

---

### Post by Hashimi on 2012-08-02
> **SeijiSensei said:**
> The easiest solution is probably to tell the router what IP address you want it to assign to the server.  You can reserve an IP address for a specific "MAC" address, the hardware address assigned to the Ethernet card.  Then you can just let the server configure itself with DHCP at boot time.

If you prefer, you can assign a static address to the machine in /etc/network/interfaces as you tried before.  However the address you use has to be in the local network subnet, like 192.168.1.34.  You cannot assign the machine a number in the public IP space; that's on the other side of your router.  If you take this approach, make sure you coordinate with the router's admin so you assign the server an address outside the range of addresses being assigned to client machines with DHCP.

I reserved an IP address to my server MAC address from my Router interface and it worked perfectly.

Thank you very much.

---

