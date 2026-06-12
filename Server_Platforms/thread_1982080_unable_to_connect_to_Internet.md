---
title: "unable to connect to Internet"
date: 2012-05-17
forum: Server Platforms
---

### Post by associates on 2012-05-17
Hi,

I have a server running on Ubuntu Server 12.04 LTS 32bit. I have assigned a static IP address to it manually on the /etc/network/interface file. Then, I run ifconfig and got to see what I expected to see with the right static IP address. Next, I tried to see if I was connected to the Internet by trying to go to google page but I could not. The Internet was not working. To fix it, I went and edited the file /etc/resolv.conf and put in a few lines of nameservers. It then worked after that. I could go online from this point.

I then happen to need to restart the server. After the reboot, I could not get onto the Internet this time. I then checked my /etc/resolv.conf and found strange that the nameservers I just added were gone or removed. I wonder how this could happen when I have set it with static IP address.

Here is my /etc/network/Interfaces file:
auto lo
iface lo inet loopback

auto lo
iface eth0 inet static
address 202.168.2.35
netmask 255.255.255.248
broadcast 202.268.2.37
gateway 202.268.2.31

Any help or input are very much welcome.

Thank you

---

### Post by josephmills on 2012-05-17
Have you had a look at this ? 
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

there is also this
[https://help.ubuntu.com/community/StaticDnsWithDhcp](https://help.ubuntu.com/community/StaticDnsWithDhcp)
Hope it helps

---

### Post by hawkmage on 2012-05-17
I am assuming that the 268 in the broadcast and gateway are are actually 168.

The network defined by 202.168.2.35 with a mask of 255.255.255.248 should have a broadcast of 202.168.2.39 and a host IP range of 202.168.2.33 - 202.168.2.38.

So  your broadcast address is wrong and your gateway is not reachable.  

I am not surprised that you can not access the internet.

---

### Post by associates on 2012-05-18
Thanks for the replies.

My apology for a mistype of the IP address there.

It should be as follows
auto lo
iface lo inet loopback

auto lo
iface eth0 inet static
address 202.168.2.35
netmask 255.255.255.248
broadcast 202.168.2.37
gateway 202.168.2.31

Quote: 

The network defined by 202.168.2.35 with a mask of 255.255.255.248 should have a broadcast of 202.168.2.39 and a host IP range of 202.168.2.33 - 202.168.2.38

Sorry no, the host IP ranges from 202.168.2.32 - 202.168.2.36 with the broadcast of 202.168.2.37 and the gateway of 202.168.2.31.

Many thanks

---

### Post by lisati on 2012-05-18
I'm no expert on networking, but 202.x.x.x looks unusual to me. On my home network it has usually been something like 192.x.x.x or 10.x.x.x for the broadcast and gateway addresses, depending which of my routers I have been connected to.

---

### Post by associates on 2012-05-18
Sorry, those IP addresses I put up are just not the real IP addresses. They are just examples but the concept is real.

Regards

---

### Post by associates on 2012-05-18
Hi,

it works now. I just found out that I have resolvconf program installed on my system. I quoted the following from wiki.debian.org/NetworkConfiguration page.

If the resolvconf program is installed, you should not edit the resolv.conf configuration file manually as it will be dynamically changed by programs in the system. If you need to manually define the nameservers (as with a static inferface), add a line something like the following to the interfaces configuration file at /etc/network/interfaces: 

dns-nameservers 8.8.8.8 8.8.4.4

save the changes and close the interfaces file. After the system reboots, the system connects straight to the Internet with no more hiccups. It works for me.

Hope this helps others.

Thanks for trying to help me out.

---

### Post by hawkmage on 2012-05-18
> **associates said:**
> Sorry no, the host IP ranges from 202.168.2.32 - 202.168.2.36 with the broadcast of 202.168.2.37 and the gateway of 202.168.2.31.
Lets look at the last octet of the IP Address and mask.

The 4th octet of the netmask has a decimal value of 248 which in binary is 11111000 so your subnet is defined by the first 3 octets and the first 5 bits of the 4th.

The 4th octet of your host address is 35 which is binary 00100011.

Using the mask on this The 4th octet of is made from the first 5 bits of the host address and setting the last 3 to 0 you have 00100000 which in decimal is 32.  This is a reserved address and should not be used.  

The 4th octet of the broadcast address on that subnet is the first 5 bit of the 4th octet of the host address and the last 3 set to 1.  This gives you 00100111 which in decimal is 39.

So in all you have your subnet of 202.168.2.32/29 with a broadcast address of 202.168.2.39 and usable addresses of 202.168.2.33 - 202.168.2.38.

The last octet of 31 will never be in the same subnet as 35 unless you netmask is /26 or smaller.  

If you don't belive me use the CDIR calculator found here: [http://www.subnet-calculator.com/cidr.php](http://www.subnet-calculator.com/cidr.php)

---

### Post by associates on 2012-05-20
Thanks for your reply, Hawkmage.

My apology. I double-checked my subnet IP addresses range and found you're absolutely right. It actually goes from 202.168.2.32 - 202.168.2.39 with 6 usable IPs between 202.168.2.33 and 202.168.2.38. The broadcast IP address is 202.168.2.39.

Thank you for clarifying that.

---

