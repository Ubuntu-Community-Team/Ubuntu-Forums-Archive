---
title: "Dell R710 Server Setup Help Requested!"
date: 2017-05-17
forum: Server Platforms
---

### Post by tragic-hipster on 2017-05-17
I'm trying to setup a Dell R710 to be a gateway/firewall with on-board NAS and multiple connections to wireless access points and computers.  I've found a few guides for desktop systems using Webmin but I always hit a point setting up the network interfaces or DHCP where the server won't talk to my existing network, but can't set up it's own network either.  Any recommendations for guides or walk-throughs?  I probably should've picked a simpler first project:oops:

---

### Post by darkod on 2017-05-17
Yes, you really put a lot on your plate... We have to break this up first...

1. I suggest not using webmin and try to use ssh session and command line. Webmin is not recommended and supported, and sometimes it can produce strange results. So have that in mind if you are insisting on it... And having said that, I think the majority of people here would know to tell you what to do on the command line, but have no idea where that option is in webmin and if it exists at all. Have that in mind too.

2. Most important question first: Will the server have connection directly to the internet with a public address, or will it be behind your home/work ISP router and have private IP?

3. The wi-fi access points, I assume you will attach them to the LAN, not the server itself directly. They need to be on your LAN, and not necessarily connected straight into the server.

---

### Post by tragic-hipster on 2017-05-17
Thank you!  I didn't realize how involved this would be until after I had installed Ubuntu Server.

 I'm not attached to Webmin at all, so that's no problem.

The R710 will have a direct connection to the cable modem and I had planned for the server to act as the gateway and LAN router and connect both wireless routers to their own ports on the back of the server and configure both as access points.  I have two Archer C-7's running DD-Wrt, currently one is configured as a router the other is an access point.

---

### Post by darkod on 2017-05-17
I would recommend to connect wi-fi points to a switch instead of directly to the server. Do you plan to have single LAN subnet? Connecting the APs directly to server ports makes it more difficult to configure, although not impossible.

Just to make sure, by cable modem you mean only a modem and the public IP from your ISP will be on the ubuntu server? The modem does not contain a router and has no private LAN subnet?

---

### Post by tragic-hipster on 2017-05-17
I do have a hardware switch I can use and the plan is to have a single LAN subnet.

This is the cable modem.  [http://www.arris.com/surfboard/products/cable-modems/sb6183/](http://www.arris.com/surfboard/products/cable-modems/sb6183/)  Just one coaxial and one ethernet.

---

### Post by darkod on 2017-05-17
The user guide for 6183 says the modem lan ip is 192.168.100.1 which is strange because if it is only a modem it would not have lan private ip (usually). So, I'm still confused...

I would suggest you confirm with the ISP if the 6183 is doing routing or not, and in case it does not, what requirements do you need on the computer connected to it. Is simply dhcp enough, will it receive ip correctly from the ISP?

That part is important because you need to know how to configure the interface on the server where you will connect the modem.

The rest will be easy...

---

### Post by tragic-hipster on 2017-05-17
I believe the modem ip is just for configuration.  Turning lights on and off and checking signal strength.  I've been using this modem for a couple years and it's been working fine with a stand alone router.  The ISP won't have any information because I bought it separately so I would not have to pay a monthly rental fee.

The DD-wrt was acting as DHCP firewall gateway and NAS.  So, as far as I know, I'm just trying to configure the server to take it's place.

Thank you for taking the time to help me out with this!

---

### Post by darkod on 2017-05-18
Well, in such case lets assume it works with simple dhcp. If you had your own router connected to the modem then you would know if any special configuration was needed for the WAN side.

1. Get the list of your network ports for the ubuntu server. I think they should usually go in order, port 1 is lowest number, then port 2, etc, depending how many ethernet ports you have on the server.
```
sudo lshw -c network
```

Lets assume you will use first port for WAN (connection to modem), second port for your LAN. I will call them eth0 and eth1 but they will probably be called differently because ubuntu 16.04 uses different names depending on NIC chipset.

2. Decide which LAN subnet you want to use, for example 192.168.10.0/24. Configure the necessary interfaces (leave the lo interface as it is):
```
auto eth0
iface eth0 inet dhcp
   post-up iptables-restore < /etc/iptables.rules

auto eth1
iface eth1 inet static
   address 192.168.10.1
   netmask 255.255.255.0
```

3. Enable forwarding in sysctl.conf:
```
sudo nano /etc/sysctl.conf
```

Find the line net.ipv4.ip_forward=1 and enable it (remove the # in front). Save and close the file.

4. Create basic firewall with iptables:
```
sudo nano /etc/iptables.rules
```

Put this inside:
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i eth1 -s 192.168.10.0/24 -j ACCEPT
-A INPUT -i eth1 -p tcp --dport 22 -j ACCEPT

COMMIT

*nat
:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -o eth0 -s 192.168.10.0/24 -j MASQUERADE

COMMIT
```

Those basic rules should stop all traffic coming from internet except the related one. Allow only forwarding from the LAN to the WAN. Allow ssh port 22 only from your LAN (you will not be able to connect to the server from the internet). But that helps stop many attacks from internet too.

You might need modification of these iptables rules, but those are the basic ones.

Reboot the server and you should have routing and firewall working. Note that you still have no dchp server to issue leases to clients. But if you configure any client with static ip in range 192.168.10.x and using as gateway 192.168.10.1, it should work. You can test like that.

The server is not remote, right? In case iptables or anything else locks you out for remote session, you can connect keyboard and monitor and work directly on the server, right? Those rules should be safe but just in case better to have direct access to the server while you are still configuring it.

---

### Post by tragic-hipster on 2017-05-18
So, I've been at this all day and followed your instructions to the T several times (to make sure I didn't mess anything up).  I still can't get the server to connect to the internet through the modem.  After making all the changes I ran:

```
service networking reload
```

to make sure I didn't input anything wrong in the iptables.  No errors popped up but dhcp client runs DHCPDISCOVER on eno1 for a while before timing out and going to sleep.

After final checks I plugged the modem into eno1 (eth0) and performed a reboot.

Once booted I ran ip addr and eno1 has no address.  I tried pinging a website (google) and I get an error.

Double checked the BIOS just make sure there wasn't some embedded setting that needed to be set for NAT gateway setup.

Reinstalled Ubuntu and tried again, same results.

Funny thing is the server connects through the router just fine, but when I plug the server directly into the modem everything locks up.

---

### Post by darkod on 2017-05-19
Check your router WAN settings, maybe there is something there that you need to match on the server. Also, is your ISP filtering for MAC address? Maybe the MAC of the router is permitted in their network but if you want to use another machine you have to report its MAC, in this case of eno1.

Many ISPs that do not force you to use username/password to connect to their network do use MAC filtering to allow only the devices they want to allow to connect.

Like I said from the start, the bigger problem is knowing what you ISP needs for you to configure the connection. After that the rest is easier...

PS. Don't waste your time trying the setup many times. If the dhcp doesn't pick up an IP then something is not right towards the ISP connection. iptables or other settings on the server do not influence that. If you don't get an address by dhcp, the setup of the WAN is not correct.

It is not strange that it is working connected to the router. You already know your router can make correct connection to the ISP, and the ubuntu server has no problem receiving address from the router by dhcp, so it is expected to work.

---

### Post by tragic-hipster on 2017-05-19
Feeling like a fool.  Turns out all I had to was power off the cable modem before plugging into the server.  Everything else was set up perfect.  Thanks for your help!

---

### Post by darkod on 2017-05-19
Hahahah, you see that didn't cross my mind right now either... :)

Glad you got it sorted out.

---

