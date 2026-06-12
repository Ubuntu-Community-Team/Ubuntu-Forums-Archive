---
title: "(BIND) DNS Server not responding!"
date: 2009-03-07
forum: Server Platforms
---

### Post by fryser_d on 2009-03-07
TAG: can't ping, cannot ping, domain, bind, DNS

Ok so I've setup a DNS server with (Bind) through (Webmin).

And everything is working fine[I can ping myDomain.com] FROM my server[sv].

> sv (ping myDomain.com) => return good address; :popcorn:

client[On the network](ping myDomain.com) => return bad address(The address of the real myDomain.com[on the internet] :(
But I can ping the ip of the server.

Now is my client isn't suppose to check on the network first, then if the DNS don't exist: search on the internet!?

Or simply there's a concept about DNS that I just missed :o

Goal: 1 Linux server + Many Windows clients connected trough the Domain.

----------------------------------------------------------------------
[SOLVED]*edit*
Thx to: netztier

_**Procedure:**_
Backup file;
edit "/etc/bind/named.conf.options";
```

sudo cp /etc/bind/named.conf.options /etc/bind/named.conf.options_BackUp
sudo nano /etc/bind/named.conf.options

```

Add option to file:
```

options {
...
	allow-recursion { 
	    localnets; 
	    192.168.1.0/24;
	};
...
}

```

_**Setup Clients:**_
*Windows:*
```

Control Panel > Network Connections > 
Right click"Local network connection" > Properties >
 Internet protocol(TCP /IP) [Properties]>
"Use the following DNS server addresses:"> Input DNS Server.

```

*Ubuntu/Linux:*
```
sudo cp /etc/resolv.conf /etc/resolv.conf_Backup
sudo nano /etc/resolv.conf

Add to first line:
"nameserver 192.168.x.x"
```

Thx again netztier ;)

---

### Post by netztier on 2009-03-07
> **fryser_d said:**
> TAG: can't ping, cannot ping, domain, bind, DNS

Ok so I've setup a DNS server with (Bind) through (Webmin).

And everything is working fine[I can ping myDomain.com] FROM my server[sv].


Check BIND's configuration files for the following section. Depending on how BIND was configured in your case, the **options {...}** section could be found in /etc/bind/named.conf, /etc/bind/named.conf.options or /etc/bind/named.conf.local


```
options {

...
	allow-recursion { 
	    localnets; 
**	    192.168.1.0/24;**
	};

...

}

```

Make sure that the IP subnet(s) that your client systems are in are listed in **allow-recursion {...}**, replacing 192.168.1.0/24 by whatever is correct for your network. Only the networks listed in there are allowed to issue queries to this DNS. "localnets" is a keyword that covers the subnet(s) the DNS machine has it's interface(s) in.

> 
Now is my client isn't suppose to check on the network first, then if the DNS don't exist: search on the internet!?


That's handled via DHCP or manual configuration on the client. List your local DNS server first, and in second place an internet-reachable one.

> 
Goal: 1 Linux server + Many Windows clients connected trough the Domain.

Nah. Don't confuse network and routing with "Domain". You don't connect "through" a domain and not "through" a DNS server. 

Connections from your clients won't go "through" a server just because it's a DNS server now. A DNS - local or remote - will only deliver name-to-IP-address information, so that the client will know to which IP address it should send a TCP SYN packet if the user had typed [http://www.somedomain.com/](http://www.somedomain.com/) in his browser. 

It might be "through" that server, if the DNS machine is also doing routing and/or ICS (Internet Connection Sharing) - but then it's because it is configured for routing and ICS, not because it happens to be a DNS as well.


regards

Marc

---

