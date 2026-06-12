---
title: "DHCP3 Server not leasing IP addreses properly..."
date: 2008-07-12
forum: Server Platforms
---

### Post by badm0nk3y369 on 2008-07-12
Hello all!
I would like to say before I begin, that I have already searched through the forums here, regarding dhcp3 and have not found an adequate solution to my problem.

My issue, as the topic suggests, is that dhcp3 is not properly distributing IPs in my defined range.
IPs will be assigned to dhcp clients on my network, but the leases never seem to be released. Every NIC that has been interfaced with the server seems to be retained in the server, even after reboots, and service restarts through init.d.

Everything else works flawlessly, and I absolutely adore my Ubuntu server, over any Windows server version I have ever had to maintain.

Please, enlighten me as to what I should be looking for. I've been using Linux for a little more than a year now, and understand the basics, plus a little more as far as Ubuntu and Debian distros go. 

My dhcpd.conf file looks correct, but I don't know if anyone else has had a problem like this. I just don't want my scope to fill up, since several PCs are connected to my network for maintenance, etc.

I thank everyone in advance for your knowledge! :)

---

### Post by chris.zeman on 2008-07-12
Could you post your dhcpd.conf file? Sometimes it takes more than one pair of eyes to spot a problem. :)

Chris

---

### Post by badm0nk3y369 on 2008-07-13
Sure thing!
Thanks for the response!
I'll ssh in right now, and post it.

---

### Post by badm0nk3y369 on 2008-07-13
> **chris.zeman said:**
> Could you post your dhcpd.conf file? Sometimes it takes more than one pair of eyes to spot a problem. :)

Chris

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style interim;

# option definitions common to all supported networks...
option domain-name "freeman.local";
option domain-name-servers 192.168.254.20, 208.67.222.222;
one-lease-per-client on;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 192.168.254.0 netmask 255.255.255.0 {
 # range 192.168.254.50 192.168.254.230;
 # option routers 192.168.254.254;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
subnet 192.168.254.0 netmask 255.255.255.0 {
range 192.168.254.50 192.168.254.100;
option domain-name-servers 192.168.254.20, 208.67.222.222;
option domain-name "freeman.local";
option routers 192.168.254.254;
option broadcast-address 192.168.254.255;
default-lease-time 60;
max-lease-time 720;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
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
#  fixed-address fantasia.fugue.com;
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

---

### Post by chris.zeman on 2008-07-14
Everything appears to be OK. I misunderstood your original post and though you had said the IPs being assigned weren't in your defined range. I'm sorry about the confusion. I have a better understanding of what you were asking now, however. :)

Are the devices that were assigned said addresses still online? If so, they are simply renewing their leases periodically. I don't know when those leases will disappear from your list, but I am pretty confident you won't have to worry about your scope filling up. I believe that dhcp3 will simply re-assign an expired lease if there are no "open" addresses. I could be wrong, but I don't THINK I am. ;) Hopefully somebody will pop in and confirm or correct this.

Chris

---

### Post by badm0nk3y369 on 2008-07-17
> **chris.zeman said:**
> Everything appears to be OK. I misunderstood your original post and though you had said the IPs being assigned weren't in your defined range. I'm sorry about the confusion. I have a better understanding of what you were asking now, however. :)

Are the devices that were assigned said addresses still online? If so, they are simply renewing their leases periodically. I don't know when those leases will disappear from your list, but I am pretty confident you won't have to worry about your scope filling up. I believe that dhcp3 will simply re-assign an expired lease if there are no "open" addresses. I could be wrong, but I don't THINK I am. ;) Hopefully somebody will pop in and confirm or correct this.

Chris


*Bump*
Thanks for your input Chris!
I didn't think about the leases being dished out again after the scope was used up.
And to answer your question about all the devices being online still: No, only a certain few are still online.
My Linux box, Mac, Windows PC, PS3 and Xbox 360 are the only things still online, (with the PCs on DHCP) and the only ones with static IPs are the game consoles. They have their own IPs out of the lease range though.

If all else fails, when the scope fills up, I guess I'll just have to copy the config and reinstall Dhcp3...

There's no way I'm going back to Win servers again. This is the only issue I've had with my Linux server so far, and it is just a minor inconvenience.

Anyone else should feel free to give their input on my issue. I don't want to have to reinstall Dhcp3 if I don't have to...

---

### Post by badm0nk3y369 on 2008-07-20
*bump*

Anyone?!?!

---

### Post by cariboo on 2008-07-21
This is from the Redhat 9 customization handbook, but it should apply to Ubuntu also:

>  On the DHCP server, the file /var/lib/dhcp/dhcpd.leases stores the DHCP client lease database. This file should not be modified by hand. DHCP lease information for each recently assigned IP address is automatically stored in the lease database. The information includes the length of the lease, to whom the IP address has been assigned, the start and end dates for the lease, and the MAC address of the network interface card that was used to retrieve the lease.

All times in the lease database are in Greenwich Mean Time (GMT), not local time.

The lease database is recreated from time to time so that it is not too large. First, all known leases are saved in a temporary lease database. The dhcpd.leases file is renamed dhcpd.leases~, and the temporary lease database is written to dhcpd.leases.

The DHCP daemon could be killed or the system could crash after the lease database has been renamed to the backup file but before the new file has been written. If this happens, there is no dhcpd.leases file that is required to start the service. Do not create a new lease file if this occurs. If you do, all the old leases will be lost and cause many problems. The correct solution is to rename the dhcpd.leases~ backup file to dhcpd.leases and then start the daemon.


Check the leases database this should give you  an idea what is going on. I use my router for dhcp now, but I did have a dhcp server running at one point and it seemed to take about a week for the ip adresses to renew, this was with the default dhcpd.conf file.

Jim

---

