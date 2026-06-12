---
title: "[HOWTO] Share internet to another computer serving IP and DNS automatically"
date: 2017-12-09
forum: Tutorials
---

### Post by Paloseco on 2017-12-09
This tutorial will explain, using the command line, how to share internet from one computer to another which doesn't have internet.
This guide if for Ubuntu 17.10.
If some program is missing, install it with apt or synaptic. The 'command-not-found' command is really helpful.

Internet < ----- > Router-192.168.0.1 [RJ45] < ---- > [eth0] PC1-192.168.0.x [eth1] < ---- > [eth2] PC2-192.168.127.x

These are the specifications of my setup:

[LIST]
[*]All connections are wired using RJ45 or RJ45 to USB adapters. Using wifi is more difficult.
[*]The Router has the IP 192.168.0.1, offering dynamic IP to the clients and connecting them to the internet automatically
[*]The PC1 has two networks adapters, eth0 and eth1, connecting to router and PC2 respectively. IP to PC2 will be in the range 192.168.127.x
[*]The PC2 only connects to PC1 over eth2. The PC2 can be Windows 10 or Linux, and will be configured in automatic mode for IP and DNS (it's the default and easiest). That will make extremely easy to interchange the computer with any other.
[*]All the commands will be entered on computer 1, there should be no need no do anything on computer 2, like if you were connecting it directly to the router instead. That's the idea.
[/LIST]

**[COLOR="#0000CD"]STEP 1: IP FORWARDING[/COLOR]**
The first step is to enable IP forwarding on computer 1.
```
sudo echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
```

**[COLOR="#0000CD"]STEP 2: IPTABLES[/COLOR]**
Now we configure the iptables firewall to redirect the packets.
```
sudo /sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo /sbin/iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo /sbin/iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

```

**[COLOR="#0000CD"]STEP 3: IP FOR eth1[/COLOR]**
This should be not necessary, but doesn't hurt:
```
sudo ifconfig eth1 192.168.127.1 netmask 255.255.255.0

```

**[COLOR="#0000CD"]STEP 4: DHCP SERVER[/COLOR]**
Install and configure dhcp server.
Then we edit '/etc/default/isc-dhcp-server' to have INTERFACESv4="eth1"
```
sudo apt-get install isc-dhcp-server
sudo sed -i '/INTERFACESv4=/c\INTERFACESv4=\"eth1\"' /etc/default/isc-dhcp-server

```

Edit '/etc/dhcp/dhcpd.conf' so it looks like that:
```
# dhcpd.conf
#
# Sample configuration file for ISC dhcpd
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

subnet 192.168.127.0 netmask 255.255.255.0 {
}

# This is a very basic subnet declaration.

#subnet 192.168.127.0 netmask 255.255.255.0 {
#  range 192.168.127.2 192.168.127.220;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
subnet 192.168.127.0 netmask 255.255.255.0 {
  range 192.168.127.2 192.168.127.100;
  option domain-name-servers 8.8.8.8;
#  option domain-name "internal.example.org";
  option subnet-mask 255.255.255.0;
  option routers 192.168.127.1;
  option broadcast-address 192.168.127.255;
  default-lease-time 600;
  max-lease-time 7200;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.example.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.example.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
```

**[COLOR="#0000CD"]STEP 5: RUN DHCP SERVER[/COLOR]**
```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo service isc-dhcp-server restart
```

**[COLOR="#0000CD"]STEP 6: CHECKING NETWORK ON PC2[/COLOR]**
Now, unplug and replug computer 2 cable if it doesn't automatically get the IP, which could be 192.169.127.2. You can alternatively disable and re-enable the network connection, or just set a static ip (192.168.127.2) if you are going to use always the same setup.
If the PC1 disconnects from internet, you may need to re-run the script to get internet to the PC2.

**[COLOR="#006400"]STEP 6: AFTER RESTARTING THE COMPUTER[/COLOR]**
After restarting the computer, all changes will be lost except those made to files in the filesystem. So, next time you reboot Computer 1, execute commands from steps 1, 2, 3 and 5. Alternatively, you can put those in the following script:
Save this to sharepc1.sh
```
sudo echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
sudo /sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo /sbin/iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo /sbin/iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
sudo ifconfig eth1 192.168.127.1 netmask 255.255.255.0
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo service isc-dhcp-server restart

```
Now copy it to /usr/local/sbin/ and adjust permissions The command will be available to any user, however it will prompted for root password to actually execute it:
```
sudo cp sharepc1.sh /usr/local/sbin/sharepc1.sh
sudo chmod 777 /usr/local/sbin/sharepc1.sh

```

**[COLOR="#FF0000"]USEFUL TIPS AND COMMANDS:[/COLOR]**
```
sudo service isc-dhcp-server status
sudo ifconfig -a
sudo iptables -t nat -L
sudo iptables -S
sudo iptables -vL -t filter

```
* [Setup DHCP server on ubuntu 14.04]("http://www.krizna.com/ubuntu/setup-dhcp-server-ubuntu-14-04/")
* [Quick-Tip: Linux NAT in Four Steps using iptables]("https://www.revsys.com/writings/quicktips/nat.html")
* [Share internet from one wired network to another]("https://ubuntuforums.org/showthread.php?t=2379461")

---

