---
title: "Assistance with DNS and Webmin"
date: 2012-08-15
forum: Server Platforms
---

### Post by AnubisXVIII on 2012-08-15
Good Day,

I have searched, followed countless tutorials but right now I do not know if I am doing the right thing. I have  a VPS with the ip 78.xxx.xxx.xxx. The host name for the server is : server.mydomain.com . I have purchased mydomain.com from godaddy already. I can access the web server using the IP address alone so I know it is accessible from the net. My problem is that when I check with websites such as pingability, I get the following errors.
> 
**[SIZE=2]Zone Info: mydomain.com[/SIZE]**

  **[SIZE=2]Zone Info[/SIZE]**

[SIZE=2][COLOR=Black][Info Type   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/COLOR][/SIZE][SIZE=2][COLOR=Black][Message   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/COLOR][/SIZE] [SIZE=2]Warning[/SIZE][SIZE=2]mydomain.com does not have an IP Address (A) record.[/SIZE] [SIZE=2]Information[/SIZE][SIZE=2]8 seconds to complete zone checks.[/SIZE][SIZE=2]
[/SIZE]**[SIZE=2]Parent Name Servers[/SIZE]**

  [SIZE=2]This section lists the hierarchy of name servers that a DNS lookup needs to walk to find your zone's name servers.  For brevity only one name server is listed per zone.[/SIZE]
   	 	    [SIZE=2][Zone   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/SIZE][SIZE=2][Name Server   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/SIZE][SIZE=2][IP   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/SIZE][SIZE=2][Location   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/SIZE][SIZE=2][Response Time (ms)   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/SIZE] 	     	        [SIZE=2]com[/SIZE][SIZE=2]i.gtld-servers.net[/SIZE][SIZE=2]192.43.172.30[/SIZE][SIZE=2]United States[/SIZE][SIZE=2]0[/SIZE] 	     	        [SIZE=2].[/SIZE][SIZE=2]l.root-servers.net[/SIZE][SIZE=2]199.7.83.42[/SIZE][SIZE=2]United States[/SIZE][SIZE=2]0[/SIZE] 	     	 
  
   	**[SIZE=2]mydomain.com Name Servers[/SIZE]**

  	  	**[SIZE=2]Zone Configuration Info[/SIZE]**

[SIZE=2][Info Type   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/SIZE][SIZE=2][Message   ]("http://pingability.com/zoneinfo.jsp?domain=pharaohinc.com#")[/SIZE] [SIZE=2]Error[/SIZE][SIZE=2]None of this zone's name servers responded on the request for 'mydomain.com' records.  Giving up.[/SIZE] [SIZE=2]Heads-up[/SIZE][SIZE=2]None of the name servers had an SOA record, randomly selecting ns2.mydomain.com as the master name server.[/SIZE]

Below is the zone file created by placing all the instructed information from following tutorials in Webmin in order to create a zone. I had originally tried manually but got nowhere, so I assumed using Webmin would be easier but I am getting the same results.

```
$ttl 38400
mydomain.com.    IN    SOA    ns1.mydomain.com. hostmaster.gmail.com. (
            1344979879
            10800
            3600
            604800
            38400 )
mydomain.com.    IN    A    75.xxx.xxx.xxx
www.mydomain.com.    IN    A    75.xxx.xxx.xxx
ns1.mydomain.com.    IN    A    75.xxx.xxx.xxx
ns2.mydomain.com.    IN    A    69.xxx.xxx.5
mydomain.com.    IN    NS    ns1.mydomain.com.
mydomain.com.    IN    NS    ns2.mydomain.com.

```

I just want to know what it is that I am doing wrong exactly. I have waited almost 48 hours just in case it was still being propagated. The IP address 69.xxx.xxx.5 was listed in my resolv.conf file.

---

### Post by sanderj on 2012-08-15
If you post the real domain name, I could test it for you. Now I have to stay abstract:

Two things to test:

Test which nameservers your domain has (set by your domain registrar):

```
host -t ns yourdomain.com

```
Test what your own nameserver says:

```
host www.yourdomain.com yourownnameserver.yourdomain.com

```

Both should be correct, and the domain registrar should be pointing to yourownnameserver.

PS:

It really is easier to let your registrar do the DNS hosting 


HTH

---

### Post by AnubisXVIII on 2012-08-15
Yeah I know it would be a lot easier, but this is something that I would like to get working. Just to avoid costs of them hosting it in the future when I run more than one site. The name of the domain is pharaohinc.com

```
host -t ns pharaohinc.com

Gave me:

pharaohinc.com name server ns1.pharaohinc.com.
pharaohinc.com name server ns2.pharaohinc.com.

host www.pharaohinc.com ns1.pharaohinc.com

Using domain server:
NameL ns1.pharaohinc.com
Address: 75.xxx.xxx.xxx#53
Aliases:

www.pharaohinc.com has address 75.xxx.xxx.xxx
```

Those were the results given, which is indeed the name server

---

### Post by SeijiSensei on 2012-08-15
From out here on the Internet, all attempts to query your nameserver fail with "host not found."  It's likely that your nameserver doesn't have UDP port 53 exposed to the Internet.  If you restart your nameserver, do you see entries in /var/log/syslog that report the server has bound to all the IP addresses, including most importantly the public-facing ones?  You should see entries like this:

```

Aug 15 01:00:06 smtp named[14803]: listening on IPv4 interface lo, 127.0.0.1#53
Aug 15 01:00:06 smtp named[14803]: listening on IPv4 interface eth0, 75.xxx.xxx.xxx#53

```

Do you have a firewall in place?  Is it blocking port 53?

Don't test from the machine itself.  You need to test from a machine outside your network.

I agree with sanderj that you should let the domain registrar host your DNS.  Running a nameserver can be a complicated task.  On top of everything else, you should be running two nameservers for redundancy to conform to [Internet standards]("http://tools.ietf.org/html/rfc1912") (see section 2.8).  One nameserver is not enough.

---

### Post by AnubisXVIII on 2012-08-15
Thanks will double check to see if it is indeed broadcasting, if not I will just follow your suggestion and let GoDaddy deal with it. Thanks for the assistance

---

### Post by AnubisXVIII on 2012-08-15
Welll I looed throught the system logs and this is what I found....
```

Aug 15 16:00:42 server named[11435]: error (network unreachable) resolving '148.87.75.65.in-addr.arpa/PTR/IN': 2001:500:13::73#53
Aug 15 16:00:42 server named[11435]: error (network unreachable)  resolving '148.87.75.65.in-addr.arpa/PTR/IN': 2001:67c:e0::1#53
Aug 15 16:00:43 server named[11435]: error (network unreachable)  resolving './NS/IN': 2001:500:1::803f:235#53
Aug 15 16:00:43 server named[11435]: error (unexpected RCODE REFUSED) resolving '148.87.75.65.in-addr.arpa/PTR/IN': 208.246.140.130#53
Aug 15 16:00:43 server named[11435]: error (unexpected RCODE REFUSED)  resolving '148.87.75.65.in-addr.arpa/PTR/IN': 208.246.140.129#53
Aug 15 16:00:43 server named[11435]: error (unexpected RCODE REFUSED)  resolving '148.87.75.65.in-addr.arpa/PTR/IN': 208.246.140.130#53
```

Then it says further down

```
Aug 16 00:04:09 server named[323]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found
```

---

### Post by sanderj on 2012-08-15
I tested, and test #1 fails:

```
sander@R540:~$ host -t ns pharaohinc.com
;; connection timed out; no servers could be reached


sander@R540:~$ time host -t ns pharaohinc.com
;; connection timed out; no servers could be reached

real	0m10.011s
user	0m0.004s
sys	0m0.004s
sander@R540:~$

```

I would say that's a misconfiguration at your registrar.

EDIT:

Registrar seems to be GoDaddy. Have you changed anything in their webinterface?

whois points to

```
   Domain servers in listed order:
      NS1.PHARAOHINC.COM
      NS2.PHARAOHINC.COM
```

but they do not exist:

```
sander@R540:~$ host NS1.PHARAOHINC.COM
;; connection timed out; no servers could be reached
sander@R540:~$ host NS2.PHARAOHINC.COM
;; connection timed out; no servers could be reached
sander@R540:~$
```

So ... that's not good. I would expect that at the moment you register your domain, the NS1 and NS2 should be pointing to GoDaddy's system. Have you changed that?

---

### Post by AnubisXVIII on 2012-08-15
I changed my name servers with GoDaddy, I followed the directions for registering my nameservers with them. That was how I was able to put ns1.pharaohinc.com...that is attached to the IP address 75.xxx.xxx.xxx and ns2.pharaohinc.com. That should be attached to 69.xxx.xxx.xxx. But that is the only thing I have done so far with GoDaddy

---

### Post by sanderj on 2012-08-16
> **AnubisXVIII said:**
> I changed my name servers with GoDaddy, I followed the directions for registering my nameservers with them. That was how I was able to put ns1.pharaohinc.com...that is attached to the IP address 75.xxx.xxx.xxx and ns2.pharaohinc.com. That should be attached to 69.xxx.xxx.xxx. But that is the only thing I have done so far with GoDaddy

What if you fill out the IP address of your nameserver at GoDaddy?

BTW: you are not mentionning the IP address of your nameserver in this thread, are you? If you would, I could test it.

---

### Post by AnubisXVIII on 2012-08-16
IP Address for ns1.pharoahinc.com = 75.98.171.215
                       ns2.pharoahinc.com = 69.39.86.5

---

### Post by sanderj on 2012-08-16
> **AnubisXVIII said:**
> IP Address for ns1.pharoahinc.com = 75.98.171.215
                       ns2.pharoahinc.com = 69.39.86.5

Those nameservers are not reachable from Internet:

```
sander@toverdoos:~$ host www.google.com 75.98.171.215
;; connection timed out; no servers could be reached
sander@toverdoos:~$ host www.google.com 69.39.86.5
;; connection timed out; no servers could be reached
sander@toverdoos:~$
```

Things to check:
is a nameserver running at all on those system
is the nameservice reachable through firewalls etc

---

### Post by AnubisXVIII on 2012-08-16
Tested the ports and it seemed to be listening for any connection on port 53.....yet outside it is saying unreachable.....just gonna start the machine from the ground up and just let godaddy deal with the DNS

---

### Post by AnubisXVIII on 2012-08-16
Okay, just waiting on technical support to give me a new VPS to set up...but it's just bugging me. So I did this

```
sudo iptables --list
```

and got this as a result

```
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh
ACCEPT     tcp  --  localhost            localhost            tcp dpt:953
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             127.0.0.0/8          reject-with icmp-port-unreachable
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:webmin
ACCEPT     tcp  --  anywhere             anywhere             state NEW tcp dpt:7822
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
LOG        all  --  anywhere             anywhere             limit: avg 5/min burst 5 LOG level debug prefix "iptables denied: "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere    
```

So is the problem the firewall rules that have been installed on the server...

---

### Post by SeijiSensei on 2012-08-17
> **AnubisXVIII said:**
> So is the problem the firewall rules that have been installed on the server...

Yes, you don't permit port 53 traffic.  Add this rule:

```
iptables -A INPUT -p udp --dport 53 -j ACCEPT
```

You can also open TCP port 53, but that is typically used for transfers between the primary and secondary name servers.  If 69.39.86.5 is the secondary, add the rule:

```
iptables -A INPUT -p tcp -s 69.39.86.5 --dport 53 -j ACCEPT
```

or just permit all traffic from the secondary if it is under your control and trusted.

---

### Post by AnubisXVIII on 2012-08-17
Thanks, that did the trick. Thanks for all the help you guys

---

