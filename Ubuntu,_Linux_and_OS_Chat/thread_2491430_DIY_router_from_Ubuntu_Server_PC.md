---
title: "DIY router from Ubuntu Server PC"
date: 2023-10-08
forum: Ubuntu, Linux and OS Chat
---

### Post by atom-goldsmith on 2023-10-08
I'm posting this here in case someone finds it useful, and to take  suggestions from the community on how to make this guide/router better. I hope that I've picked the most appropriate forum but if not, please feel free to move it or I'll repost it in the correct place!

The following guide traces the steps for creating your own router out of an Ubuntu Server machine. To follow this guide and maintain a router like this obviously requires some experience with Linux, home networking, and docker-compose. Please don't attempt this if you can't understand the guide and/or don't have the skills to maintain such a device!

We'll go through the process of setting up AdGuardHome as a DNS and DHCP server, securing SSH access with fail2ban, and getting an IPv6 delegated prefix so that every device on your network can get its own unique global address and bypass NAT.

We do NOT cover the process of adding a wireless interface--I assume that you will use your old wifi router as an access point, like me.

The process outline is fairly simple:
1. Allow packet forwarding
2. Define WAN/LAN interfaces
3. Set up DNS and DHCP with AdGuardHome (docker)
4. Configure firewall
5. Set up fail2ban to protect SSH access (docker)

Warning: do not use the same LAN subnet as your current home network when setting this up!



[SIZE=4] 1.     The basics:     [/SIZE]
        
1a.    Obtain a PC with at least two Ethernet ports. A laptop with ethernet is also handy for troubleshooting!
 
1b.    Install Ubuntu Server 23. Earlier versions of Ubuntu Server lack support for the version of firewalld  to define zones as interfaces (6b, 6c). If you insist on using 20.04 or earlier, you can manually upgrade to firewalld v1.3 or greater.

1c.    Connect the WAN port of the machine to your current LAN.

1d.    Get the machine's LAN IP and SSH in.



[SIZE=4] 2.    Install packages, in case something breaks along the way:[/SIZE]

2a.    Run 'sudo apt update && sudo apt upgrade -y'.

2b.    Run 'sudo apt remove ufw && sudo apt install -y docker docker-compose firewalld net-tools openvswitch-switch'.



[SIZE=4] 3. Allow packet forwarding and enable IPv6 features:[/SIZE]

3a.    Edit /etc/sysctl.conf and uncomment the following:

```
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.ip_forward = 1
net.ipv6.conf.all.forwarding = 1
```
    
3b.    Add the following:

```
# Enable IPv6 router advertisements, SLAAC, and prefix info
net.ipv6.conf.all.autoconf = 1
net.ipv6.conf.all.accept_ra = 2
net.ipv6.conf.all.accept_ra_pinfo = 1
```

3c.    Run 'sudo sysctl -p'.

    
    
[SIZE=4] 4.    Define and configure interfaces: [/SIZE]

4a.    Use ifconfig to get the physical interfaces. The WAN port should be connected to your current LAN and the LAN port(s) should have nothing.

4b.    Edit your netplan file in /etc/netplan (mine is 00-installer-config.yaml). A simple two-port example, using enp1s0 as WAN and enp3s0 as LAN, is below:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      dhcp4: true    
      dhcp6: true
    enp3s0: 
      dhcp4: no
      dhcp6: no
      addresses: [10.0.0.1/24]
      nameservers:
        addresses: [10.0.0.1]
```
        
A more complex netplan example, with a single WAN port (enp1s0) and four bridged LAN ports:

```
network:
  version: 2
  bridges:
    br0:
      interfaces: [eno1, enp0s25, enp4s0, enp5s0]
      addresses: [10.0.0.1/24]
      nameservers:
        addresses: [10.0.0.1]
  ethernets:
    eno1: {}
    enp0s25: {}
    enp1s0:
      dhcp4: true
      dhcp6: true
    enp4s0: {}
    enp5s0: {}
```

Note that we have defined a nameserver (10.0.0.1) that doesn't exist yet; we will set up  AdGuard Home DNS next.

4c.    To request an IPv6 delegated prefix from your ISP so that all of your devices get unique public IPs, create the folder /etc/systemd/network/10-netplan-enp1s0-network.d/ (replace enp1s0 with your WAN iface name), then create override.conf in that folder and enter the following (note that I only get a ::/60 since I use Xfinity Residential, but I request a ::/48 anyway):

```
[Match]
Name=enp1s0

[DHCPv6]
PrefixDelegationHint=::/48
```

4d.    Create the folder /etc/systemd/network/10-netplan-br0-network.d/ (replace br0 with your LAN iface name), then create a file inside that folder called override.conf and enter the following to assign the first of your subnets to your LAN:

```
[Match]
Name=br0

[Network]
IPv6PrefixDelegation=dhcpv6
IPv6DuplicateAddressDetection=1
LinkLocalAddressing=ipv6

[DHCPv6PrefixDelegation]
## Must be unique per subnet
SubnetId=0
```

4d.    Run 'sudo netplan apply'.



[SIZE=4] 5.     AdGuardHome DNS and DHCP server[/SIZE]

5a.    Create a folder for the AdGuard Home docker files (I use /srv/adguard).

5b.    Create a file called docker-compose.yaml and enter the following:

```
version: '3.9'
services:
  adguardhome:
    image: adguard/adguardhome
    container_name: adguardhome
    network_mode: host
    volumes:
      - ./work:/opt/adguardhome/work
      - ./conf:/opt/adguardhome/conf
    restart: always
```


5c.    Navigate to the same folder as the docker-compose file then run 'sudo docker-compose up -d'.

5d.    Go to [LAN IP]:3000 to complete the initial setup of AGH. It doesn't matter what you pick as the interfaces for now; we'll change these in the config file.

5e.    Run "sudo docker-compose down" and edit the file conf/AdGuardHome.yaml:

```
http:
  address: 10.0.0.1:80
...
dns:
  bind_hosts:
    - "0.0.0.0"
    - "::"
...
dhcp:
  enabled: true
  interface_name: "br0"
  ...
  dhcpv4:
    gateway_ip: "10.0.0.1"
    subnet_mask: "255.255.255.0"
    range_start: "10.0.0.2"
    range_end: "10.0.0.254"
```

5f.    Stop and disable the default system resolver by running 'sudo systemctl stop systemd-resolved && sudo systemctl disable systemd-resolved', otherwise AGH will fail to bind to 0.0.0.0:53 and [::]:53.

5g.    In the same folder as the docker-compose file, run 'sudo docker-compose up -d' to bring the container back up, then run 'sudo docker-compose logs adguardhome' and check for errors before proceeding.

5h.    Go to [http://](http://)[LAN IP] from a device on LAN, or if you have a laptop with ethernet, connect it to the LAN interface and go to [http://10.0.0.1](http://10.0.0.1) and configure AdGuardHome. Note that the default DNS server does not provide ad blocking.



[SIZE=4] 6.    Basic Firewall Setup[/SIZE]
    
6a.    Copy the files home.xml and external.xml from /usr/lib/firewalld/zones to /etc/firewalld/zones.

6b.    Edit /etc/firewalld/zones/home.xml:

```
<?xml version="1.0" encoding="utf-8"?>
<zone>
  <short>Home</short>
  <description>For use in home areas. You mostly trust the other computers on networks to not harm your computer. Only selected incoming connections are accepted.</description>
  <interface name="br0"/>
  <service name="ssh"/>
  <service name="dns"/>
  <service name="http"/>
  <service name="dhcp"/>
  <forward/>
</zone>
```

6c.    Edit /etc/firewalld/zones/external.xml

```
<?xml version="1.0" encoding="utf-8"?>
<zone>
  <short>External</short>
  <description>For use on external networks. You do not trust the other computers on networks to not harm your computer. Only selected incoming connections are accepted.</description>
  <interface name="enp1s0"/>
  <service name="dhcpv6-client"/>
  <forward/>
</zone>
```

6d.    Create and edit /etc/firewalld/policies/masquerade.xml to allow traffic to flow from the home zone to the external zone:

```
<?xml version="1.0" encoding="utf-8"?>
<policy target="ACCEPT">
  <masquerade/>
  <ingress-zone name="home"/>
  <egress-zone name="external"/>
</policy>
```

6d.    Run 'sudo firewall-cmd --reload'. If you have a test machine connected to a LAN port, it should now have internet access.




[SIZE=4] 7.    Hosting Remote Services and Port Forwarding (optional)[/SIZE]
    
7a.    Check /usr/lib/firewalld/services or 'sudo firewall-cmd --get-services' for available services, or create your own in /etc/firewalld/services. 

7b.    To enable a service on its default port, add it to '/etc/firewalld/zones/external.xml':

```
<?xml version="1.0" encoding="utf-8"?>
<zone>
  <short>External</short>
  <description>For use on external networks. You do not trust the other computers on networks to not harm your computer. Only selected incoming connections are accepted.</description>
  <interface name="enp1s0"/>
  <service name="dhcpv6-client"/>
  <service name="ssh"/>
  <forward/>
</zone>
```

7c.    A better approach to using default ports like above is to use random high-numbered ports and forward traffic to the service, i.e. opening port 22222 and forwarding traffic to port 22 for SSH access. This dramatically reduces the amount of noise on your services. To do this, make a custom service for the remote port(s):

services/remote-ssh.xml: I am opening two ports because I have two machines that I want to access by SSH: the new router and a media server.
```
<?xml version="1.0" encoding="utf-8"?>
<service>
  <short>Remote-SSH</short>
  <description>Open ports for remote SSH access.</description>
  <port protocol="tcp" port="22222"/>
  <port protocol="tcp" port="22223"/>
</service>
```

services/remote-jellyfin.xml: 
```
<?xml version="1.0" encoding="utf-8"?>
<service>
  <short>Remote-Jellyfin</short>
  <description>Remote port for access to Jellyfin Media Server.</description>
  <port protocol="tcp" port="28920"/>
</service>
```

7d.    Add the custom services to external.xml, and include appropriate forward-port statement:

```
<?xml version="1.0" encoding="utf-8"?>
<zone>
  <short>External</short>
  <description>For use on external networks. You do not trust the other computers on networks to not harm your computer. Only selected incoming connections are accepted.</description>
  <interface name="enp1s0"/>
  <service name="dhcpv6-client"/>
  <service name="remote-ssh"/>
  <service name="remote-jellyfin"/>
  <forward-port protocol="tcp" port="22222" to-port="22"/>
  <forward-port protocol="tcp" port="22223" to-port="22" to-addr="10.0.0.2"/>
  <forward-port protocol="tcp" port="28920" to-port="8920" to-addr="10.0.0.2"/>
  <forward/>
</zone>
```

7d.    To allow forwarding of traffic from WAN to devices on LAN (like the media server at 10.0.0.2 referenced above), create a policy that will allow only certain traffic to flow from WAN to LAN:

```
<?xml version="1.0" encoding="utf-8"?>
<policy target="DROP">
  <service name="remote-ssh"/>
  <service name="remote-jellyfin"/>
  <ingress-zone name="external"/>
  <egress-zone name="home"/>
</policy>
```

7e.    Run 'sudo firewall-cmd --reload'.



[SIZE=4] 8.    Fail2Ban SSH Intrusion Detection and Prevention
[/SIZE]
8a.    Create a folder for the fail2ban docker files (I use /srv/fail2ban).

8b.    Create the file 'docker-compose.yaml' and enter the following:

```
version: '3.9'
services:
  fail2ban:
    image: linuxserver/fail2ban:latest
    container_name: fail2ban
    environment:
      - TZ=America/Los_Angeles
      - PUID=1000
      - PGID=1000
    volumes:
      - ./config:/config
      - /var/log:/var/log:ro
    cap_add:
      - NET_ADMIN
    network_mode: host
    restart: unless-stopped
```

8c.    Run 'sudo docker-compose pull && sudo docker-compose up -d'.

8d.    Create the file config/fail2ban/jail.local and enter the following:

```
[DEFAULT]
banaction = firewallcmd-rich-rules[actiontype=]
banaction_allports = firewallcmd-rich-rules[actiontype=]

[sshd]
enabled = true
```

8e.    Enable any other public-facing services compatible with fail2ban as needed (check config/fail2ban/jail.d) by entering them into jail.local as with sshd above, and mounting a volume with the logs in the fail2ban docker.

8f.    Restart fail2ban with 'sudo docker restart fail2ban'.
    
    
    
[SIZE=4] 9.    Switch to the new router[/SIZE]
9a.    Shut down your old router, new DIY router, and modem. 
9b.    Rewire your home network as needed.
9c.    Start the new router and wait until it's fully booted. Start the modem and wait until it's connected.
9d.    Connect directly to your old wifi router (via ethernet or wifi) to switch it to access point mode.



[SIZE=4] 10.    Additional suggestions:[/SIZE]
* Backups -- nuff said.
* Set up some kind of DDNS service.
* Further secure SSH by disabling root login and using encryption key-only access.
* Set up a WireGuard server to access your local services and network files as though you were at home.
* Set up a NodeExporter-Prometheus-Grafana stack to monitor metrics, performance, network statistics, and fail2ban intrusion attempts.
* Set up Portainer and/or an ELK (Elasticsearch-Logstash-Kibana) stack to monitor docker.

---

### Post by TheFu on 2023-10-09
Best not to use non-LTS versions of Ubuntu. Nobody wants to go through all this for a system that will get 6 months of patches.  23.04 Ubuntu support end in January, for example.  Today, this guide should be pushing 22.04 which is the most current LTS release.

In a few weeks, 23.10 will be released - don't use it for a router base. Support for it ends next June.

If you are going to use a full OS for a router, why not use an OS built for that purpose by experts?  OpenWRT, OPNSense, pfSense come to mind.  Also, I'm a strong proponent of NOT over installing extra stuff onto a router that is your front line for WAN security.  

Swapping out ufw/iptables/nftables to use firewalld for the interface to the kernel firewall seems unnecessary.  People used to Ubuntu are used to those tools, not firewalld.  However, I do like the firewalld interface API, but not enough to swap out what Ubuntu people expect and know.

Just because there's CPU and storage to load "the kitchen sink," doesn't make it a good idea.  I put a VPN server into that group.  

Same for DNS and DHCP. Those are core infrastructure needs and don't belong on the WAN router.  Long ago, the Linksys people put DNS and DHCP onto their hardware because that's all the had and it was the only hardware they could count on being there. They weren't considering security implications.

Also, Ubuntu people would expect lxd/lxc to be used for Linux Containers, not docker.  Loading docker just to use fail2ban?  Really?  Now, if you want to put something into a Linux Container, consider putting the pihole system into one and using that as your LAN DNS. This works well under lxd ... though I wouldn't put it on the same hardware as my WAN router.

Opening a port to the internet for Jellyfin?  Setup wireguard of you want remote access to anything inside the LAN, including jellyfin. BTW, this works. I use it daily.
Only ssh and wireguard need to allow public access. Nothing else.  I wouldn't enable either on my WAN router. I'd forward those 2 port to another system inside the LAN and let it provide access to other subnets.  After all, we all need at least 2 LAN subnets to follow the FBI's recommendations about IosT devices.  [https://www.fbi.gov/news/stories/cyber-tip-be-vigilant-with-your-internet-of-things-iot-devices](https://www.fbi.gov/news/stories/cyber-tip-be-vigilant-with-your-internet-of-things-iot-devices)

On Ubuntu, root cannot be logged into, so there's little need to do anything with ssh to make that happen.

Of course, opinions vary.

Good topic for chat.  Do you plan to update this and post it to the Tutorials sub-forum?

---

### Post by atom-goldsmith on 2023-10-09
Thanks for your feedback. That's a good point about using an LTS version, I'll have to update the guide for that.

> If you are going to use a full OS for a router, why not use an OS built  for that purpose by experts?  OpenWRT, OPNSense, pfSense come to mind.

As for the many quality router OSes out there, I won't deny that they are better options and that this is a niche project. Personally, I did this because I wanted to run dockers like WireGuard and experiment with k8s, but support for those on most router OSes is poor or nonexistent. OpenWRT is an exception, but the x86 upgrade procedure is horrible. Then, a friend of mine convinced me that it would only take a few config files and containers to turn a Linux PC into a router, so I thought, what the hell... it'll be an interesting experiment.

I may upgrade to a dedicated router OS in the (nearish) future, but for now this serves my needs.

I'm not going to pretend to know all the reasons why someone else might want to do this, but I'm sure someone else will in the near future and I hope this saves them time and effort.

> Swapping out ufw/iptables/nftables to use firewalld for the interface to  the kernel firewall seems unnecessary.  People used to Ubuntu are used  to those tools, not firewalld.  However, I do like the firewalld  interface API, but not enough to swap out what Ubuntu people expect and  know.

I'm trying to keep it simple for the sake of the guide and avoid direct iptables/nftables rules. As for ufw, a friend and I spent two weeks with my first DIY router attempt trying to get it to forward traffic to another LAN machine properly. It was maddening.  Once I switched to firewalld 1.3, everything became simple and smooth. 

> Just because there's CPU and storage to load "the kitchen sink," doesn't  make it a good idea.  I put a VPN server into that group.  

Same for DNS and DHCP. Those are core infrastructure needs and don't  belong on the WAN router.  Long ago, the Linksys people put DNS and DHCP  onto their hardware because that's all the had and it was the only  hardware they could count on being there. They weren't considering  security implications.

As for the WireGuard server, I actually like having it on the router but my use case is somewhat unusual... I want this server to access the internet, but not local services, since I'm not the only one using it. To accomplish this, I assign the wg0 interface to the 'public' zone in firewalld, allow traffic to WAN, and deny traffic to the LAN home zone except for  services like Jellyfin. This works beautifully and is simpler than the firewall rules for having it hosted on a LAN machine.

I don't disagree with you about DNS and DHCP, but for the sake of simplicity in the guide, I decided to combine them into one. Still, I will add a note in the next revision that this is best accomplished on a separate machine/device.

> Also, Ubuntu people would expect lxd/lxc to be used for Linux  Containers, not docker.  Loading docker just to use fail2ban?  Really?   Now, if you want to put something into a Linux Container, consider  putting the pihole system into one and using that as your LAN DNS. This  works well under lxd ... though I wouldn't put it on the same hardware  as my WAN router.

Unfortunately, I'm not familiar with lxd/lxc, only docker. However, note that AdGuardHome is also running in docker here, so it's not just fail2ban.

> Opening a port to the internet for Jellyfin?  Setup wireguard of you  want remote access to anything inside the LAN, including jellyfin. BTW,  this works. I use it daily.

Oh no doubt it works, but like with the WireGuard server, I'm not the only one using Jellyfin, so remote access is a must. And anyway, the firewall rules in the guide are only examples... my real firewall rules are more complex.

> On Ubuntu, root cannot be logged into, so there's little need to do anything with ssh to make that happen.

Good point.

>  Good topic for chat.  Do you plan to update this and post it to the Tutorials sub-forum?                 

Absolutely!

---

