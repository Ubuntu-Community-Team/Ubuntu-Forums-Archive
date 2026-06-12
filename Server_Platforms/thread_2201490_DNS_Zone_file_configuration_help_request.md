---
title: "DNS Zone file configuration help request"
date: 2014-01-24
forum: Server Platforms
---

### Post by Ron Jones on 2014-01-24
SITUATION:

I am on Ubuntu 12.04.4 LTS

Since the release of 12.04, I have had a local network consisting of DHCP server (also running Bind9 and configured as 'master' for the devices on the 192.168.x.x network here at home), a web server, and a mail server.

I'm switching ISP's (someone ran fiber to our neighbourhood, and I can ditch Comcast business). 

****The trouble is, now I must move my hosting off-site (still saves money though ;-) ).

CONCERN:

All of the devices on my local network (PCs, laptops, smart phones, iPads, video games) receive their network configuration from the DHCP/DNS server. AND...they are part of the mydomain.us network. Which means, my desktop (office.mydomain.us), the firewall (firewall.mydomain.us), and the computer my son uses (mario.mydomain.us) are all part of the same domain of which [www.mydomain.us](www.mydomain.us) is a part.

Although I have only moved Mail and WWW offsite, I am worried that there will be conflicts or issues (not for the rest of the world...SecuritySpace points them to the website)...but for us, inside the Local Area Netowrk...because part of the network behind the firewall, and part of it is outside.

I have made a couple of  changes in /var/lib/bind/db.mynetworkname.us that seems to help.

1. I removed the MX record entry that was MX 10 mail.mydomain.us (the mail client now points to the hosting company's domain)
2. I added: www  CNAME dallas06.hostingcompanydomain.com. 
3. I added: mail  CNAME dallas06.hostingcompanydomain.com. (This is for webmail access, which I don't use...though I haven't gotten this right yet, as the hosting company's instructions specify going to [https://mydomain.us:2096](https://mydomain.us:2096) to log-in to webmail... and I'm not sure how to redirect that in a zine file.

QUESTIONs:

Is it really that simple? just a CNAME entry in the zone file? Any caveats or gotchas?

An idea if it's possible to make a CNAME (or other) entry in my zone file to enable sending traffic offsite for webmail access? currently, when I use [https://mydomain.us:2096](https://mydomain.us:2096), I get a network error. I suspect that this is because everything in the zone file is mydomain.us and ONLY mail & www are off site (mail works fine in Thunderbird, etc. But just in case someone at home wanted to use web access, I'd like to make it work.

Thanks,

---

### Post by CharlesA on 2014-01-25
The way I have my network setup is similar, but I only have A records set up for local DNS. Example:

dig ubuntu.charles.net = 192.168.1.200, but if I try to run dig on a host that is not listed on the internal zone, it will forward those requests to external DNS servers, which resolve the public IP of that host.

I would probably be running dnsmasq instead of bind9 if you need DHCP+DNS though.

---

### Post by Ron Jones on 2014-01-26
Good tip, thanks. I've been researching dnsmasq since reading your post. It's definitely a possibility.

Currently, I'm using Bind9+dhcpd together. It works...but... I'm a big fan of the KISS principle.

---

### Post by SeijiSensei on 2014-01-27
I run two separate BIND name servers for my primary domain, one on my publicly-visible virtual server at Linode, and another on my local network's server.  The public server is registered as authoritative via my domain registrar.  (Actually I have two virtual servers, one on each coast, in part to comply with the [requirement]("http://www.zoneedit.com/doc/rfc/rfc1912.txt") that all domains have a minimum of two publicly-visible domain servers.)  The internal server has local entries for things like NS and MX, as well as forwarding queries for a client's domain over a VPN to the client's internal nameserver.  (That client also maintains separate public and private servers, the latter being an Active Directory server.)

---

### Post by Ron Jones on 2014-01-29
Okay... so I made some changes, and let it run for a few days to see if there were any hiccups. So far so good (except for a tiny problem I will detail at the end).

I thought I'd share my experience, and configuration, in case someone else ever has this headache:

First, some perspective: Attached to this post, see the file "jonesNet.png." The two servers named "Tigger" and "Pooh" (yes, I have small children) were the www and email servers respectively; while "minister" is the utility server that provides DNS, DHCP, RADIUS authentication and etc.

My DNS server is behind a firewall with the rest of the network. So, while it is configured as authoritative. It is only authoritative to the computers on my LAN. The outside world does not see behind the firewall. 
--Though, formerly, I had a DNS provider that pointed all www and email traffic to the WAN interface of my firewall. As that is no longer necessary, those holes have been plugged. And if you want my www presence, it is handled by the hosting company's DNS server.

NOW, after switching from Comcast business Internet service to TDS telecom (fiber to the curb) meant no more static IP (it's a residential account), but it's cheaper enough that + offsite hosting was still less overall than Comcast.

HOWEVER...what to do about the network, and DNS server?

In the end, the changes were minor, and this is what they look like:

/etc/bind/named.conf (-rw-r--r-- 1 bind:bind)
-----------------------------------------------------
```
key "rndc-key" {
       algorithm hmac-md5;
       secret "mysupersecretkeyhere";
};
controls {
       inet 127.0.0.1 port 953
               allow { 127.0.0.1; } keys { "rndc-key"; };
};
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
```



/etc/bind/named.conf.local (-rw-r--r-- 1 bind:bind)
-----------------------------------------------------------
```
/Secret key used for DHCP updates
key DHCP_UPDATER {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;
    # Important: Replace this key with your generated key.
    # Also note that the key should be surrounded by quotes.
    secret "mysupersecretkeyhere";
};
//
// Do any local configuration here
//
zone "familynetwork.us" {
type master;
file "/var/lib/bind/db.familynetwork.us";
allow-update { key DHCP_UPDATER; };
allow-query { any; };
};

zone "29.168.192.in-addr.arpa" {
type master;
file "/var/lib/bind/db.29";
allow-update { key DHCP_UPDATER; };
allow-query { any; };
};
```



the db file (below) was where I made the bulk of the changes. Note how just adding the offsite IP address was sufficient. AND there've been no timeouts



/var/lib/bind/db.familynetwork.us (-rw-r--r-- 1 bind:bind)
--------------------------------------------------------------------
```
$ORIGIN .
$TTL 604800     ; 1 week
familynetwork.us          IN SOA  minister.familynetwork.us. ron.familynetwork.us. (
                                20140134   ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      minister.familynetwork.us.
                        A       <routable offsite IP>
                        MX      0 familynetwork.us.
$ORIGIN familynetwork.us.
$TTL 10800      ; 3 hours
android-d1d889b1bf83e4b1 A      192.168.29.129
                        TXT     "311a26c3432b6d74fee5fe0170284383c9"
$TTL 604800     ; 1 week
APJones1                A       192.168.29.3
APJones2                A       192.168.29.5
cpanel                  A       <routable offsite IP>
firewall                A       192.168.29.1
$TTL 10800      ; 3 hours
Iffound58181299         A       192.168.29.128
                        TXT     "31ba5038574666be3cdf9ca1742b8ac3ec"
$TTL 604800     ; 1 week
localhost               A       127.0.0.1
minister                A       192.168.29.2
webmail                 A       <routable offsite IP>
whm                     A       <routable offsite IP>
www                     CNAME   familynetwork.us.
```



If I run the "dig" command from my desktop, to get more information about the domain (remember, I'm asking my own DNS server, to tell me about my domain)...


dig familynetwork.us returns:



```
; <<>> DiG 9.8.1-P1 <<>> familynetwork.us
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55402
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;familynetwork.us.            IN    A

;; ANSWER SECTION:
familynetwork.us.        604800    IN    A    <routable offsite IP>

;; AUTHORITY SECTION:
familynetwork.us.        604800    IN    NS    minister.familynetwork.us.

;; ADDITIONAL SECTION:
minister.familynetwork.us. 604800    IN    A    192.168.29.2

;; Query time: 2 msec
;; SERVER: 192.168.29.2#53(192.168.29.2)
;; WHEN: Wed Jan 29 15:38:57 2014
;; MSG SIZE  rcvd: 87
```



THE ONLY PROBLEM I have is that the dhcp daemon now no longer updates the zone file. I know this, because when I ping aanother computer on the network by name, I get the "ping: unknown host <hostname>" response. 

I suspect it is a file permission/ownership issue (the 'supersecretkey' is in all the right spots....but I have not yet been able to find out how to troubleshoot the problem.



/etc/dhcp/dhcpd.conf (-rw-r----- 1 dhcpd:dhcpd)
---------------------------------------------------------
```
# DHCP.conf for familynetwork.us
#
#
ddns-update-style interim;
ignore client-updates;
ddns-domainname "familynetwork.us.";
ddns-rev-domainname "in-addr.arpa.";
# option definitions common to all
default-lease-time 86400;
max-lease-time 86400;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.29.255;
option routers 192.168.29.1;
option ntp-servers 192.168.29.2;
option domain-name-servers 192.168.29.2;
option domain-name "familynetwork.us";
# This is the official DHCP server for familynetwork.us
authoritative;
# used to send dhcp log messages
log-facility local7;

key DHCP_UPDATER {
        algorithm HMAC-MD5.SIG-ALG.REG.INT;
        secret "mysupersecretkeyhere";
};
zone familynetwork.us. {
        primary 127.0.0.1;
        key DHCP_UPDATER;
}
zone 29.168.192.in-addr.arpa. {
        primary 127.0.0.1;
        key DHCP_UPDATER;
}
allow unknown-clients;
subnet 192.168.29.0 netmask 255.255.255.0 {
range 192.168.29.100 192.168.29.150;
}
```

---

### Post by CharlesA on 2014-01-29
Thanks! You might want to put the output of some of those files in code tags for easier reading.

I tried to get bind working internally but had problems with it resolving anything that was internal after adding the forward and reverse lookup zones.

So far I haven't gone back to it to check to see what the problem could be, but I think you might have helped me solve it in any case.

---

### Post by Ron Jones on 2014-01-29
Ha! forgot the code tags. Wait one.

---

