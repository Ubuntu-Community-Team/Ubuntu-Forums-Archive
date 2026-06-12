---
title: "Squid not working"
date: 2008-01-04
forum: Server Platforms
---

### Post by cov on 2008-01-04
I cannot get squid to work on Ubuntu 7.1.

I have a DHCP server (IP 192.168.60.254, named 'Base') set uo on the Ubuntu box which is correctly allocating IPs in the range 192.168.60.100-192.168.60.199 on eth1.

I have eth0 connecting to my router/ADSL Modem and acquiring an IP through DHCP.

I have a laptop running XP (Home) connected to eth1 which reports the following in response to 'ipconfig'

```

IP Address ..........192.168.60.199
Default Gateway....192.168.60.254

```

My Squid /etc/squid/squid.conf is as follows:
```

http_port 3128 transparent
http_port 192.168.60:80 vhost vport=8080
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
acl apache rep_header Server ^Apache
access_log /var/log/squid/access.log squid
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
acl all src 0.0.0.0/0.0.0.0
acl IQNetwork src 192.168.60.0/255.255.255.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 # https
acl SSL_ports port 563 # snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl purge method PURGE
acl CONNECT method CONNECT

http_access allow IQNetwork
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
icp_access allow all
cache_effective_user squid
cache_effective_group squid
visible_hostname Base

```

My /var/log/squid/cache.log looks like this:```

2008/01/04 20:13:48| Starting Squid Cache version 2.6.STABLE14 for i386-debian-linux-gnu...
2008/01/04 20:13:48| Process ID 8698
2008/01/04 20:13:48| With 1024 file descriptors available
2008/01/04 20:13:48| Using epoll for the IO loop
2008/01/04 20:13:48| DNS Socket created at 0.0.0.0, port 32868, FD 6
2008/01/04 20:13:48| Adding nameserver 192.168.1.254 from /etc/resolv.conf
2008/01/04 20:13:48| User-Agent logging is disabled.
2008/01/04 20:13:48| Referer logging is disabled.
2008/01/04 20:13:48| Unlinkd pipe opened on FD 11
2008/01/04 20:13:48| Swap maxSize 102400 KB, estimated 7876 objects
2008/01/04 20:13:48| Target number of buckets: 393
2008/01/04 20:13:48| Using 8192 Store buckets
2008/01/04 20:13:48| Max Mem  size: 8192 KB
2008/01/04 20:13:48| Max Swap size: 102400 KB
2008/01/04 20:13:48| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2008/01/04 20:13:48| Rebuilding storage in /var/spool/squid (CLEAN)
2008/01/04 20:13:48| Using Least Load store dir selection
2008/01/04 20:13:48| Current Directory is /
2008/01/04 20:13:48| Loaded Icons.
2008/01/04 20:13:48| Accepting transparently proxied HTTP connections at 0.0.0.0, port 3128, FD 13.
2008/01/04 20:13:48| commBind: Cannot bind socket FD 14 to 192.168.0.60:80: (99) Cannot assign requested address
2008/01/04 20:13:48| Accepting ICP messages at 0.0.0.0, port 3130, FD 14.
2008/01/04 20:13:48| HTCP Disabled.
2008/01/04 20:13:48| WCCP Disabled.
2008/01/04 20:13:48| Ready to serve requests.
2008/01/04 20:13:48| Done reading /var/spool/squid swaplog (0 entries)
2008/01/04 20:13:48| Finished rebuilding storage from disk.
2008/01/04 20:13:48|         0 Entries scanned
2008/01/04 20:13:48|         0 Invalid entries.
2008/01/04 20:13:48|         0 With invalid flags.
2008/01/04 20:13:48|         0 Objects loaded.
2008/01/04 20:13:48|         0 Objects expired.
2008/01/04 20:13:48|         0 Objects cancelled.
2008/01/04 20:13:48|         0 Duplicate URLs purged.
2008/01/04 20:13:48|         0 Swapfile clashes avoided.
2008/01/04 20:13:48|   Took 0.3 seconds (   0.0 objects/sec).
2008/01/04 20:13:48| Beginning Validation Procedure
2008/01/04 20:13:48|   Completed Validation Procedure
2008/01/04 20:13:48|   Validated 0 Entries
2008/01/04 20:13:48|   store_swap_size = 0k
2008/01/04 20:13:49| storeLateRelease: released 0 objects
2008/01/04 21:09:28| Preparing for shutdown after 0 requests
2008/01/04 21:09:28| Waiting 30 seconds for active connections to finish
2008/01/04 21:09:28| FD 13 Closing HTTP connection
2008/01/04 21:09:28| Shutting down...
2008/01/04 21:09:28| FD 14 Closing ICP connection
2008/01/04 21:09:28| Closing unlinkd pipe on FD 11
2008/01/04 21:09:28| storeDirWriteCleanLogs: Starting...
2008/01/04 21:09:28|   Finished.  Wrote 0 entries.
2008/01/04 21:09:28|   Took 0.0 seconds (   0.0 entries/sec).
CPU Usage: 0.016 seconds = 0.008 user + 0.008 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Memory usage for squid via mallinfo():
	total space in arena:    2104 KB
	Ordinary blocks:         2001 KB      8 blks
	Small blocks:               0 KB      0 blks
	Holding blocks:           240 KB      1 blks
	Free Small blocks:          0 KB
	Free Ordinary blocks:     102 KB
	Total in use:            2241 KB 96%
	Total free:               102 KB 4%
2008/01/04 21:09:28| Squid Cache (Version 2.6.STABLE14): Exiting normally.
```

My Laptop cannot access the Internet, it just says "Server not found"

On the Ubuntu box (Base), it *will* connect but occasionally it too says "Server not found", however this is usually resolved on clicking the "Try Again" button.

Can anyone advise me?

---

### Post by evymetal on 2008-01-05
> 
192.168.60:80

Is that the address you really mean? it's on a different subnet to the rest of your network so you can't talk to it.

Where is squid running? 

what machines are accessing squid? are the other boxes set up to use a proxy or are you trying to get the router to use squid?

your conf file looks quite confused, but I haven't set up squid for nearly 5 years.

---

### Post by koenn on 2008-01-05
where do you see it's on a different subnet ? 

It ***is ** * a bad address, because it's incomplete (4th octet missing), and squid complains about it : 

> commBind: Cannot bind socket FD 14 to 192.168.0.60:80: (99) Cannot assign requested address

I don't know if this is the cause of the trouble, but it's worth fixing.

---

### Post by cov on 2008-01-06
Yes, I'm afraid that it is a bit confused.

Part of the problem is that I have been referring to multiple howtos in an effort to get it to work.

I have fixed the typo and restarted squid but am still unable to get it to work.

Squid is running on Ubuntu server 'Base' with IP 192,168.60.254

The line has been changed to:

```
http_port 192.168.60.254:80 vhost vport=8080
```

The machines that are to access squid are on 192.168.60.0 and I'm trying to use it as a transparent proxy.. Apart from anything else, a significant number of machines are laptops and will need to connected to other networks.

Thanks very much for the responses; I was starting to think that I wouldn't get any...

PS. I have turned off the firewall

---

### Post by cov on 2008-01-06
My cache.log now has the following error:

```
commBind: Cannot bind socket FD 14 to 192.168.60.254:80: (98) Address already in use
```

I have commented out the line, but my Laptop on the network (IP 192.168.60.199) still cannot access the 'net.

---

### Post by koenn on 2008-01-06
> My Laptop cannot access the Internet, it just says "Server not found"
you did confiigure that laptop to use a **proxy,** didn't you ?

If so, can your laptop ping 192.168.60.254 ? Can it ping Base ?
can the laptop connect if you do
```
telnet Base 3128 
```
if it does, type anything (eg 'quit') and see if squid returns something

---

### Post by koenn on 2008-01-06
> My Laptop cannot access the Internet, it just says "Server not found"
you did confiigure that laptop to use a **proxy,** didn't you ?

And is squid actually running ? Your log ends with "squid exiting". 
what do you get if you '/etc/init.d/squid restart' it ?

---

### Post by cov on 2008-01-06
> **koenn said:**
> you did confiigure that laptop to use a **proxy,** didn't you ?

If so, can your laptop ping 192.168.60.254 ? Can it ping Base ?
can the laptop connect if you do
```
telnet Base 3128 
```
if it does, type anything (eg 'quit') and see if squid returns something

Koenn,

Thank you for your assistance.

I have not configured the Laptop to use a proxy as I want it to be transparent. ie. the Laptops have to connect to other networks and I don't want to have network-specific configurations.

I can ping Base which gives me a 'Reply from 192.168.60.254' as expected.

I cannot, however telnet to port 3128 as the Connect fails.

Using PuTTy on port 3128 also fails.

---

### Post by koenn on 2008-01-06
Ah, ok, I missed the transparant thing. 

Your squid log says (last line) : 2008/01/04 21:09:28| Squid Cache (Version 2.6.STABLE14): Exiting normally.
Did you stop it ? 
It has to be running if you want it to work  :)
What do you get if you start squid (/etc/init.d/squid restart) ? Does it start normally ?

---

### Post by cov on 2008-01-06
Koenn,

I have reinstalled squid (apt-get --reinstall install squid) and recieved an error message about file permissions in /var/log/squid which dpkg offered to correct.

On correcting these I can now telnet Base 3128. (blank screen)

However, 'Server not found' error message remains in Firefox 

'ping [www.google.com](www.google.com)' returns 'could not find host'

I have simplified my squid.conf to:```
visible_hostname Base
acl IQNetwork src 192.168.60.0/24
acl all src 0.0.0.0/0.0.0.0
http_access allow IQNetwork

http_port 3128 transparent

```

Still no joy....

---

### Post by cov on 2008-01-06
> **koenn said:**
> Ah, ok, I missed the transparant thing. 

Your squid log says (last line) : 2008/01/04 21:09:28| Squid Cache (Version 2.6.STABLE14): Exiting normally.
Did you stop it ? 
It has to be running if you want it to work  :)
What do you get if you start squid (/etc/init.d/squid restart) ? Does it start normally ?

Yes.

I keep restarting it when I change the squid.conf

---

### Post by koenn on 2008-01-06
> **cov said:**
> Koenn,
On correcting these I can now telnet Base 3128. (blank screen)

However, 'Server not found' error message remains in Firefox 

'ping [www.google.com](www.google.com)' returns 'could not find host'
[/CODE]


OK, let's verify that squid is working correctly . If you telnet it, you can make it return a html page with an error msg by sending a command it doesn't understand :
```

ix:~$ telnet squidserver 3128
Trying 192.168.2.1...
Connected to squi... 
Escape character is '^]'.

quit
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<HTML><HEAD><META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=iso-8859-1">
.... 

```

If that works, you should also be able to let your laptop use it if you tell it to use a proxy (forget the transparent for a moment). 

if all that works, the problem is probably in the way you set up the transparency. For transparent proxy to work, you need to redirect traffic towards any server : port80 to Base : port3128. Did you do that ?

---

### Post by cov on 2008-01-06
Yes, okay, the proxy server is working alright.

Where do I configure the redirection? Through NAT?

---

### Post by koenn on 2008-01-06
> **cov said:**
> 
Where do I configure the redirection? Through NAT?

Sort of. 
You can do it with iptables, but I don't remember the exact wording. It's something with 
PREROUTING  destination port 80 -j REDIRECT to 3128

---

### Post by cov on 2008-01-06
Uh.

I switched off iptables when I took down the firewall...

---

### Post by koenn on 2008-01-06
I suggest you set up iptables with all ACCEPT policies and no filtering, so you can get the REDIRECT working without interference from the firewall.
If redirect is working, you can start adding rules to filter the traffic (and check that your firewall rules don't block your web traffic  :) )

---

### Post by cov on 2008-01-06
Thanks Koenn.

I'm really battling to set up iptables.

I have found a number of recipes including [http://www.howforge.com/transparent-proxy-using-squid-and-iptables-in-ubuntu-dapper]("http://www.howforge.com/transparent-proxy-using-squid-and-iptables-in-ubuntu-dapper") but iptables -L just returns empty fields.

---

### Post by cov on 2008-01-06
This has got me tearing my hair out.

It's all supposed to be ready for tomorrow morning and there's no way.

Using this script:```
#!/bin/sh
# ------------------------------------------------------------------------------------
# See URL: http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html
# (c) 2006, nixCraft under GNU/GPL v2.0+
# -------------------------------------------------------------------------------------
# squid server IP
SQUID_SERVER="192.168.60.254"
# Interface connected to Internet
INTERNET="eth0"
# Interface connected to LAN
LAN_IN="eth1"
# Squid port
SQUID_PORT="3128"

# DO NOT MODIFY BELOW
# Clean old firewall
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
# Load IPTABLES modules for NAT and IP conntrack support
modprobe ip_conntrack
modprobe ip_conntrack_ftp
# For win xp ftp client
#modprobe ip_nat_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward
# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
# Unlimited access to loop back
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
# Allow UDP, DNS and Passive FTP
iptables -A INPUT -i $INTERNET -m state --state ESTABLISHED,RELATED -j ACCEPT
# set this system as a router for Rest of LAN
iptables --table nat --append POSTROUTING --out-interface $INTERNET -j MASQUERADE
iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT
# unlimited access to LAN
iptables -A INPUT -i $LAN_IN -j ACCEPT
iptables -A OUTPUT -o $LAN_IN -j ACCEPT
# DNAT port 80 request comming from LAN systems to squid 3128 ($SQUID_PORT) aka transparent proxy
iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
# if it is same system
iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT
# DROP everything and Log it
iptables -A INPUT -j LOG
iptables -A INPUT -j DROP
```

I have managed to get iptables to look linke this (iptables -L)```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere       
```

However, the Poxy Proxy still doesn't work....

This is the file generated by 'sh -c "iptables-save > /etc/iptables.rules"'
```
# Generated by iptables-save v1.3.6 on Sun Jan  6 15:43:02 2008
*filter
:INPUT DROP [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [170:37342]
-A INPUT -i lo -j ACCEPT 
-A INPUT -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -i eth1 -j ACCEPT 
-A INPUT -j LOG 
-A INPUT -j DROP 
-A FORWARD -i eth1 -j ACCEPT 
-A OUTPUT -o lo -j ACCEPT 
-A OUTPUT -o eth1 -j ACCEPT 
COMMIT
# Completed on Sun Jan  6 15:43:02 2008
# Generated by iptables-save v1.3.6 on Sun Jan  6 15:43:02 2008
*mangle
:PREROUTING ACCEPT [7369:4636096]
:INPUT ACCEPT [7357:4634944]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [6640:1456128]
:POSTROUTING ACCEPT [6784:1479798]
COMMIT
# Completed on Sun Jan  6 15:43:02 2008
# Generated by iptables-save v1.3.6 on Sun Jan  6 15:43:02 2008
*nat
:PREROUTING ACCEPT [27:3659]
:POSTROUTING ACCEPT [57:7185]
:OUTPUT ACCEPT [308:24727]
-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.60.254:3128 
-A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128 
-A POSTROUTING -o eth0 -j MASQUERADE 
COMMIT
# Completed on Sun Jan  6 15:43:02 2008
```

Can anyone see what I'm doing wrong?

---

### Post by koenn on 2008-01-06
> This has got me tearing my hair out. and that didn't help either ?  :)

> It's all supposed to be ready for tomorrow morning and there's no way.ah, deadlines ...  is this work-related ? 

I think that script assumes that iptables and squid are not on the same machine. In your case, squid and iptables are on the same host, right ? 

try this:
comment out these lines in the script```

## DNAT port 80 request comming from LAN systems to squid 3128 ($SQUID_PORT) aka transparent proxy
#iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j DNAT --to $SQUID_SERVER:$SQUID_PORT
##if it is same system
# iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port $SQUID_PORT

```
add this in stead : 
```

iptables -t nat -A PREROUTING -i $LAN_IN -p tcp --dport 80 -j REDIRECT --to-port  $SQUID_PORT

```
run the script again.
check if your proxy works
also, if i'm not mistaking, browsing to [http://Base](http://Base) (from your laptop) should then get you a reply from squid (probably "page not found or internal server error)

---

### Post by cov on 2008-01-06
Yes, before I went away for the holidays I said "Please pay me for the work and I'll have it ready for when work starts again".

About [Http://Base](Http://Base)....

I get an error message (from squid) which says "Unable to determine IP address host name for base. The dns server returned: Name Error: the domain name does not exist".

Also /var/log/squid/cache.log has these entries:```


2008/01/06 16:37:16| WARNING: Forwarding loop detected for:
Client: 192.168.60.254 http_port: 192.168.60.254:3128
GET http://192.168.60.254:3128/ HTTP/1.0

Host: 192.168.60.254:3128

User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-GB; rv:1.8.1.11) Gecko/20071127 Firefox/2.0.0.11

Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

Accept-Language: en-gb,en;q=0.5

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Via: 1.1 Base:3128 (squid/2.6.STABLE14), 1.0 Base:3128 (squid/2.6.STABLE14)

X-Forwarded-For: 192.168.60.199, 192.168.60.254

Cache-Control: max-age=259200

Connection: keep-alive
```

Does this give any insight?

I will try your suggestion with the script and report back...

---

### Post by koenn on 2008-01-06
> **cov said:**
> Does this give any insight?

dunno ... looks as if the redirection from port 80->3128 actually works ...

---

### Post by cov on 2008-01-06
Does it need DNS reconcilliation?

---

### Post by koenn on 2008-01-06
it does need dns - squid, that is : squid needs to resolve to domain part of the url's to IP addresses so it needs access to a dns server
if you can do a 'dig [www.google.com](www.google.com)' from the server, and get a reply, that's sufficient - all it needs is dns for web servers on the internet

(you may need to install dnsutils to get dig)

---

### Post by cov on 2008-01-06
Yes, 'dig [www.google.com](www.google.com)' works.

---

### Post by cov on 2008-01-14
Thanks to all that tried to help me here.

I have managed to get Squid working quite well, the problem was that I did not have a DNS server configured.

I will try to recount the steps that I took in resolving this issue, but it's no small job. Suffice to say that I tried an inordinate number of permutations of configuration files that I found by googling  until I found a combination that works. (After a fashion). Once I have managed to nail down this squid server (I'm over two weeks late with it), I shall try to assemble a simple howto.

---

