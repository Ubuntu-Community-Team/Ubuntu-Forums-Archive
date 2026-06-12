---
title: "dhcp3-server ddns-update failes :-("
date: 2005-04-20
forum: Server Platforms
---

### Post by mjpowersjr on 2005-04-20
Hello,

I am running hoary as both  a dns server (a la bind9) and a dhcp server ( a la dhcp3-server) both work fine independently.... I am tring to configure dhcpd to automatically update bind with a hostnames information when a lease is aquired. Using google lead me to people that where recieving errors when dhcpd tries to update the dns information, but i am recieving no such errors in my /var/log/syslog file. It appears that dhcpd is blowing off the ddns settings. I have attached my bind and dhcp configuration files below. This is my first time setting up a dhcp and dns server, so any help would be appreciated. 

Also btw, a windows xp client can register itself fine w/ dns 
and a manual update of a client nix machine via nslookup works also.
but the dhcpd server should be doing this automatically, not leaving it to the cleints.

> mike@pserver:/etc/bind$ cat named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "powers.home" {
        type master;
        notify no;
        file "/var/cache/bind/db.powers.home";
        allow-update {192.168.0/24;};
};

zone "192.168.0.in-addr.arpa" {
        type master;
        notify no;
        file "/var/cache/bind/db.192.168.0";
};

> 
mike@pserver:/etc/bind$ cat db.powers.home
;
; Zone file for powers.home
;
; The full zone file
;
$TTL 3D
@       IN      SOA     ns.powers.home. root.powers.home. (
                        200504131       ; serial, todays date + todays serial #
                        8H              ; refresh seconds
                        2H              ; retry seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
        NS      ns
        MX      10 mail                 ; primary mail exchange
        MX      20 mjpowersjr.gmail.com.; secondary mail exchange
;
localhost       A       127.0.0.1
ns              A       192.168.0.2
mail            A       192.168.0.2

linksysrouter   A       192.168.0.1
                TXT     "linksysrouter"



> mike@pserver:/etc/dhcp3$ cat dhcpd.conf

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)

ddns-updates on;
ddns-update-style interim;
ddns-domainname "powers.home";
update-static-leases on;
ignore client-updates;

authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  option domain-name-servers 192.168.0.2;
  option domain-name "powers.home";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}


---

### Post by mjpowersjr on 2005-04-22
Just to give an update, I have figured out the problem, everything seems to work great now. :-) I had to tweak a few things in the dhcpd.conf file, and tweak the ubuntu  clients also. Basically I thought that when a client was assigned an ip address from the server, bind would say "hey man, whats your hostname???" and update the dns zone files accordingly, but your actually have to edit the clients configuration to make the clients say "hey hear i am, give me an ip, and btw, my hostname is ........" This week has been kinda crazy, but if anyone is interested I could write up a guide as to how I got everything working.

p.s. Ubuntu Rocks!

-mike powers

---

### Post by fduplex on 2005-04-24
I just ran into the same situation, i've spent hours trying to get it working. Both DHCP and BIND are working fine by themselves but no matter what I try it seems dhcpd isn't even attempting to update the zones. I've gone over everything I can find in the dhcpd/bind docs and google, and I was convinced it was a bug.

How did you manage to get it working?

**Edit**: nevermind, I had a closer look at your config files and compared them to mine, I figured out the problem. Everything seems to be working :) thanks.

---

