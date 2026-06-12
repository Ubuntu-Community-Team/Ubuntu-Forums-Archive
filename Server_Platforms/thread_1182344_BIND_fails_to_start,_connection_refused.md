---
title: "BIND fails to start, connection refused"
date: 2009-06-08
forum: Server Platforms
---

### Post by jeremy1138 on 2009-06-08
I'm trying to get a DNS server up and running using BIND.  I initially installed the DNS server as part of the Ubuntu 9.04 server edition install routing (ie I checked the box next to DNS server during the initial os install).  Then I followed this how-to:

[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

to get it configured.  I went through all the steps and I think I got it configured correctly but it doesn't work.  Here is what I get the first time I tried to restart BIND:

```

jeremy@server1:~$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                 [ OK ] 
 * Starting domain name service... bind9                                 [fail] 

```

I tried to restart again thinking it was a fluke and I got this:

```

jeremy@server1:~$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                        
rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [ OK ]
 * Starting domain name service... bind9                                 [fail] 

```

and this is the same thing I get every time now.

I tried forwarding port 953 in my router config and I still get the same error.  I tried putting the server in my router's DMZ and I get the same error still.  My router is a Linksys WRT54G by the way.

Ok so I think It might be helpful to show the files that I edited as part of the how-to I mentioned earlier, so I'll do that now:

first I forwarded port 53 to my servers network address of 192.168.1.105.  Then I ran:

```

sudo gedit /etc/bind/named.conf.local

```

and edited it to look like this:

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name

zone irishviking.net {
type master;
file /etc/bind/zones/irishviking.net.db;
};

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0

zone 1.168.192.in-addr.arpa {
type master;
file /etc/bind/zones/rev.1.168.192.in-addr.arpa;
};

```

Then I ran

```

sudo gedit /etc/bind/named.conf.options

```

and changed it to look like this:

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
	 	24.92.226.40;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```

Next I ran

```

sudo mkdir /etc/bind/zones

sudo gedit /etc/bind/zones/irishviking.net.db

```

irishviking.net is my domain name by the way.  I copied the following into irishviking.net.db and edited what I thought I needed to:

```

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
irishviking.net. IN SOA ns1.irishviking.net. admin.irishviking.net. (
// Do not modify the following lines!
2007031001
28800
3600
604800
38400
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mail = mail server name
// example.com = domain name
irishviking.net. IN NS ns1.irishviking.net.
irishviking.net. IN MX 10 mail.irishviking.net.

// Replace the IP address with the right IP addresses.
www IN A 192.168.1.105
mta IN A 192.168.1.105
ns1 IN A 192.168.1.105

```

This file made me think: I want to have a web server, mail server, dns server and ftp server running on the same machine.  I hope that's not a problem...  This is going to be a very low traffic site for just my family.  Anyway, onward!

I then ran

```

sudo gedit /etc/bind/zones/rev.1.168.192.in-addr.arpa

```

and edited it to look like this:

```

//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, its 1, as my IP address is 192.168.0.1.
@ IN SOA ns1.irishviking.net. admin.irishviking.net. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS ns1.irishviking.net.
105 IN PTR irishviking.net

```

Then I ran

```

// replace example.com with your domain name, and 192.168.0.1 with the address of your new DNS server.

search irishviking.net
nameserver 192.168.1.105

```

That catches us up to running

```

sudo /etc/init.d/bind9 restart

```

which, of course, led to the error mentioned at the top.  I am certainly not an expert on this stuff but I am trying to learn and I'm sorry that this is so long but I wanted to be thorough.  I'd appreciate any help you can give.

Thanks!

Oh and by the way, I want to give some details on my setup.  I registered a domain with godaddy: irishviking.net, and it points to my ip address without a problem from both inside and outside my home network.  I have an apache server and an ftp server running on there without a problem.  The ip address assigned to the server is 192.168.1.105.  One of the things that confused me about the how-to that I followed was when it asked for my "network address".  The guy writing the tutorial said that his was 192.168.0...  I'm not sure how to get that but I know that the address of my router is 192.168.1.1 so I just assumed that my "network address" is 192.168.1 so that's what I used in the config files.  The computer acting as the server is an old Dell with a Pentium 4 processor (not the computer mentioned in my sig).

One more thing that I find interesting is that I can't get to any websites from firefox on the server now.  If I try to go to google.com it says address not found.  I can still get to my routers configuration page by typing 192.168.1.1 into the address bar however.  Internet on my other computers that are connected to the same network still works fine.

Ok that's it.  Thanks in advance for any help you can give and I'll be happy to provide any additional info if needed.

---

### Post by Zeosa on 2009-06-08
Look at /var/log/syslog when starting bind up and see if it spits any specific errors out that lead you to the problem  (tail -f /var/log/syslog).

---

### Post by jeremy1138 on 2009-06-08
> **Zeosa said:**
> Look at /var/log/syslog when starting bind up and see if it spits any specific errors out that lead you to the problem  (tail -f /var/log/syslog).

Man you are a GENIUS!  That is the most useful piece of advice I have ever gotten on this forum...  ever!  Apparently bind was looking for quotes around some strings in my /etc/bind/named.conf.local file.  I just added in the quotes to make it look like this:

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name

zone irishviking.net {
type master;
file "/etc/bind/zones/irishviking.net.db";
};

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0

zone 1.168.192.in-addr.arpa {
type master;
file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};

```

I missed these quotes in the how-to that I followed.  Copy and paste goofs up with some of the special characters when I copy from my local computer to another computer via VNC.  I need to watch it more closely I guess.

Also, It appears that I do have to have port 953 forwarded to the server for some reason...  I'm not really sure why that is because it's only supposed to be using 53 from what I understand.  Anyone have any idea why it's listening to 953 instead?  

Also I tried to do what the how-to says to test my server and this is what I get:

```

jeremy@server1:~$ dig irishviking.net

; <<>> DiG 9.5.1-P2 <<>> irishviking.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 45508
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;irishviking.net.		IN	A

;; Query time: 11 msec
;; SERVER: 192.168.1.105#53(192.168.1.105)
;; WHEN: Mon Jun  8 23:18:40 2009
;; MSG SIZE  rcvd: 33

```

I notice that it says status: SERVFAIL.  Does that mean it isn't working correctly?  If so, any ideas what I might do to fix it?  By the way I still had my terminal running

```

tail -f /var/log/syslog

```

while I tested my DNS and it didn't spit out anything.

Thanks again Zeosa.  Your help is greatly appreciated!

---

