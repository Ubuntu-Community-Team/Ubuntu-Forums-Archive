---
title: "[SOLVED] noob needs help with dns server"
date: 2008-09-30
forum: Server Platforms
---

### Post by meomike2000 on 2008-09-30
i need to set up a dns server for my network.

any advice would help, i am still fairly new at linux, tryin to break away from windows. so please be specific.

tia.......

---

### Post by Xipher on 2008-10-01
Could you provide some additional information. With this be a caching DNS server (just handling queries for hosts on your network for other domains), or will it be authoritative (hosting the records for a domain you own/operate)?

---

### Post by lykwydchykyn on 2008-10-01
If your network is fairly small, DNSmasq is a good choice.  It must be configured by editing the config file, but that's not as hard as it sounds.

The other option is BIND9, which is more or less an industry standard.  There are several graphical front-ends for it, but even with those you need a bit of understanding of some terminology and architecture of BIND (zones, views, etc).

---

### Post by meomike2000 on 2008-10-01
well i need the server to handle dns for multiple domains, or at least give me the option to. i should be able to handle the setups and some of the configs, just need some advice of what to use. i know a good bit about networking just never had to with linux of any type, im a windows guy tryn to change over. i have a server that i have set up that will handle the site/sites. at this time there is no internet server pointing to it. i am using other computers on the network to simulate. i can access it by using the ip address from any of them, windows, ubuntu. dont matter. bu i need a name server to handle the request and point to it when u use the site name.

hope that makes sense and hope u can help.

---

### Post by orotrev on 2008-10-01
BIND is really not that difficult to setup. The first thing to do is:
```
sudo apt-get install bind
```
Once you have BIND installed take a look at the config files found in /etc/bind. Then check out
[http://www.isc.org/index.pl?/sw/bind/index.php]("http://www.isc.org/index.pl?/sw/bind/index.php")
This is the official documentation for BIND. I used this when I setup BIND for the first time. I was able to have a working DNS server in about an hour. Always remember to start with the basics and then add to your config as your knowledge grows. Unless this is a production server, in which case get it all setup right before you open it to the internet.

---

### Post by windependence on 2008-10-02
If you are just trying to point your sites at your IP(s) then you most likely don't need any local DNS. You would point your domains at your servers using your registrar's DNS servers in your control panel for your registrar.

Unless you have 100s of local servers, it's generally not necessary to run your own DNS.

-Tim

---

### Post by smullie on 2008-10-02
I have documented my own install of DNS and DHCP with dynamic updates as follow.
Use the correct ip addresses and names.

DNS Server
Run
	apt-get install bind9
For security reasons we want to run BIND chrooted so we have to do the following steps: 
	/etc/init.d/bind9 stop
Edit the file /etc/default/bind9 so that the daemon will run as the unprivileged user bind, chrooted to /var/lib/named. Modify the line: OPTIONS="-u bind" so that it reads OPTIONS="-u bind -t /var/lib/named":
	nano /etc/default/bind9
OPTIONS="-u bind -t /var/lib/named"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes

Create the necessary directories under /var/lib: 
	mkdir -p /var/lib/named/etc
	mkdir /var/lib/named/dev
	mkdir -p /var/lib/named/var/cache/bind
	mkdir -p /var/lib/named/var/run/bind/run
Then move the config directory from /etc to /var/lib/named/etc:
	mv /etc/bind /var/lib/named/etc
Create a symlink to the new config directory from the old location (to avoid problems when bind gets updated in the future): 
	ln -s /var/lib/named/etc/bind /etc/bind
Make null and random devices, and fix permissions of the directories: 
	mknod /var/lib/named/dev/null c 1 3
	mknod /var/lib/named/dev/random c 1 8
	chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
	chown -R bind:bind /var/lib/named/var/*
	chown -R bind:bind /var/lib/named/etc/bind
We need to modify /etc/default/syslogd so that we can still get important messages logged to the system logs. Modify the line: SYSLOGD="" so that it reads: SYSLOGD="-a /var/lib/named/dev/log":
	nano /etc/default/syslogd
#
# Top configuration file for syslogd
#

#
# Full documentation of possible arguments are found in the manpage
# syslogd(8).
#

#
# For remote UDP logging use SYSLOGD="-r"
#
SYSLOGD="-a /var/lib/named/dev/log"

Restart the logging daemon: 
	/etc/init.d/sysklogd restart
Start up BIND, and check /var/log/syslog for errors:
	/etc/init.d/bind9 start
	tail /var/log/syslog

For dynamic update and standard settings do the folloing:
Edit /etc/bind/named.conf.local as below:
	nano /etc/bind/named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# allow dns updates from localhost with key "rndc-key"
include "/etc/bind/rndc.key";
controls {
        inet 127.0.0.1 port 953
                allow {localhost; } keys { "rndc-key"; };
};

#defines example.com
zone "example.com" {
  type master;
    file "/etc/bind/db.example.com";
    allow-update { key "rndc-key"; };
};

#defines our local subnet 192.168.1.0/24
zone "1.168.192.in-addr.arpa" {
  type master;
  file "/etc/bind/db.1.168.192";
  allow-update { key "rndc-key"; };
};

Edit /etc/bind/named.conf.options as below, but change ip addresses acording to the one u need:
	nano /etc/bind/named.conf.options

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        Forwarders { // replace x with your isp dns ip addresses
                xx.xx.xx.x;
                xx.xx.xx.x;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


Create a file db.example.com as below
	nano /etc/bind/db.example.com

;
; Zone file for example.com
;
; The full zone file
$ORIGIN .
$TTL 259200     ; 3 days
example.com              IN SOA  ns.example.com. postmaster.example.com. (
                                200806525  ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      ns.example.com.
                        MX      10 mail.example.com.
$ORIGIN example.com.
mail                    A       192.168.1.2 ; this is for as this server is also the mailserver
ns                      A       192.168.1.2
$TTL 259200     ; 3 days
router                  A       192.168.1.1
server1                 A       192.168.1.2 ; this is this server
host1                   A       192.168.1.101 ; this is an example for static adresses

Create a file db.1.168.192 as below
	nano /etc/bind/db.1.168.192 

$ORIGIN .
$TTL 259200     ; 3 days
1.168.192.in-addr.arpa  IN SOA  example.com. postmaster.example.com. (
                                200806445  ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      ns.example.com.
                        PTR     example.com.
$ORIGIN 1.168.192.in-addr.arpa.
1                       PTR     router.example.com.
2                       PTR     server1.example.com. ; This is this server
                        PTR     ns.example.com.
                        PTR     mail.example.com.  ; this is for as this server is also the mailserver
101                     PTR     host1.example.com.  ; this is an example for static adresses

Modify /etc/resolv.conf, and add the DNS server to it:
	nano /etc/resolv.conf

search example.com
nameserver 192.168.1.1


DHCP3 Server
Run
	apt-get install dhcp3-server 
	/etc/init.d/dhcp3-server stop 
	mv /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.conf.org
	nano /etc/dhcp3/dhcpd.conf
Put text below in the new file

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
# Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0";

# naming the server
# and enabling ddns
server-identifier example.com;
authoritative;

ddns-update-style interim;

include "/etc/bind/rndc.key";

# Use what key in what zone
zone    1.168.192.in-addr.arpa. {
    primary server1.example.com ;
    key             "rndc-key";
  }
zone    example.com. {
    primary server1.example.com ;
    key             "rndc-key";
  }

# Standard DHCP settings
default-lease-time 14400;
max-lease-time 28800;
log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.50 192.168.1.100;
  option routers  router.example.com ;
  option broadcast-address 192.168.1.255;
  option domain-name "example.com";
  option domain-name-servers 192.168.1.2;
  option netbios-name-servers 192.168.1.2;
  }

#static addresses
# host1
#  host host1 {
#  hardware ethernet xx:xx:xx:xx:xx:xx;
#  fixed-address 192.168.1.101;
#  }


change group of /etc/bind/rndc.key to dhcpd, so dhcp server can read the key.

Start the dhcp server
	/etc/init.d/dhcp3-server start 
Check the syslog file for errors
	tail /var/log/syslog

Thats All....

---

### Post by meomike2000 on 2008-10-03
thank you.

---

### Post by hu5h on 2008-10-11
thanks a lot!
but shouldnt there be an extra trailing dot "." after example.com in the zone-file?
I followed this but couldn do a lookup. Ran "nslint" to see what was wrong and it said a whole lot of stuff, including the missing dot.
 
I now have everything working. Thansk a bunch.

---

### Post by meomike2000 on 2008-10-12
i need to add a slave zone to point to a server on my network called web1
its static address is xx.xx.x.xxx.

can somebody help me add this zone into named.conf.local and give me an example of what the file should look like for a slave zone.

thanks mike

---

### Post by smullie on 2008-11-12
Mike,

There was an error here:
;
; Zone file for example.com
;
; The full zone file
;$ORIGIN .

last line sould be:
$ORIGIN .
so without the ; (comment)

To add an static address you have to use the line like host1
host1 is an example, just for static addresses.
so in db.example.com and in db.1.168.192
you sould add in db.example.com:
web1 A xx.xx.x.xxx
and in 
db.1.168.192:
xxx PTR web1.example.com.

the xxx are the last octet e.g: from 192.168.1.151 you should enter 151

---

