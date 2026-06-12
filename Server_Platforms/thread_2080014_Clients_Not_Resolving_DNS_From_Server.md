---
title: "Clients Not Resolving DNS From Server"
date: 2012-11-02
forum: Server Platforms
---

### Post by jlacroix on 2012-11-02
Hello, I have a strange problem that is probably something stupid but I can't seem to figure it out. I had a dedicated DNS/DHCP server but I consolidated that functionality into my file server, and then I took my former DHCP server offline. I added DNS/DHCP to my main server by copying the config files over (that's probably the problem). The server *seems* able to resolve DNS. My client isn't.

I submitted a topic similar to this one before, and the problem then was that my client wasn't set up to point to the DNS server. That is not the case this time. The symptom is that when I ping a local machine, it goes out to the Internet instead of checking my DNS server first.

My server is 172.16.254.10. I am using KVM on this server, so it is using a bridge. /etc/network/interfaces looks like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 172.16.254.10
        network 172.16.254.0
        netmask 255.255.255.0
        broadcast 172.16.254.255
        gateway 172.16.254.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

dns-search localnet
dns-nameservers 172.16.254.10 172.16.254.1

```

Here is /etc/bind/named.conf:
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
```

Here is /etc/bind/named.conf.options:
```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                208.67.222.222; 8.8.8.8;
        };

        //=====================================================================$
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //=====================================================================$
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

Here is /etc/bind/named.conf.local:
```
//
// Do any local configuration here
//
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "localnet" IN {
        type master; file "/etc/bind/net.localnet";
};

zone "254.16.172.in-appr.arpa" {
        type master; notify no; file "/etc/bind/revp.172.16.254";
};

// The below lines were advised to be put in the config file, per RFC1918.
// It was explained that this prevents useless forwarding to the Internet.

zone "10.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "17.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "18.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "19.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "20.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "21.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "22.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "23.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "24.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "25.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "26.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "27.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "28.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "29.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "30.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "31.172.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
zone "168.192.in-addr.arpa" { type master; file "/etc/bind/db.empty"; };
```

Here is /etc/bind/named.conf.default-zones:
```
// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};
```

Here is /etc/bind/net.localnet:
```
;
; dns zone for for localnet
;

$TTL 1D

; any time you make a change to the domain, bump the
; "serial" setting below. the format is easy:
; YYYYMMDDI, with the I being an iterator in case you
; make more than one change during any one day

@ IN SOA localnet. hostmaster.localnet. (

201211022 ; serial

8H ; refresh
4H ; retry
4W ; expire
1D ) ; minimum
IN A 172.16.254.10
;
@ IN NS hermes.localnet.
athena          IN      A       172.16.254.13
ceres           IN      A       172.16.254.11
pluto           IN      A       172.16.254.10
trinity         IN      A       172.16.254.12

; bla           IN      CNAME   pluto ; Example of a CNAME record, if necessary
; www           IN      A       172.16.254.10 ; Example of a www record
```


On my client, I ran nmcli dev list iface eth3 to check the servers:
```
GENERAL.DEVICE:                         eth3
GENERAL.TYPE:                           802-3-ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82577LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 2.0.0-k
GENERAL.FIRMWARE-VERSION:               0.12-1
GENERAL.HWADDR:                         5C:26:0A:20:F3:77
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth3
GENERAL.IP-IFACE:                       eth3
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     /org/freedesktop/NetworkManager/ActiveConnection/25
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 172.16.254.236/24, gw = 172.16.254.1
IP4.DNS[1]:                             172.16.254.10
IP4.DNS[2]:                             172.16.254.1
IP4.DOMAIN[1]:                          localnet
DHCP4.OPTION[1]:                        domain_name = localnet
DHCP4.OPTION[2]:                        expiry = 1351994941
DHCP4.OPTION[3]:                        broadcast_address = 172.16.254.255
DHCP4.OPTION[4]:                        dhcp_message_type = 5
DHCP4.OPTION[5]:                        dhcp_lease_time = 86400
DHCP4.OPTION[6]:                        ip_address = 172.16.254.236
DHCP4.OPTION[7]:                        routers = 172.16.254.1
DHCP4.OPTION[8]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[9]:                        domain_name_servers = 172.16.254.10 172.16.254.1
DHCP4.OPTION[10]:                       network_number = 172.16.254.0
DHCP4.OPTION[11]:                       dhcp_server_identifier = 172.16.254.10

```

But it still can't ping local network devices...

---

### Post by SeijiSensei on 2012-11-03
Your named.conf uses forwarders, so requests won't be handled by the local server.  Try removing the forwarders directive in named.conf.options.

---

### Post by jlacroix on 2012-11-03
> **SeijiSensei said:**
> Your named.conf uses forwarders, so requests won't be handled by the local server.  Try removing the forwarders directive in named.conf.options.
Are you sure? I thought that just meant that if it doesn't find what you want locally, it will look it up via the forwarders next. For example, if I ping "www.yahoo.com" it will look in the local database, not find it, and then go to the forwarding address.

Regardless, I removed it, but it didn't fix it.

---

### Post by SeijiSensei on 2012-11-03
Are you sure bind9 is listening on the 172 IP address?  Restart bind9 with "sudo service bind9 restart" then look in /var/log/syslog.  You might need to add a "listen-on" option with all the addresses specified.

What if you are on the machine itself and use the "host" command?  Try running "host www.google.com" and see what IP server it says it is using.  It should send the request to localhost (127.0.0.1).  Now tell it to use the server's 172 address by running "host [www.google.com](www.google.com) 172.16.254.10".  Does that work?

There is no need to use forwarders except in very unusual circumstances.  If you send a request for "www.yahoo.com" to your local nameserver, it will query the root nameservers for the NS records for yahoo.com and send the request there directly.  It will also add this information to its local cache for later reuse.  I've run DNS servers on local networks for years and never used forwarders except in some very narrow cases.  (For instance, I have a VPN connection to a client's network.  I have an entry in named.conf for that client's domain with a specific forwarders rule to send queries for that domain to the client's internal nameserver.)

---

### Post by jlacroix on 2012-11-03
> **SeijiSensei said:**
> Are you sure bind9 is listening on the 172 IP address?  Restart bind9 with "sudo service bind9 restart" then look in /var/log/syslog.  You might need to add a "listen-on" option with all the addresses specified.

What if you are on the machine itself and use the "host" command?  Try running "host www.google.com" and see what IP server it says it is using.  It should send the request to localhost (127.0.0.1).  Now tell it to use the server's 172 address by running "host [www.google.com](www.google.com) 172.16.254.10".  Does that work?

There is no need to use forwarders except in very unusual circumstances.  If you send a request for "www.yahoo.com" to your local nameserver, it will query the root nameservers for the NS records for yahoo.com and send the request there directly.  It will also add this information to its local cache for later reuse.  I've run DNS servers on local networks for years and never used forwarders except in some very narrow cases.  (For instance, I have a VPN connection to a client's network.  I have an entry in named.conf for that client's domain with a specific forwarders rule to send queries for that domain to the client's internal nameserver.)
It appears that it is listening on that address, if I am reading this correctly:

tail -n 100 /var/log/syslog | grep listening:
```
Nov  3 13:04:44 Pluto named[2654]: listening on IPv6 interfaces, port 53
Nov  3 13:04:44 Pluto named[2654]: listening on IPv4 interface lo, 127.0.0.1#53
Nov  3 13:04:44 Pluto named[2654]: listening on IPv4 interface br0, 172.16.254.10#53

```

If I run the "host" command on the DNS server, it doesn't declare what DNS it is using. If I use the host command with the IP address of the server on my local machine, DNS works. But, if I want to ping any local machine, it won't respond and the external DNS responds instead.

So now, if I want to do:
vnc://pluto:1
That won't work. I instead have to do:
vnc://172.16.254.10:1
In order to use VNC to connect to my server.

What really boggles me is that these same config files worked fine on my dedicated DNS server (which I decommissioned) and that server worked flawlessly. I use the exact same DNS config files, so maybe I'm missing one or maybe the configuration is invalid somewhere?

In regards to fowarders, Another reason I use them is for OpenDNS. If I don't declare that, it would just default to my ISPs DNS and not OpenDNS, wouldn't it?

---

### Post by jlacroix on 2012-11-03
Solved. 

I went through my config files many times, making sure that there were no references to the old DNS server. However, a simple grep command showed that I missed two instances. I changed them to the correct host name, and it's solved.

Deep down I knew it had to be something silly on my side. Sorry guys.

---

