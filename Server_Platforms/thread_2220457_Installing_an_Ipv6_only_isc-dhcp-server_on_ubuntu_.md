---
title: "Installing an Ipv6 only isc-dhcp-server on ubuntu 14.04 (missing files)"
date: 2014-04-28
forum: Server Platforms
---

### Post by richard51 on 2014-04-28
I am trying to create an Ipv6 only dhcp server using isc-dhcp-server on the Ubuntu 14.04 server platform.

 I have installed isc-dhcp-server and have noticed (*as in some previous packages*) the **/etc/init.d/isc-dhcp-server6** and **/etc/dhcp/dhcpd6.conf** files are not included.

 My questions are these:
    
[LIST]
[*]Are these files still required for Ipv6 to work? 
[*]If so, why are they not included in the package? 
[*]Where can I download the **/etc/init.d/isc-dhcp-server6 **file and how do I get it to work with **apparmor**? 
[*]Could I just alter the **/etc/init.d/isc-dhcp-server **file, adding the -6 option where needed, and then disable the **/etc/init/isc-dhcp-server.conf** (*as there is a /etc/init/isc-dhcp-server6.conf*). 
[/LIST]
  Please note: This is an Ipv6 only server.   I have seen some *how-to's *on the internet, but these seem outdated and incomplete.

Any advice would be appreciated. :D

---

### Post by richard51 on 2014-04-28
Is the **/etc/init.d/isc-dhcp-server** file obsolete? And thats why there isn't a **/etc/init.d/isc-dhcp-server6** file?
```
# /etc/init.d/isc-dhcp-server status (*reports, dhcpd not running*)

# service isc-dhcp-server status (*reports, start/running process xxxx*).

# service isc-dhcp-server6 status (*reports, start/running process xxxx*)
```
So, is the **/etc/init.d/isc-dhcp-server** file obsolete, if not, what is it used for?

Note: I have managed to set up a IPv6 DHCP only server, and I did alter the **/etc/init.d/isc-dhcp-server** file, but because it's not running, I don't think it has any impact on my configuration?

---

### Post by richard51 on 2014-04-29
I actually over-thought this. I have now worked out a more elegant, simpler way to achieve an **IPv6 only** DHCP server.

1.Create the dhcpd6.conf file.
```
# sudo nano /etc/dhcp/dhcp6.conf
```
2. Edit the dhcpd6 configuration file (*Note: change the subnet declaration to match your own*).
```
# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed.
ddns-update-style none;

# Option definitions common to all supported networks...
default-lease-time 43200; # 12 hours
max-lease-time 43200; # 12 hours

# This DHCP server is the official DHCP server for the local network
authoritative;
 
# Subnet declaration
subnet6 2001:db8:0:2::/64 {
    range6 2001:db8:0:2::1001 2001:db8:0:2::13E9;
    option dhcp6.name-servers 2001:db8:0:2::1;
    option dhcp6.domain-search "foobar.com";
}
```
3. Open the default isc-dhcp-server file.
```
# sudo nano /etc/default/isc-dhcp-server
```
4. Edit the default isc-dhcp-server file (*Note: change the INTERFACES to match your own*).
```
# Defaults for isc-dhcp-server initscript
# sourced by /etc/init.d/isc-dhcp-server
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
DHCPD_CONF=/etc/dhcp/dhcpd6.conf

# Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
DHCPD_PID=/var/run/dhcpd6.pid

# Additional options to start dhcpd with.
#    Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
OPTIONS="-6"

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
```
5. Override /etc/init/isc-dhcp-server.conf (*Note: This stops the IPv4 DHCP server from automatically starting*).
```
# sudo sh -c "echo 'manual' > /etc/init/isc-dhcp-server.override"
```
6. Stop the IPv4 DCHP server.
```
# sudo service isc-dhcp-server stop
```
7. Restart the IPv6 DCHP server.
```
# sudo service isc-dhcp-server6 restart
```

And thats all folks!

---

