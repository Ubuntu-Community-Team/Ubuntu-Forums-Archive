---
title: "PTR Record working incorrectly."
date: 2012-04-24
forum: Server Platforms
---

### Post by orzgroup on 2012-04-24
First let me start by saying I'm 99% sure I've set everything up correctly.

I have a zone for "184.107.208.66" setup with the name
"208.107.184.in-addr.arpa", within that zone I have a ptr record for "66" pointing to "jewel1.trustelegance.com.", it is my understanding that by having the ptr record set as "66" without the terminating dot it will automatically append ".208.107.184.in-addr.arpa", this is confirmed later.

When I run nslookup on the ip address
```

whitespace@orzgroup ~ $ nslookup 184.107.208.66

```

I get
```

Server:		209.18.47.61
Address:	209.18.47.61#53

** server can't find 66.208.107.184.in-addr.arpa.: NXDOMAIN

```

This indicates the configuration is bad, however when I run
```

whitespace@orzgroup ~ $ nslookup 184.107.208.66 ns1.trustelegance.com

```

I get
```

Server:		184.107.208.67
Address:	184.107.208.67#53

66.208.107.184.in-addr.arpa	name = jewel1.trustelegance.com.

```
Which indicates the configuration is good, but when I don't specifically set it as ns1 (which resolves to 184.107.208.67) it appears to go through 209.18.47.61, which is not an ip address on the server.

I'm fairly confused as to why nslookup shows this seemingly random address when I don't specify a second parameter.

Please advise, thanks.

---

### Post by hawkmage on 2012-04-24
nslookup is getting this address from your /etc/resolv.conf.  There should be one or more entry in there for "nameserver" .  nslookup will use them in order.  

If you are using DHCP to get the IP address for this system you may very well be getting your name servers from the DHCP server as well.

---

### Post by orzgroup on 2012-04-24
Exactly just! Thank you, I should have speculated that myself.

/etc/resolv.conf
```

search privatedns.com
nameserver 70.38.0.3
nameserver 70.38.0.4

```

Would t his mean that as I'm obtaining via privatedns it would be up to them to set the ptr record, or am I mistaken?

---

### Post by Jonathan L on 2012-04-25
Hi Orzgroup

Your name servers ns1 and ns2 appear to be set up correctly apart from a missing PTR record for 67, although it's considered best practice not to have two public name servers for the same domain on the same network, nor to run other things on nameservers.  Your domain trustelegance.com seems completely correct, including the glue records for the name servers in the parent domain.

However, your reverse domain isn't delegated: for the chain of name servers to find yours, you need to have an entry in the parent domain, and this can be difficult to achieve.

Can I ask if you have the whole block 184.107.208/24?  If you did, then you would have the entries like you have them, but you ask for these to be put into the _servers of the parent domain_ 107.184.in-addr.arpa, which are run by iweb. _ Their_ zone file would therefore look like this:
```
$ORIGIN 107.184.in-addr.arpa.
@ SOA ...
@ NS ns1.iweb-hosting.com.
@ NS ns1.iweb-hosting.com.
...
208 NS ns1.trustelegance.com.
208 NS ns2.trustelegance.com.
...
```These delegations for reverses are rather problematic, and most ISPs are extremely reluctant to do them even for a whole /24.  I know of no ISP which will delegate below a /24, as it's rather trickier (see [http://tools.ietf.org/html/rfc2317](http://tools.ietf.org/html/rfc2317)) -- I know of nobody who has implemented this at scale.  Some ISPs will put PTR records in their zones for you, like this:

```
$ORIGIN 208.107.184.in-addr.arpa.
@ SOA ...
@ NS ns1.iweb-hosting.com.
@ NS ns2.iweb-hosting.com.
...
66 PTR jewel1.trustelegance.com.
...

```If you're not clear about how the delegation works, try this in order.  You'll see that each one chooses a server from the previous answer, just like the normal look up will do automatically:

Commands are laid out with extra spaces to show the tree:

```

dig                                                . ns
dig @a.root-servers.net                         com. ns
dig @a.gtld-servers.net           trustelegance.com. ns
dig @ns1.trustelegance.com jewel1.trustelegance.com. a
```Now compare that with what happens for the reverse domain:

```
dig                                                       . ns
dig @a.root-servers.net                               arpa. ns
dig @a.root-servers.net                       in-addr.arpa. ns
dig @a.in-addr-servers.arpa               184.in-addr.arpa. ns
dig @z.arin.net                       107.184.in-addr.arpa. ns
[COLOR=Red]dig @ns1.iweb-hosting.com         208.107.184.in-addr.arpa. ns[/COLOR]
dig @ns1.iweb-hosting.com      66.208.107.184.in-addr.arpa. ptr
(error NXDOMAIN)

```If you have the whole /24. you ask iweb to delegate to you, as I described above, and then the red query would return ns1.trustelegance.com, not ns1.iweb-hosting.com, and the last query would look like this:
```

dig @ns1.trustelegance.com      66.208.107.184.in-addr.arpa. ptr
(answer: jewel1.trustelegance.com)

```If you have only a small number of hosts, you could try asking them to put your PTR records in their server, but honestly I'll be very surprised if they're willing and able.

Can I ask what you want it for?  The only thing which really uses reverses much is email, where many servers refuse incoming connections unless the reverse lookup matches the forward.  If you're setting up an email server, it's usually simplest to forward your mail out of a service for this.

Having run DNS in various incarnations, I can't recommend it unless you just want to find out how it works.  If you want it for a production system, I'd recommend you use the services of your domain company or your web hosting company.  There's a lot of work, many things which can go wrong, and for very little benefit.  Of course if you're just learnnig for its own sake, more power to you!

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by orzgroup on 2012-04-25
Thanks very much for your reply! It was very helpful in understanding the process. We do not have the full /24 in anticipation that the answer was as you've stated I had already contacted the datacenter, no reply yet..

As for what we need it for, I'm not too sure, my client asked me to ensure it was configured properly, I've never done anything with ptr records before so I wasn't sure if I was possibly missing a step or what!

Again thank you for the guidance, this can be marked as solved!

---

### Post by webservervideos on 2012-04-25
does you zone section in named.conf point to 66.208.107.184.in-addr.arpa or 208.107.184.in-addr.arpa?  are there any errors in your log files for named after reload?  did you advance the serial numbers in all files changes (like the arpa one) and then reload?  did you check with an online resource like nslookup and mx check to look for issues you are missing?

---

### Post by SeijiSensei on 2012-04-25
```

seiji@host:~$ host -t ns trustelegance.com
trustelegance.com name server ns2.trustelegance.com.
trustelegance.com name server ns1.trustelegance.com.

seiji@host:~$ host ns1.trustelegance.com
ns1.trustelegance.com has address 184.107.208.67
ns1.trustelegance.com mail is handled by 0 ns1.trustelegance.com.

seiji@host:~$ host -t ns 208.107.184.in-addr.arpa
208.107.184.in-addr.arpa name server ns2.iweb-hosting.com.
208.107.184.in-addr.arpa name server ns1.iweb-hosting.com.

seiji@host:~$ host 184.107.208.66
Host 66.208.107.184.in-addr.arpa. not found: 3(NXDOMAIN)
seiji@host:~$ host 184.107.208.67
Host 67.208.107.184.in-addr.arpa. not found: 3(NXDOMAIN)


```

The only entity who can set up reverse resolution for 184.107.208.66 and .67 is iweb-hosting.com.  As Jonathan said, it's highly unlikely they'll delegate the PTR records for these hosts to you.  If your web site is on a machine that shared with other customers, then they almost certainly won't set up reverse-resolution for those addresses to point solely to you.  If those addresses are assigned uniquely to you, most ISPs will set up a reverse record.

The only time when I think having proper reverse resolution matters is if the machine is sending mail.  Most SMTP servers use reverse resolution to see if the alleged sending hostname matches the reverse lookup.  This is an anti-spam measure.  If the site is only being used to host web services, the lack of a reverse entry isn't that important.

---

### Post by Jonathan L on 2012-04-25
> my client asked me to ensure it was configured properlyHi again ...

If it's just setting up a web server, I'd definitely recommend using the domain name company's servers; most have really very good web control panels: I'm familiar with Go Daddy and Network Solutions, both of which (in the advanced panel) let you simply put records into your domain.

If it's more than that, I'd still recommend using serviced DNS.  Most domain companies have good services.  Ultra DNS and Amazon have interesting offerings.

If you have good, multiple, internet links, preferably with different companies in diffierent locations, then doing your own DNS starts making sense.

And just to clarify: there are two things people mean when they talk about DNS setup:
1.  Resolving Queries from the public about your domains (this is what we've been talking about)
2.  Resolving Queries from your servers about anything

The second can be complex too, if you have a network with private (eg 192.168.0.1) addresses with network address translation (NAT) at the border.  It is quite common for servers to run a DNS server simply to do their own resolution (ie, their resolve.conf says nameserver 127.0.0.1) as this can speed up the resolution a bit, or provide autonomy from the web server company.

If you really, really, want to set up DNS servers, my recommendations would be:

1.  Get a domain like trustelegance-dns.com
2.  Put two name servers in different continents
3a  Put trustelegance-dns.com's NS and A records in the domain company's DNS.
3b. Or if you really have to:
```
$ORIGIN trustelegance-dns.com.
@ SOA ...
@ NS ns1.trustelegance-dns.com.
@ NS ns2.trustelegance-dns.com.
ns1 A 1.2.3.4
ns2 A 2.3.4.5
```I really recommend option 'a' because if you do 'b' then if for any reason you have to move trustelegance-dns.com's servers, you have to update the domain company's servers anyway, for the glue records; with 'a' you just have the one step.

4. All your other domains have their records on your two servers:
```
$ORIGIN clientdomain1.com.
@ SOA ...
@ NS ns1.trustelegance-dns.com.
@ NS ns2.trustelegance-dns.com.
www A ...

$ORIGIN clientdomain2.com.
@ SOA ...
@ NS ns1.trustelegance-dns.com.
@ NS ns2.trustelegance-dns.com.
www A ...
```5.  Obviously if you have any reverses, they would be like this:
```
$ORIGIN 3.2.1.in-addr.arpa.
@ SOA ...
@ NS ns1.trustelegance-dns.com.
@ NS ns2.trustelegance-dns.com.
1 PTR www.clientdomain1.com.
2 PTR www.clientdomain2.com.
```Basically this setup is designed so that only one domain (trustelegance-dns.com) has name servers inside its own domain. Took me years to work that out: please send One (1) Beer!

Hope that's helpful.  

Kind regards,
Jonathan.

---

