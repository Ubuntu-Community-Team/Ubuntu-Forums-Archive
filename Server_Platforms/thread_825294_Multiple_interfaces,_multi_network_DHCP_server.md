---
title: "Multiple interfaces, multi network DHCP server"
date: 2008-06-10
forum: Server Platforms
---

### Post by mangoHead84 on 2008-06-10
Hi,

I am trying to set up a gateway/router/firewall box for a small business. The requirements for the job are that the box must serve up internet to the business and also to the apartment downstairs and I am having trouble configuring the DHCP server on the gateway.

The gateway has three Network Interface Cards:
[INDENT]eth0: which connects to the modem and the rest of the internet
eth1: which goes downstairs, to serve the apartment
eth2: which serves the small business[/INDENT]

The DHCP server should assign all dynamic ip addresses to the downstairs network, in the range 192.168.0.0 - 192.168.0.255

The upstairs (business) should assign static ip addresses to the servers on the network and dynamically assign ip addresses to any other computers asking for a DHCP lease on the eht2 interface. The addresses assigned to this network should be in the range of 10.0.0.0 - 10.0.0.255

My problem is that computers connected to the 'eth1' interface do not receive an ip address. After connecting a computer to the eth1 interface the computer requests an ip address, but none comes.

NOTE: I am quite sure this is not a hardware fault, I have tested the system first with a crossover cable and a computer directly connected to the router interface and also with both computers connected to a switch using patch cables. 

The contents of my /etc/dhcp3/dhcpd.conf file are as follows:

[Global Settings]....

subnet 10.0.0.0 netmask 255.255.255.0 {
[INDENT]interface eth2;
option routers 10.0.0.254;
option subnet-mask 255.255.255.0
option domain-name-servers 10.0.0.254;[/INDENT]

[Server Settings]...
...
...

}

subnet 192.168.0.0 netmask 255.255.255.0 {
[INDENT]interface eth1;
        option routers                  192.168.0.254;
        option subnet-mask              255.255.255.0;

        option domain-name              "example.com";
        option domain-name-servers       192.168.0.254;[/INDENT]
}

---

### Post by netztier on 2008-06-11
> **mangoHead84 said:**
> Hi,
The gateway has three Network Interface Cards:
[INDENT]eth0: which connects to the modem and the rest of the internet
eth1: which goes downstairs, to serve the apartment
eth2: which serves the small business[/INDENT]


Did you check this against **/etc/defaults/dhcp3-server** ?
```
marc@blaze:/etc/default$ more dhcp3-server 
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES=""
```

Is dhcpd listening on all interfaces you want it to? Make sure it does not do so on the interface that faces the Internet.

regards

Marc

---

### Post by mangoHead84 on 2008-06-11
Hi Marc, 

Thanks for the reply, I do in fact have the two internal interfaces listed in the /etc/default/dhcp3-server file, this is the contents of that file:
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1 eth2"
```

Also, the way I tried to set up the /etc/dhcp3/dhcpd.conf file is as follows:

```
##########################################
#####----- Global Configuration -----#####
##########################################
ddns-updates off;
option T150 code 150 = string;
deny client-updates;
#one-lease-per-client false;
#allow bootp;

ddns-update-style none;

option domain-name "vlan.local";
option domain-name-servers    210.56.15.1, 231.117.250.27;

default-lease-time 6000;
max-lease-time 7200;

authoritative;
##############################################
#####----- End Global Configuration -----#####
##############################################

###############################################
#####----- Start Modem Configuration -----#####
###############################################
subnet 192.168.1.0 netmask 255.255.255.0 {
	interface eth0;
}
#############################################
#####----- End Modem Configuration -----#####
#############################################

####################################################
#####----- Start Downstairs Configuration -----#####
####################################################
subnet 192.168.0.0 netmask 255.255.255.0 {
	interface eth1;
	default-lease-time 6000;
	max-lease-time 7200;
	option subnet-mask 255.255.255.0;
	option routers 192.168.0.254;
	option broadcast-address 192.168.0.255;
}
##################################################
#####----- End Downstairs Configuration -----#####
##################################################

##################################################
#####----- Start Upstairs Configuration -----#####
##################################################
subnet 10.0.0.0 netmask 255.255.255.0 {
	interface eth2;
	default-lease-time 6000;
	max-lease-time 7200;
	range 10.0.0.100 10.0.0.200;
	option subnet-mask 255.255.255.0;
	option routers 10.0.0.254;
	option broadcast-address 10.0.0.255;
}
################################################
#####----- End Upstairs Configuration -----#####
################################################

#####################################################################
#####----- Start Server and Fixed IP Address Configuration -----#####
#####################################################################
group{
	###--- Any global server settings should go here ---###

	#- Printer -#
	host printer {
		hardware ethernet 00:00:00:00:00:00;
		fixed-address 10.0.0.25;
		}
	#- James computer -#
	host james {
		hardware ethernet 00:00:00:00:00:00;
		fixed-address 10.0.0.105;					
	}
	#- TServer computer -#
	host tserver {
		hardware ethernet 00:00:00:00:00:00;
		fixed-address 10.0.0.110;
	}
	#- Windows 2008 Server -#
	host win2008server {
		hardware ethernet 00:1C:C0:2C:9C:2F;
		fixed-address 10.0.0.115;
	}
	#- Asterisk Box -#
	host asterisk {
		hardware ethernet 00:00:00:00:00:00;
		fixed-address 10.0.0.120;
	}
	#- WWW Server -#
	host www2 {
		hardware ethernet 00:00:00:00:00:00;
		fixed-address 10.0.0.125;
	}
}
###################################################################
#####----- End Server and Fixed IP Address Configuration -----#####
###################################################################
```

NOTE: I have changed the ip addresses and zeroed out the MAC addresses, for security, but they are set up properly.

So, the part in which I try to specify that all requests for a dhcp lease coming in on eth1 belong to subnet 192.168.0.0 is in the subnet section with the line 'interface eth1;'. I'm not sure if this is correct or not, but this was the only way I found how to do it. Is this line correct? If not how would you tell dhcpd to do this?

---

### Post by mangoHead84 on 2008-06-11
Ok, I figured out what was wrong, thanks to 'witte' on the debian channel at irc.debian.org. 

The problem was that the subnet declaration for the 192.168.0.0 network was missing the range argument. So I just added the line 'range 192.168.0.200 192.168.0.253' to the subnet section and viola!! It works! I'm so happy, I've been stuck on this problem for two days.

Thank you for all your help.

---

