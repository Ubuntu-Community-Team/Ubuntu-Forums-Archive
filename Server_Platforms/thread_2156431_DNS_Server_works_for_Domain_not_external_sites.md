---
title: "DNS Server works for Domain not external sites"
date: 2013-06-21
forum: Server Platforms
---

### Post by WilJenMM on 2013-06-21
I just set up my 2nd Ubuntu Server as a DNS server using bind.  My queries within the domain respond correctly.  When I try to query something external '[www.ubuntu.com/]("http://www.ubuntu.com/")' using my Windows box I receive the request could not find [www.ubuntu.com]("http://www.ubuntu.com").  When I do a NSLookup I get a response of server as unknown with the address of my DNS server.  With my working DNS server the nslookup provides both the correct name and IP of the DNS server.  When I go to my server I can ping externally etc.  I did notice that when I do a DIG instead of listing the Server as my local address, it is the address of my ISP's DNS server which I have listed as the second nameserver on my interface.  When I look at my working DNS server that field reflects the local IP.  All my zones pass the check (forward and reverse).  I do not have anything set in my named.conf.options file that would restrict recursion.  I have confirmed that Bind is running and listening on port 53.  What else do I need to look at?

---

### Post by SeijiSensei on 2013-06-21
Some ISPs intercept DNS requests, usually so they can show ads to people when they mistype a domain name.  In order for your server to resolve domains outside your own it needs to be able to connect directly with the root nameservers.  If the ISP grabs those requests, those requests will be diverted.

You could try installing **nmap**, then running 

```
sudo nmap -sU -p 53 a.root-servers.net
```

That returns this result for me:
```
Nmap scan report for a.root-servers.net (198.41.0.4)
Host is up (0.11s latency).
PORT   STATE         SERVICE
53/udp open|filtered domain

```

If the ISP is intercepting DNS requests, your best bet it to add a "[forwarders]("http://www.zytrax.com/books/dns/ch4/#forwarding")" directive that sends requests for hosts outside your domain to your ISP's nameservers.

---

### Post by newbie-user on 2013-06-23
You need to add forwarders in your named.conf.options file.
```
        forwarders {
                8.8.8.8;
                8.8.4.4;
        };

```
Your DNS server is only authoritative for your domain. It cannot resolve external domains on its own, so it needs to forward unknown DNS requests to external servers for name resolution.

---

### Post by SeijiSensei on 2013-06-23
> **newbie-user said:**
> You need to add forwarders in your named.conf.options file.
Your DNS server is only authoritative for your domain. It cannot resolve external domains on its own, so it needs to forward unknown DNS requests to external servers for name resolution.

No, it doesn't.  A DNS server communicates directly with the root nameservers to resolve names outside the domains for which it is authoritative.  I only use forwarders in rare situations like when I want to resolve names against some internal DNS server.  For instance, I have forwarding set up for one of my client's domains so that queries are sent to their internal nameserver over a VPN tunnel.  

In the OPs case he may need to use forwarders if the ISP intercepts port 53 traffic on remote servers.  That would make it impossible for his server to communicate directly with the roots.

---

### Post by WilJenMM on 2013-06-24
I installed nmap and ran as described.  I get basically the same output.  My concern is the first part of the output.

---

### Post by newbie-user on 2013-06-24
> **SeijiSensei said:**
> No, it doesn't.  A DNS server communicates directly with the root nameservers to resolve names outside the domains for which it is authoritative.  I only use forwarders in rare situations like when I want to resolve names against some internal DNS server.  For instance, I have forwarding set up for one of my client's domains so that queries are sent to their internal nameserver over a VPN tunnel.  

In the OPs case he may need to use forwarders if the ISP intercepts port 53 traffic on remote servers.  That would make it impossible for his server to communicate directly with the roots.

Ah, thanks for getting me straight on that. :)

---

### Post by newbie-user on 2013-06-24
> **WilJenMM said:**
> I installed nmap and ran as described.  I get basically the same output.  My concern is the first part of the output.

Check your /etc/hosts file and see if your hostname matches the contents of the file.

---

### Post by WilJenMM on 2013-06-24
That was the issue.  Typo.  The other issue turns out to be the firewall.  I now allow the server out on IP and it works.  When I limit it to UDP it fails.  I thought you only needed TCP for zone transfers, which I don't believe I am doing.  I would like to lock the server down as much as possible.  I also have noticed that sites hosted by Akamai respond on a hit and miss basis.

---

### Post by SeijiSensei on 2013-06-25
> **WilJenMM said:**
> When I limit it to UDP it fails.  I thought you only needed TCP for zone transfers, which I don't believe I am doing.

That's my understanding as well.  

> I would like to lock the server down as much as possible.

Letting your own server make outbound queries is not much of a risk.  As long as you allow reply traffic ("ESTABLISHED,RELATED" in iptables) you should be fine.  Bind9 has the occasional security problem, but Paul Vixie and company at ISC are quick to patch it, and the updates are distributed soon thereafter.  I never worry about outbound traffic on my servers.  I haven't had a server compromised in any way in about a decade now, and the last time it happened it was my own fault for not updating to fix a security hole in Apache 1.3.  Inbound traffic is a different story, of course.

---

### Post by WilJenMM on 2013-06-25
I reviewed a capture of ping's from my dns server.  I saw requests going to both my ISP and the root servers.  I have gone in and removed the forwarders.  Responses are better, yet a little slow.  I do have issues with sites hosted by Akamai.  I can ping a site (from a dns client) and it will time out.  I immediately try again and it responds.  This is primarily with the Akamai hosted sites.  Is there some additional configuration changes I can make on my end?

---

### Post by SeijiSensei on 2013-06-25
Can you post the contents of named.conf?

---

### Post by WilJenMM on 2013-06-27
$cat named.conf     Several lines of stock comments then three include lines of "/etc/bind/named.conf.options" "/etc/bind/named.conf.local" "/etc/bind/named.conf.default-zones"

---

### Post by SeijiSensei on 2013-06-27
But what is in the options{} section of the file?  That's what really matters.  I doubt it's just "stock comments."

---

### Post by newbie-user on 2013-06-27
The default named.conf is now just an "includes" file.  The options{} section has been moved to named.conf.options.

---

### Post by WilJenMM on 2013-06-27
do you mean the named.conf.options file?

---

### Post by WilJenMM on 2013-06-27
leaving out the commented items:  options { directory "/var/cache/bind";   dnssec-validation auto;  auth-nxdomain no; # conform to RFC1035     listen-on-v6 { none };      };     note all other lines in the file are commented out with the // including the forwarders section.

---

### Post by Doug S on 2013-06-27
> **WilJenMM said:**
> ...  I do not have anything set in my named.conf.options file that would restrict recursion.  ...Yes, but I think it's disabled by default, so you need to specifically allow it for your internal clients. Here is my file:```
doug@doug-64:~/config/bind$ cat named.conf.options
options {
        directory "/var/cache/bind";

        recursion yes;
        allow-recursion {any;};
        allow-query {any;}; // this is needed to override the default
        allow-transfer {"none"; }; // transfer will be allowed per zone below.

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

//      forwarders {
//              75.153.176.9;
//              75.153.176.1;
//      };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { none; };
};
```(and external DNS requests are not allowed, but via my iptables rules, instead of above.)

---

### Post by WilJenMM on 2013-07-01
ip tables rules?

---

### Post by SeijiSensei on 2013-07-01
> **WilJenMM said:**
> ip tables rules?

iptables is the method for writing firewall rules in Linux.  It is built into the kernel by default.

Here are a couple of rules for DNS; assume eth0 points to the Internet, and eth1 points to an internal network.

```

# allow UDP DNS queries on all interfaces
/sbin/iptables -A INPUT --p udp --dport 53 -j ACCEPT

# allow a TCP zone transfer to off-site my.backup.dns.server
/sbin/iptables -A INPUT -p tcp -i eth0 -s my.backup.dns.server --dport 53 -j ACCEPT
[additional rules for any other servers that need to back up zones from you

# block any other TCP traffic on port 53
/sbin/iptables -A INPUT -p tcp --dport 53 -j REJECT

```

The first rule allows both public and private clients to query your server on port 53.  Whether you are actually listening to port 53 on one or both interfaces, and whether you accept public queries, is controlled in named.conf.  

The next two rules cover TCP connections to your server which are used to transfer zone files.  If this computer is a master for a domain, then its slaves need to connect with it over TCP.  Depending on how many different backup servers you have, you might have multiple iptables rules with the name or IP address of each backup.  The last command adds ("-A") the final rule governing DNS to the INPUT chain that denies any other TCP connections to your computer's port 53. 

You could block external queries to the DNS server, but allow them from inside the local network, by replacing the first rule above with these:
```

# allow internal queries on eth1; block public queries on eth0
/sbin/iptables -A INPUT -p udp -i eth1 --dport 53 -j ACCEPT
/sbin/iptables -A INPUT -p udp -i eth0 --dport 53 -j REJECT

# allow internal zone transfers
/sbin/iptables -A INPUT -p tcp -i eth1 --dport 53 -j ACCEPT
[etc.]

```I also added a rule to allow TCP zone transfers on eth1 if the server has slaves within the local network.

You can also control access to your server with parameters like "listen-on {};" in named.conf.  That is a level 7 protocol in the OSI model, where the [application]("http://en.wikipedia.org/wiki/OSI_model#Layer_7:_application_layer") itself, in this case bind9, manages its relations with other computers.  Iptables operates at the "[network]("http://en.wikipedia.org/wiki/OSI_model#Layer_3:_network_layer")" level, level 3, because it screens packets based on their headers.

---

