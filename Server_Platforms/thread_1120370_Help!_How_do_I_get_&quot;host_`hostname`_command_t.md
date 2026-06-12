---
title: "Help!? How do I get &quot;host `hostname` command to come back with my private IP address?"
date: 2009-04-08
forum: Server Platforms
---

### Post by Linuxwho? on 2009-04-08
**It is showing up with some other address and I need it to come up with the internal IP of 192.168.1.110.**

**"root@ubuntu:/etc#** host `hostname`
ubuntu has address 63.251.179.13
ubuntu has address 8.15.7.117
[B]Host ubuntu not found: 3(NXDOMAIN)
root@ubuntu:/etc#[/B]"
------
**Here's my network entry:**
# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.1.110
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

-------
[B]and I ping my servername "ubuntu" and it comes back with the 110 address just fine.

Here is my named.conf file..should it be populated? Is my server acting as a DNS server? Dumb question but I think the answer is yes?
[/B]
"// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

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

---------
**Here is named.conf.local**

"//
zone "mydomain.com" {
type master;
file "/etc/bind/db.mydomain.com";
};
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
---------
**Here is DB.mydomain.com:**
;
; Bind data file for mydomain.com
;
$TTL 604800
@ IN SOA mail.mydomain.com. admin.mydomain.com. (
070725 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS mail
IN MX 10 mail
IN A 192.168.1.110
mail IN A 192.168.1.110

---

### Post by volkswagner on 2009-04-09
I am not sure what the command does.  When I perform that type of synatax I get the same unknown IP address, no matter what I substitute for 'hostname'.  I don't get the samme IP as you, just the same for all my queries.

I think you want to run the following:

```
hostname
```

```
hostname -f
```

---

### Post by BkkBonanza on 2009-04-09
That command works for me - returns 192.168.0.103. But my hostname is assigned using dhcp by my router. That is typical for local networks though, rather using dns. I don't think that your hostname will be assigned at all by using dns. I have a setting in my dhclient.conf that tells it to get the hostname.

If you are just concerned with getting your ip address however it's assigned then you could use (assuming eth0, chg if need),

ifconfig eth0 | grep "inet addr:" | cut -d':' -f2|awk '{print $1}'

---

### Post by Linuxwho? on 2009-04-09
Thanks guys.  I am installing Zimbra 5.0.14 and they are suggesting it be the final requirement prior to installing it.  I have assigned myself a static IP.  I have to read more about how ubuntu 8.04 does DNS as I know very little although I installed it during set up.


Thanks BkkBonaza.  What does this do?  
"ifconfig eth0 | grep "inet addr:" | cut -d':' -f2|awk '{print $1}' "

I used sudo aptitude and it says "bind9host" is installed.  So I guess that is like DNS in windows? UPDATE - ok, after doing some reading, in the resolv.conf file it says the server is refering to istelf for dns.

---

### Post by BkkBonanza on 2009-04-09
That command looks at your interface config and gets your ip address. Assuming your primary interface is eth0 it should return the ip address same as host `hostname` would do. 

I'm not sure what your overall goals with this are and how big a network you are setting up or managing. I have to ask: why do you want to run DNS? You do not have to run your own DNS server and it's generally a big resource hog and hassle to setup and run. If you're thinking you need it to run a web server and other services then that is not correct. For public ips it's much easier to use an external server and there are so many free ones around now it generally makes sense that way. For local LAN nameserving and address management it is more common to let the dhcp server on your router do the work. A typical setup is to put the address of your router in /etc/resolv.conf so that name lookups get referred to your router running dhcp. It then refers to either your isp nameserver or some other public one. There are some reasons why it would make sense to run it on your server but it's not by any means mandatory. Most routers today would run a dnsmasq server that is sufficient for a small LAN setup. I run mail on my servers but don't usually install DNS unless I have a special need. My servers are small vps accounts so cutting back on less needed resource use is very helpful. Sorry, not trying to rain on your parade but just give you some more info.

Another thing about dnsmasq/dhcp - you do not have to have static ip for a server if you config the dhcp to assign a static lease - just an entry on the router. This way it always assigns the same ip during the dhcp process. This makes lan management a lot easier as you add/remove machines.

---

### Post by Linuxwho? on 2009-04-09
I am using this in a test environment only.  I think it is called split DNS but have no idea really.  Selecting DNS was one of the requirements.

I don't see how having an entry in named.conf is  causing a heavy resource usage especially in the test environment ?

---

### Post by BkkBonanza on 2009-04-10
Use **top** to see how much memory named is using. If you have 1G then it's not likely a problem. When you start serving a lot of names and cache many requests it grows and if you need resources for web serving and mysql and php then it can be an issue. Particularly on a small vps account where you only have 128MB (or less sometimes, the smallest ones being 32MB or 64MB). 

I ran pdns for a brief test and it was using 70MB of RAM. Apparently named uses more. The only DNS server I use now is TinyDNS and it takes about 1-2 MB. In a test environment you can do whatever you like. If you're mainly doing this to learn about named then go ahead, I'm not discouraging that.

---

### Post by Linuxwho? on 2009-04-11
> **BkkBonaza said:**
> Use **top** to see how much memory named is using. If you have 1G then it's not likely a problem. When you start serving a lot of names and cache many requests it grows and if you need resources for web serving and mysql and php then it can be an issue. Particularly on a small vps account where you only have 128MB (or less sometimes, the smallest ones being 32MB or 64MB). 

I ran pdns for a brief test and it was using 70MB of RAM. Apparently named uses more. The only DNS server I use now is TinyDNS and it takes about 1-2 MB. In a test environment you can do whatever you like. If you're mainly doing this to learn about named then go ahead, I'm not discouraging that.

Wow that is a cool command!  It shows I am using a total of 74m out of 1gig.  (I guess cuz small test env)  Thanks very much for the advice.  :guitar:

---

### Post by BkkBonanza on 2009-04-11
There's a nicer version called **htop** but it's not installed by default. Also another interesting one is **atop** (apache top) which shows page request stats as they occur. And **mtop** does similar for mysql. I'm not sure those ones are available as packages though - may require compiling from source.

---

### Post by Linuxwho? on 2009-04-12
Thanks.  I forgot I am still left with my original issue though.

---

