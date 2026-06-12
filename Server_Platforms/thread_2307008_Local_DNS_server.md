---
title: "Local DNS server"
date: 2015-12-21
forum: Server Platforms
---

### Post by gardenair on 2015-12-21
hi,
    we are using a external DNS  server which is place some where and in  the clients computers we add that ip address of that DNS server.I want to create my own DNS server  that instead to use that server our local server resolve it. Suppose if some one want to resolve [www.google.com](www.google.com) then instead to use my ISP snd server  IP address I may add my own DNS Server IP address .For that purpose what kind of DNS server should I create ?

---

### Post by darkod on 2015-12-21
You need to install bind and configure few basic things to get a dns server up and running. It's quite easy. For any zone (request) that is not configured on that server, there is a forwarder option that includes the IP of another server where the request should be forwarded. That way your DNS server will reply to the requests that it can, and forward all other request to your ISP DNS, or the google dns, etc...

---

### Post by gardenair on 2015-12-21
well i have just google and i see that to install bind in the system. There is already a file inside /etc/named.conf so the bind is different and /etc/named.conf is different  ? or they are interlinked with each other ? 

Yes you are correct ,I want that my local DNS server may forward the request coming from the client to the isp DNS server.

---

### Post by darkod on 2015-12-21
What do you mean "you have google"? Are you trying to create a zone for google on local dns? I don't think you can do that, since the google domain register specifies which DNS servers are the nameservers to use for the domain.

Otherwise people would be able to easily falsify web sites and point you to a wrong one.

PS. Here you have the basic info for bind coming with 14.04 LTS: [https://help.ubuntu.com/lts/serverguide/dns.html](https://help.ubuntu.com/lts/serverguide/dns.html)

---

### Post by SeijiSensei on 2015-12-21
You want what's called a "caching nameserver."  There are instructions for this at [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) and [https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04).  A caching nameserver talks directly to the root name servers and stores any records it requests for future use.  With this configuration you don't need to use forwarding. You do need to make sure your firewall allows the server to send requests to remote UDP port 53.  Usually that happens automatically with most routers unless you have more stringent custom firewall rules.  Port 53 on the server itself must also be open to the local clients though not to the Internet.

---

### Post by MAFoElffen on 2015-12-22
I agree with the other 2 ( SeijiSensei and darkod)... to what they are saying and what they have said.

Lets get an understandng of what has been said... I computer needs a nameserver to resolve a name to an IP address. Normally, a computer would get these through DCHP from their ISP. If you need more than that, then understanding some basic on networking will help out immensely. The only reasom you need name resolution locally, is if you are accessing resources on your own network by name.

If you have a couple pc's, where you could benefit from name resolution, then you might benefit from copying over a common hosts file, where you can resolve your local name/ip's for your local resources on a small network. I admit, if it's only a few, I can rember their Ip's. Once your local network grows to over 10, then think about a local DNS. 

I use Bind9 on 2 boxes as my primary and secondardy local DNS. I have those same 2 as my DHCP primary and secondary. I use OpenDNS as my upstream DNS.

---

### Post by gardenair on 2015-12-22
well i have created my own DNS server and it is connected with the ISP server.I only add one Host which is 10.1.83.250 (a private network).The DNS server fetch web page for my windows browser in  windows machine but when I use nslookup command it show me.
plz see the attachment.

---

### Post by CharlesA on 2015-12-22
I was able to replicate the "cannot find server name" message - that is likely because you do not have any local DNS set up for that entry. It is trying to resolve the hostname so it can put that for the Server rather than Unknown.

As far as the default servers cannot be found message, read this:
[http://docstore.mik.ua/orelly/networking_2ndEd/dns/ch12_07.htm](http://docstore.mik.ua/orelly/networking_2ndEd/dns/ch12_07.htm)
[https://technet.microsoft.com/en-us/library/cc961417.aspx](https://technet.microsoft.com/en-us/library/cc961417.aspx)

---

### Post by SeijiSensei on 2015-12-22
My office DNS server maintains private records for some of my domains that differ from those published on the Internet.  It also uses a forwarder to direct requests for a client's domain to its internal DNS servers over a virtual private network.  For all other requests it contacts the root name servers directly and caches the replies.

---

### Post by MAFoElffen on 2015-12-23
> **SeijiSensei said:**
> My office DNS server maintains private records for some of my domains that differ from those published on the Internet.  It also uses a forwarder to direct requests for a client's domain to its internal DNS servers over a virtual private network.  For all other requests it contacts the root name servers directly and caches the replies.
I agree with you... The purpose of a Local DNS is so the local network can find local resources by name, before going to 0.0.0.0, which would route outside the Local Network, trying to resolve the name outside that local network. Or as you mentioned, shared secrets between domains, possibly on domain controllers in the same Forest.

The OP has now configured BIND9 and needs help with it's configuration, so let's back up a few steps. Lets go back to an explanation of how it works and what he needs to do.

BIND9 uses a database (region files) with records to resolve a named resource to an IP address. You end up with forward lookup and matching reverse lookup files. A forward lookup resolves a name to an IP. A reverse lookup resolves an IP to a name. The resulting DNS db is hierarchical, in that it takes layers of DNS servers to search through those layers to resolve a named resource with an IP. So if a local db does not have a match, it goes to the next higher DNS layer to search for a match ... and so on and so forth. This needs two things to work. (1) A valid well-formed record to find a local resource. (2) A well-formed record pointer to the forwarded DNS'es IP, in the next layer up.

So what I see in your output is probably a problem in the records of both... When I enter a record in any of my BIND9 db files, before restarting BIND9 to pickup those changes, I test them with some of the included utilities, to insure that they are well-formed (no syntax errors in the records), and that they can resolved what I expect them to (can match a name to an IP and are of the type or regions that I expect them to).

How I propose going about correcting this, it to list the file names of your BIND9 db files... then post the db files that you modified. This is where I suspect you have your problem, in what you are trying to do. (the config of your regions and your named/IP records) Read to the end of this post before posting anything.

The thing is, this is the same (or very similar) with any DNS configuration, no matter what platform your DNS resides on. So when you learn to do this in a Linux environment, you can figure out how to do this in/on other environments. Meaning that DNS records in Windows Server's DNS Service are in the same format... Learning how to do this in BIND9, later carried me through understanding how to do that in my Windows Server and CISCO certification courses.

I know that when I first used BIND9, the doc's say configure everything and to use the "dig" utility to check it... That is actually step #2, used after you ensure that your db (region) files are okay. There is no mention in the initial install, configuration, or how-to doc's of another included utility called "[named-checkconf]("http://manpages.ubuntu.com/manpages/trusty/man8/named-checkconf.8.html")". Use this utility FIRST to check and verify your region db files, to ensure there are no syntax errors, before you try to restart BIND9 with your changes. Go to [http://manpages.ubuntu.com/manpages/trusty/man8/named-checkconf.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/named-checkconf.8.html) to learn how to use that utility. Note that when you go to post your conf files here, use this utility with the "-x" option, and post the output from that, instead of posting your actual files. This replaces the specifics of your local network, for your protection. (That utility is priceless!!!)

Pointers in your main region file, can point to other region files ... or not. You can do it all in the main forward and reverse lookup files... and/or point to other files. It works like an "include" statement (include these other files and anything in this file) in code files. I do this to organize my regions, and as a best practice (keep myself in practice for enterprise networks). Separation or segmenting your regions in this manner-- Go to that region file to change or add a new resource to that region...

The initial setup does take some work. The payoff when configured is worth it. Note that this follows the advice from my previous post. Local DNS gives you greater detail than just using the "[hosts]("http://manpages.ubuntu.com/manpages/hardy/man5/hosts.5.html")" file on individual local machines, and gives you centralized administration of your resources. Meaning that you only have to go to one place on your network to manage all your network resources. For me, that fall-over point to make a decision between distributed hosts files or Local DNS is having to manage over 10 resources.

---

### Post by gardenair on 2015-12-26
hi,
     Well Thanks for your detail reply. I have review ubuntu page as well  "https://help.ubuntu.com/lts/serverguide/dns-configuration.html" regarding to DNS. The thing which I want to discuss is what is the meaning of " @" , "IN"   "A". for a layman how can u tell me.

The thing which I understand is @ sign is used for the servers names ?

"IN" is used for pointing  .....?
and "A" for the host in the domain (The computers on the network which want to resolve) ?

please elaborate it.

---

### Post by CharlesA on 2015-12-26
> **gardenair said:**
> hi,
     Well Thanks for your detail reply. I have review ubuntu page as well  "https://help.ubuntu.com/lts/serverguide/dns-configuration.html" regarding to DNS. The thing which I want to discuss is what is the meaning of " @" , "IN"   "A". for a layman how can u tell me.

The thing which I understand is @ sign is used for the servers names ?

"IN" is used for pointing  .....?
and "A" for the host in the domain (The computers on the network which want to resolve) ?

please elaborate it.

It depends on what you are looking at. See this example output from dig:

```
dig google.com @localhost

; <<>> DiG 9.8.1-P1 <<>> google.com @localhost
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43244
;; flags: qr rd ra; QUERY: 1, ANSWER: 8, AUTHORITY: 4, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             300     IN      A       70.186.24.54
google.com.             300     IN      A       70.186.24.55
google.com.             300     IN      A       70.186.24.56
google.com.             300     IN      A       70.186.24.57
google.com.             300     IN      A       70.186.24.58
google.com.             300     IN      A       70.186.24.59
google.com.             300     IN      A       70.186.24.52
google.com.             300     IN      A       70.186.24.53

;; AUTHORITY SECTION:
google.com.             172800  IN      NS      ns2.google.com.
google.com.             172800  IN      NS      ns3.google.com.
google.com.             172800  IN      NS      ns1.google.com.
google.com.             172800  IN      NS      ns4.google.com.

;; Query time: 129 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Dec 26 07:18:06 2015
;; MSG SIZE  rcvd: 228

```

All the A records are IP addresses that resolve to google.com.

---

### Post by darkod on 2015-12-26
The @ is not used exactly for server names. Unless I've got it wrong, you can consider the @ like being the domain name that the zone is for. For example you are setting up a zone for mydomain.com and the main record would be something like:
```
@   IN   A   11.22.33.44
```

That will make mydomain.com point to the IP of your webserver. So when a browser client wants to open [http://mydomain.com](http://mydomain.com) it would resolve to that IP.

A domain also needs specified at least one nameserver, by hostname, not IP. But you also need A record to link that nameserver with an IP. That would be:
```
@   IN   NS   ns1.mydomain.com.
ns1   IN   A   12.34.56.78
```

Is it little clearer now? Basically the @ is used only in the few basic records and after that you do not use it any more. You mainly use IN A to create A records, and IN CNAME for cname aliases.

---

### Post by SeijiSensei on 2015-12-26
The "@" usually appears in the "statement of authority" or SOA record at the top of a DNS zone file and refers to the entire domain.  "IN" indicates the record is of class "Internet" which constitutes essentially all records these days.  

```

@   IN SOA example.com. admin.example.com. (2015122601 43200 3600 86400 43200)

```
The fifth field provides the administrator's email address, in this case the equivalent of [email]admin@example.com[/email].  The remaining fields provide a serial number for this associated set of records and expiration information.  The serial number must be incremented if changes are made to the records.  This will inform secondary DNS servers that they must update their records as well.

Beyond that are five basic record types:

NS - provides the IP addresses of the servers registered as authoritative for the domain
```

     IN NS 10.10.10.10
     IN NS 10.10.10.11

```
If the record starts with a blank, it is considered to be associated with the record above it.  In this case if the NS record follows the SOA record, then the "@" representing the domain is implicitly associated with the NS record.

MX- "mail exchanger" record for the domain denoting the servers that accept mail for the domain with "priorities" to indicate which server is preferred
```

     IN MX 0 mail1.example.com.
     IN MX 5 mail2.example.com.

```
The priorities are ordinal.  Note that all names must end in a period which represents the "root" of the name service tree.

A - indicates the address associated with a hostname
```

hostname  IN A 10.10.10.100

```

CNAME - an alias for another hostname
```

hostname  IN CNAME www

```
Makes "hostname" an alias for "www".  Notice that I haven't specified the domain since it's implicit.  Also the name here does not end with a period since it is relative to the domain.

TXT - an arbitrary text string associated with the domain; used most often these days as part of the "[sender policy framework]("http://www.openspf.org/")" standard to designate outbound mail servers
```

     IN TXT  "v=spf1 a:mail1.example.com a:mail2.example.com ~all"

```

In some cases you may have multiple records for a single host.  For instance,
```

www    IN    A    10.10.10.10
       IN    MX   0 www.example.com.

```
This designates [www.example.com](www.example.com) as its own mail server even if the entire domain has a different MX record.  So mail for [email]someone@www.example.com[/email] would be sent there, while all other mail for [email]someone@example.com[/email] would be sent to the primary MX for the domain.

---

### Post by gardenair on 2015-12-26
I am so much thankful to all you for the detail replies.

```
;
; BIND data file for example.com
;
$**TTL    604800&#8203;**
@       IN      SOA     example.com. root.example.com. (
                              [B]2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL[/B]
        IN      A       192.168.1.10
```



I want to add some thing more which I have bold  in the above example. Normally these are numbering are constant in every DNS server. Are the vales are fix ? Suppose the value
 ```

**TTL** **604800&#8203;**
```Is it is Mile-sec values ? want are is Serial , Refresh,Expire,Negative Cache TTL ? Can we change the values according to our self  or these are fixed ?

2- Point there is a line in named.conf regarding to

```
recursion yes 
```

Please also en light on it  

Once again  thanks for guiding me.

---

### Post by CharlesA on 2015-12-26
That TTL is for seven days.

You can change the settings here, but most are already set for the recommended values. See here:
[http://serverfault.com/questions/69183/recommended-dns-soa-record-ttl-default](http://serverfault.com/questions/69183/recommended-dns-soa-record-ttl-default)

---

### Post by MAFoElffen on 2015-12-27
Just adding an explanation of the symbol "@" itself...
> Quoted from the docs:
@
; replace with the current value of $ORIGIN
 
; blank/space or tab in which case the last
; owner-name used or the value of $ORIGIN 
; (or its default value) is substituted
Summarized translation, it's a like using shorthand, a compiler symbolic or a variable ... used to substitute the last name used as an owner.

---

### Post by SeijiSensei on 2015-12-27
You can set any values you like for the expiration times.  If your server is under development, so that the records may be changing frequently, then choose smaller values.  Once it is stable you can increase the time-to-live figure.  All the values are in seconds.  86400 seconds = one day.

As for recursion, it concerns whether the server can be queried for domains outside of the ones for which it is authoritative.  You should use the allow-recursion{} directive to limit recusive queries to ones coming from within your local network.  Allowing random external users to make recursive queries against your server is generally a poor practice.  It can enable people to employ your server as a node in distributed denial-of-service attacks against other servers.  See [http://www.zytrax.com/books/dns/ch9/close.html](http://www.zytrax.com/books/dns/ch9/close.html) for details.

---

