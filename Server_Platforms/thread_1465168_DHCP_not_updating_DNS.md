---
title: "DHCP not updating DNS"
date: 2010-04-29
forum: Server Platforms
---

### Post by BarryDocks on 2010-04-29
Help!!  I have been trying to get a dynamic DNS server set up.  I have followed these 2 guides:
[http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/]("http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/")
[http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/]("http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/")
which works as a caching nameserver but does the dhcp server does not update the DNS server. 

Any suggestions would be greatly appreciated, Thanks. 

Contents of dhcp3.conf:
```
ddns-updates on;
# Make sure to change the ddns update style to interim:
ddns-update-style interim;
ignore client-updates;
ddns-domainname "daviesandjones.lan.";
ddns-rev-domainname "in-addr.arpa.";

key DHCP_UPDATER {
	algorithm HMAC-MD5.SIG-ALG.REG.INT;
	# Also note that the key should be surrounded by quotes.
	secret "mAWhzcn8N9+QJEAE3zpJog==";
	}

zone daviesandjones.lan. {
  primary 10.10.64.1;
  key DHCP_UPDATER;
}

zone 64.10.10.in-addr.arpa. {
  primary 10.10.64.1;
  key DHCP_UPDATER;
}

option host-name "Server64";
option domain-name "daviesandjones.lan";
ddns-hostname "Server64";

authoritative;
#option domain-name-servers 208.67.222.222, 208.67.220.220;
option domain-name-servers 10.10.64.1;

option wpad-url code 252 = text;
option wpad-url "http://10.10.64.1/wpad.dat";

# LAN1
subnet 10.10.64.0 netmask 255.255.255.0 {
	deny unknown-clients;
	max-lease-time 604800;
	default-lease-time 604800;
	option ntp-servers 10.10.64.1;
	option time-servers 10.10.64.1;
	option routers 10.10.64.1;
	option subnet-mask 255.255.255.0;
	option ip-forwarding off;
	# Wireless Access Point
	host AcccesPt {
		max-lease-time 31536000;
		default-lease-time 31536000;
		hardware ethernet 00:1C:DF:13:B6:09;
		fixed-address 10.10.64.2;
		}
	# Brother HL-2030 Printer
	host HL2030 {
		max-lease-time 31536000;
		default-lease-time 31536000;
		hardware ethernet 00:40:71:00:56:f9;
		fixed-address 10.10.64.20;
		}
	pool {
		max-lease-time 43200;
		default-lease-time 43200;
		range dynamic-bootp 10.10.64.20 10.10.64.25;
		allow unknown-clients;
		deny known-clients;
		}
	range dynamic-bootp 10.10.64.10 10.10.64.19;
	}

# Nats Laptop (WiFi)
host NatsLaptopWiFi {
	hardware ethernet 00:16:44:ae:45:d1;
	}
# Adrian's Laptop (WiFi)
host AdeLaptopWiFi {
	hardware ethernet 00:16:44:e7:a1:8c;
	}
# Adrian's Laptop
host AdeLaptop {
	hardware ethernet 00:21:70:91:c4:23;
	}
# Wii
host Wii {
	hardware ethernet 00:22:4c:05:a9:51;
	}
# Blackberry
host Blackberry {
	hardware ethernet 00:21:06:ba:e6:d5;
	}

```

Contents of named.conf.local:
```
# The secret key used for DHCP updates.
key DHCP_UPDATER {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;

    # Important: Replace this key with your generated key.
    # Also note that the key should be surrounded by quotes.
    secret "mAWhzcn8N9+QJEAE3zpJog==";
};


zone "daviesandjones.lan" IN {
    type master;
    file "/var/lib/bind/daviesandjones.lan.db";
    allow-update { key DHCP_UPDATER; };
};

zone "64.10.10.in-addr.arpa" {
    type master;
    file "/var/lib/bind/rev.64.10.10.in-addr.arpa";
    allow-update { key DHCP_UPDATER; };
};



// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
```

contents of daviesandjones.lan.db:
```
$ORIGIN .
$TTL 86400      ; 1 day
daviesandjones.lan      IN      SOA     server64.daviesandjones.lan. hostmaster$
                        2008080910
                        28800
                        14400
                        2419200
                        86400 )
                        NS      server64.daviesandjones.lan.
                        MX      10 server64.daviesandjones.lan.
$ORIGIN daviesandjones.lan.
bzr                     CNAME   server64
daviesandjones.lan      IN      A       10.10.64.1
server64.daviesandjones.lan.    IN      A       10.10.64.1

```

contents of rev.64.10.10.in-addr.arpa:
```
$ORIGIN .
$TTL 86400      ; 1 day
64.10.10.in-addr.arpa   IN      SOA     server64.daviesandjones.lan. hostmaster$
                        2008080906
                        28800
                        14400
                        2419200
                        86400 )
                        NS      server64.daviesandjones.lan.
$ORIGIN 64.10.10.in-addr.arpa.
1                       PTR     server64.daviesandjones.lan.

```

---

### Post by BarryDocks on 2010-04-29
Also found the following in the syslog:
```
Apr 29 12:30:43 Server64 named[6597]: client 10.10.64.1#49760: updating zone 'daviesandjones.lan/IN': update unsuccessful: Server64.daviesandjones.lan: 'name not in use' prerequisite not satisfied (YXDOMAIN)
Apr 29 12:30:43 Server64 named[6597]: client 10.10.64.1#46268: updating zone 'daviesandjones.lan/IN': update unsuccessful: Server64.daviesandjones.lan/TXT: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)
Apr 29 12:30:43 Server64 dhcpd: Forward map from Server64.daviesandjones.lan. to 10.10.64.15 FAILED: Has an A record but no DHCID, not mine.
Apr 29 12:30:43 Server64 dhcpd: DHCPREQUEST for 10.10.64.15 from 00:16:44:e7:a1:8c (adrian-laptop) via eth1
Apr 29 12:30:43 Server64 dhcpd: DHCPACK on 10.10.64.15 to 00:16:44:e7:a1:8c (adrian-laptop) via eth1
Apr 29 12:30:47 Server64 nmbd[5965]: [2010/04/29 12:30:47, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172) 
Apr 29 12:30:47 Server64 nmbd[5965]:   process_name_refresh_request: unicast name registration request received for name NATALIELAPTOP<20> from IP 10.10.64.17 on subnet UNICAST_SUBNET. 
Apr 29 12:30:47 Server64 nmbd[5965]: [2010/04/29 12:30:47, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173) 
Apr 29 12:30:47 Server64 nmbd[5965]:   Error - should be sent to WINS server 
Apr 29 12:30:47 Server64 nmbd[5965]: [2010/04/29 12:30:47, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172) 
Apr 29 12:30:47 Server64 nmbd[5965]:   process_name_refresh_request: unicast name registration request received for name NATALIELAPTOP<00> from IP 10.10.64.17 on subnet UNICAST_SUBNET. 
Apr 29 12:30:47 Server64 nmbd[5965]: [2010/04/29 12:30:47, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173) 
Apr 29 12:30:47 Server64 nmbd[5965]:   Error - should be sent to WINS server 
Apr 29 12:30:47 Server64 nmbd[5965]: [2010/04/29 12:30:47, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172) 
Apr 29 12:30:47 Server64 nmbd[5965]:   process_name_refresh_request: unicast name registration request received for name WORKGROUP<00> from IP 10.10.64.17 on subnet UNICAST_SUBNET. 
Apr 29 12:30:47 Server64 nmbd[5965]: [2010/04/29 12:30:47, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173) 
Apr 29 12:30:47 Server64 nmbd[5965]:   Error - should be sent to WINS server 

```

---

### Post by HermanAB on 2010-04-29
Hmmm, usually one wants to eliminate security holes, not deliberately create them.

I suggest that you reconsider.

---

### Post by BarryDocks on 2010-04-29
> **HermanAB said:**
> Hmmm, usually one wants to eliminate security holes, not deliberately create them.

I suggest that you reconsider.
Care to expand?

---

### Post by Iowan on 2010-04-29
I use DNSMasq for DHCP/DNS on my home network. It integrates the two, but I've no idea how expandable it might be.

---

### Post by BarryDocks on 2010-04-30
Had a go with dnsmasq but couldn't get it to work and I had already spent time setting up dhcp.

Any way have now been successful after following these guides:
[http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable]("http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable")
[https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html#dns-primarymaster-configuration]("https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html#dns-primarymaster-configuration")
which probably give a more secure result as the rdnc key is not exposed?

---

### Post by HermanAB on 2010-04-30
Howdy,

Allowing an unauthenticated client to update a server is usually not a good idea.

Microsoft does this with their hacked version of BIND, but all large installations disable it.

---

