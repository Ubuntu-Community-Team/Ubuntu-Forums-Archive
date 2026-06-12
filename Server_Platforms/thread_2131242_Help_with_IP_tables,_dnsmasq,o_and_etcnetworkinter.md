---
title: "Help with IP tables, dnsmasq,o and /etc/network/interfaces"
date: 2013-04-01
forum: Server Platforms
---

### Post by BhimaPandava on 2013-04-01
I'm setting up a Soekris Net6501 as a router using Ubuntu Server.  The networking hardware I have is as follows: Wired Lan eth0-3 (built-in), Huawei e372 USB stickmodem (ppp0), Sierra Wireless MC7710 MiniPCIe Modem, TPLink USB WiFi dongle. 
 
The configuration that I want to end up with:
  DHCPD listening on eth0 & wlan0 with an address range 192.168.0.50-100
  Eth1 static IP connected to another Linux Server.
  Eth2&3 bonded with 802.3ad connected to my Mac workstation. (currently working fine)
  wwan0 & wwan1 bonded with Bond-RR.  I am having difficulties with the MC7710 right now, so currently I am using the Sakris script & the e372 to get ppp0.
  NAT/IP masquerading from the internal ports (bond0, devices attached with DHCP, static connection on eth1) to the bonded wwan modems (though right now I just need ppp0).


My questions about this are:
1: In this configuration I have about 15 devices which need a working domain, dns, FQDNs, & all that related stuff among themselves but I don't have a real domain.  I have just used "lab.pandava" & wish that all the devices take on a (device).lab.pandava (as in Net6501.lab.pandava).  However, I am still uncertain about the wider implications for this and wonder if some of my problems are in part from the fact that this isn't a real domain somewhere. 

3: My ISP does not have very reliable DNS servers, so I wish to either do some sort of cacheing or insert additional servers into a list (which hopefully is smart enough to begin to ignore unreliable servers) or both.  Currently it's my understanding that dnsmasq is the correct tool for most this.  So, I am going away from isc-dhcp-server to this.  I had also tried adding entries to hostfiles & hostnames.  However, this does not always work for me and I suspect it's down to my iptable setup.

2: When I first setup the router I had it in my head that the router should have an address of 192.168.0.1 and configured a lot of services with this expectation.  However, I am not sure if a actual network port should have this address assigned to it and if so, which one & what factors determine that decision?  In particular I have several services running on the router which the devices connected to DHCP must be able to access (and I am having troubles with that).  I am also not clear what exactly the "allow-hotplug" and "static" v. "manual" directives mean in /etc/networking/interfaces.

3: My current understanding is that I should bridge eth0 and wlan0 as br0 and then refer to br0 in the rest of network configuration.  However, the configuration of dnsmasq is different than isc-dhcp-server.  Rather than specifying which port to use with dhcpd, I'm specifying which port NOT to use, ppp0.  Now I am unsure what the best practice is for this case.

4: Hostapd appears to be the tool to use to make my wifi usb dongle into an access point.  But I am having trouble getting it so all the devices will connect and then once they do get an IP address be able to connect to the rest of my network.  I suspect this is down to a misconfiguration in iptables.  Also, I've never got my iPad to connect, even when other devices could. I am not sure if that shows a fundamental configuration error or if it's just some weird incompatibility of the iPad that requires special treatment.  Again, devices which connect through this need to be able to connect to services running on the router (both by address and FQDN).

5: The time required to restart my networking has varied greatly and lately has begun to require a fairly long time.  I wonder if this is not because I have an incorrect configuration somewhere and I am waiting on a timeout for something.

If anyone has some insight into this, I would really appreciate hearing about it.

The following is my current configuration 

```

[SIZE=2][FONT=courier new]auto ppp0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    allow-hotplug ppp0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    iface ppp0 inet dhcp[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    dns-nameservers 8.8.8.8 8.8.4.4[/FONT][/SIZE]


[SIZE=2][FONT=courier new]## Wired LAN served by the [/FONT][/SIZE][FONT=courier new]DHCP Server on [/FONT][FONT=courier new]Net6501[/FONT]
[SIZE=2][FONT=courier new]auto eth0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    allow-hotplug eth0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    iface eth0 inet static[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       address 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       netmask 255.255.255.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       gateway 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       network 192.168.0.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]       dns-nameservers 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## Wireless Lan Access Point[/FONT][/SIZE]
[SIZE=2][FONT=courier new]auto wlan0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    iface wlan0 inet manual[/FONT][/SIZE]
[SIZE=2][FONT=courier new]        pre-up iw dev wlan0 set type __ap[/FONT][/SIZE]
[SIZE=2][FONT=courier new]        hostapd /etc/hostapd/hostapd.conf
        address 192.168.0.4
        netmask 255.255.255.0
        gateway 192.168.0.1
        network 192.168.0.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]        dns-nameservers 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## Wired Lan with Static Connection to Lab Server[/FONT][/SIZE]
[SIZE=2][FONT=courier new]auto eth1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    iface eth1 inet static[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               address 192.168.0.5[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               netmask 255.255.255.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               gateway 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               network 192.168.0.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               dns-nameservers 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## Bridge for DHCP Server on Wlan0 and eth0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]auto br0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    allow-hotplug br0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    iface br0 inet static[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               address 192.168.0.3[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               netmask 255.255.255.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               gateway 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               network 192.168.0.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               dns-nameservers 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]               bridge-ports eth0 wlan0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]#eth2 is manually configured and slave to bond0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]auto eth2[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    iface eth2 inet manual[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    bond-master bond0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]# same with eth3[/FONT][/SIZE]
[SIZE=2][FONT=courier new]auto eth3[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    iface eth3 inet manual[/FONT][/SIZE]
[SIZE=2][FONT=courier new]    bond-master bond0[/FONT][/SIZE]


[SIZE=2][FONT=courier new]#bond0 is configured with static IP outside of DHCP range[/FONT][/SIZE]
[SIZE=2][FONT=courier new]auto bond0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   iface bond0 inet static[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   address 192.168.0.10[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   gateway 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   netmask 255.255.255.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   network 192.168.0.0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   dns-nameservers 192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## use 802.3ad bonding[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   bond-mode 802.3ad[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   bond-miimon 100[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   bond-lacp-rate 1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]   bond-slaves none[/FONT][/SIZE]

```

The commands I used to create the current iptable
```

[SIZE=2][FONT=courier new][COLOR=#333333]sudoiptables -A FORWARD -o ppp0 -i bond0 -s 192.168.0.0/24 -m conntrack--ctstate NEW -j ACCEPT[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=courier new][COLOR=#333333]sudoiptables -A FORWARD -o ppp0 -i br0 -s 192.168.0.0/24 -m conntrack--ctstate NEW -j ACCEPT[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=courier new][COLOR=#333333]sudo iptables -A FORWARD -o ppp0 -i eth1 -s 192.168.0.0/24 -mconntrack --ctstate NEW -j ACCEPT[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=courier new][COLOR=#333333]sudoiptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -jACCEPT[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=courier new][COLOR=#333333]sudoiptables -t nat -F POSTROUTING[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=courier new][COLOR=#333333]sudoiptables -t nat -A POSTROUTING[/COLOR]-s 192.168.1.0/24 [COLOR=#333333]-o ppp0 -j MASQUERADE[/COLOR][/FONT][/SIZE]

```

The current configuration of dnsmasq
```

[SIZE=2][FONT=courier new]except-interface=ppp0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]#DNS Settings[/FONT][/SIZE]
[SIZE=2][FONT=courier new]server=/localnet/192.168.0.1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]server=/#/8.8.8.8[/FONT][/SIZE]
[SIZE=2][FONT=courier new]server=/#/8.8.4.4[/FONT][/SIZE]


[SIZE=2][FONT=courier new]domain=lab.pandava                #sets the domain name[/FONT][/SIZE]
[SIZE=2][FONT=courier new]dhcp-range=192.168.0.51,192.168.0.100,12h    #sets the range allocate IP addresses to clients and the lease time[/FONT][/SIZE]
[SIZE=2][FONT=courier new]dhcp-option=option:router,192.168.0.1        #sets the IP address of the router (gateway address) to be given to clients[/FONT][/SIZE]
[SIZE=2][FONT=courier new]dhcp-option=option:ntp-server,192.168.0.1       #sets the NTP server[/FONT][/SIZE]
[SIZE=2][FONT=courier new]dhcp-authoritative                #authoritative  DHCP server
[/FONT][/SIZE]
```

[SIZE=2][FONT=arial]The current configuration of hostapd.  So far I have not able to get encryption working, so I created a MAC address whitelist to use in the mean time.  I also would like to use all hardware modes to maximize compatibility but declarations like "hw_mode=b+g" don't appear to work like I would expect. [/FONT][/SIZE]

```

[SIZE=2][FONT=courier new]logger_syslog=-1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]logger_syslog_level=2[/FONT][/SIZE]
[SIZE=2][FONT=courier new]logger_stdout=-1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]logger_stdout_level=1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]### Wireless network name ###[/FONT][/SIZE]
[SIZE=2][FONT=courier new]interface=wlan0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]### Set your bridge name ###[/FONT][/SIZE]
[SIZE=2][FONT=courier new]bridge=br0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## Driver Used[/FONT][/SIZE]
[SIZE=2][FONT=courier new]driver=nl80211[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]ssid=test[/FONT][/SIZE]
[SIZE=2][FONT=courier new]channel=1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]##Set operation mode (a = IEEE 802.11a, b = IEEE 802.11b, g = IEEE 802.11g)[/FONT][/SIZE]
[SIZE=2][FONT=courier new]hw_mode=g[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]### (country name code in ISO/IEC 3166-1 format) ###[/FONT][/SIZE]
[SIZE=2][FONT=courier new]country_code=EU[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]### For open network ##[/FONT][/SIZE]
[SIZE=2][FONT=courier new]wmm_enabled=0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]ignore_broadcast_ssid=0[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]#wpa=3[/FONT][/SIZE]
[SIZE=2][FONT=courier new]#wpa_passphrase=123456789[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## Key management algorithms ##[/FONT][/SIZE]
[SIZE=2][FONT=courier new]#wpa_key_mgmt=WPA-PSK[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## Set cipher suites (encryption algorithms) ##[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## TKIP = Temporal Key Integrity Protocol[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## CCMP = AES in Counter mode with CBC-MAC[/FONT][/SIZE]
[SIZE=2][FONT=courier new]#wpa_pairwise=TKIP[/FONT][/SIZE]
[SIZE=2][FONT=courier new]#rsn_pairwise=CCMP[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## Shared Key Authentication ##[/FONT][/SIZE]
[SIZE=2][FONT=courier new]#auth_algs=1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]
[/FONT][/SIZE]
[SIZE=2][FONT=courier new]## Accept CERTAIN  MAC address ###[/FONT][/SIZE]
[SIZE=2][FONT=courier new]macaddr_acl=1[/FONT][/SIZE]
[SIZE=2][FONT=courier new]accept_mac_file=/etc/hostapd/accept[/FONT][/SIZE]
```

---

### Post by darkod on 2013-04-01
Why so many network connections?

You only need two, one interface towards the internet, and one interface towards your local LAN.

For example, there is no need for specific interfaces to connect you another server or the Mac. If they are in the same LAN, they can connect to the ubuntu router just fine. You can bond interfaces for higher bandwidth, that's OK, but you don't need so many of them with different configuration.

It looks to me like a big mess, you need to bring it down to the basics, and work step by step.

Also, for forwarding packets between interfaces you need to have the ip.forward enabled in /etc/sysctl.conf. Did you enable it?

---

### Post by BhimaPandava on 2013-04-01
I'm not really sure how to respond to the question of why so many, except that this device is the lan and everything connects to it.  The only other network switch that I planned to use will be connected to eth0 but currently it's not connected to anything.  Setting up isc-dhcp-server to listen on multiple nics on the same network segment turned out to be a bad idea.  So I configured everything that does not ever get unplugged from the router to use static IP addresses.  So far, this has worked fine.

When I first began this configuration, I began with the basics and I had some things working OK.  Bond0 works fine and always has.  Eth1 works fine as a static connection to the other server.  Ppp0 works as well can be expected.  And my initial iptables configuration also worked OK.  At that point I had everything that I understood how to configure working (I could connect to internet from all devices and the NAT worked as I wanted it to). 

However, when I added the WiFi dongle as an access point things began to fail sporadically (and attempting to revert back to the early configuration without it turned out to be painful). My understanding was that I needed to bridge both eth0 and wlan0 together and then direct the dhcp server to that bridge... but perhaps that is something only needed by the isc-dhcp-server.

I think one of the things that make returning to basic settings so painful is that I don't fully understand how to structure iptables, so changing them to reflect network configurations changes is difficult.  Moreover returning to a basic configuration lacks capabilities which I still need... like dhcp and wifi.

Lastly ip.forward is enabled in /etc/sysctl.conf.  I can connect to all the services running on the router from all my devices with static IP addresses but not from devices with IP addresses assigned to them by the dhcp server in dnsmasq.

---

### Post by darkod on 2013-04-01
So, you are actually trying the server to be a switch also, not just a router? If you already have a switch, why? It doesn't have enough ports?

That configuration is much more complicated than only a router. If you can avoid it, I would. Just use the server as a router, and let the switch do its job.

If you need wi-fi too, get one of those access points or similar.

Otherwise, to make the server act as switch you are looking into much more complexity I guess.

---

### Post by BhimaPandava on 2013-04-01
> **darkod said:**
> So, you are actually trying the server to be a switch also, not just a router? If you already have a switch, why? It doesn't have enough ports?

That configuration is much more complicated than only a router. If you can avoid it, I would. Just use the server as a router, and let the switch do its job.

If you need wi-fi too, get one of those access points or similar.

Otherwise, to make the server act as switch you are looking into much more complexity I guess.

I really not unappreciative of any help you might be trying to give me but I am really having trouble understanding your responses.  I have the hardware I have and without a really good reason don't want to buy more.  I chose the connections I have setup specifically to use the hardware I have. I know that individually all the hardware do exactly what I need because I've already successfully configured each of them to work by themselves.

What I am having trouble with is correctly configuring all the pieces to work together.  I get that this might be a complicated setup but I really do not want to just buy new hardware because I can't figure out a correct setting for iptables.

---

### Post by darkod on 2013-04-01
Unfortunately, I don't know enough iptables to help you with this. If you only wanted to make a router, that's not too complicated. But you want to make a switch as it seems. I would say that is definitely more complicated.

Also, don't underestimate this: Just because your pieces of hardware are working by themselves, that doesn't mean they can work together as you intend to use them. There is big difference between working separately, and together. So, we are not talking about buying HW because you can't figure out iptables, we are talking about possibly buying HW you need for things to work. Are you sure this can be done at all, regardless of iptables configuration? I'm not.

If you really want to continue, I would still make changes to your setup. You said so far you left the switch aside. Don't do that, use the switch. Don't create multiple wired connections on the server, only one, and connect it to the switch. Other wired devices will be connected to the switch too, and that's how they will be able to talk to your server/router.

If I understood correctly, you will use one 3g usb modem as internet connection, and another tp-link usb wi-fi dongle to create wi-fi network. What's the purpose of the sierra wireless? Don't use HW just because you have it, use it if you need it. Otherwise it just makes complications in your setup, without any real benefit.

That's what I would do. Wired connection from the server/router to the switch (you can bond interfaces if you want, you said you have 4 ports on the server). But use only one connection, not 2 or 3 connections. If you bond more interfaces, use the bonded one, no problem, but that still counts as single connection and has only one private IP assigned. Also, your switch might need to support bonding, otherwise you have to use a single connection/port.
Then, use the 3g dongle for internet access, and the tp-link wi-fi to make a wi-fi network.

Does that sound like what you are trying to accomplish?

---

