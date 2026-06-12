---
title: "Best practice for pointing domain name to nameservers"
date: 2015-09-15
forum: Server Platforms
---

### Post by th.sigit on 2015-09-15
I have a question similar to [http://ubuntuforums.org/showthread.php?t=2061055](http://ubuntuforums.org/showthread.php?t=2061055), but I am looking for the best practices. 

Above thread asked and explained to create different Virtual Hosts for setting up multiple IP to different domain addresses. As a conclusion, I believe I can setup A record for each domain name pointing towards each Virtual Hosts, e.g.

example1.com IN A 192.168.1.1 
example2.com in A 192.168.1.2 
example3.com in A 192.168.1.3 

What if I want to do it differently? I want to create my own nameservers as such that:

ns1.example1.com IN 192.168.1.1
ns2.example1.com in 192.168.1.2
ns3.example1.com in 192.168.1.3

ns1.example2.com IN 192.168.1.1
ns2.example2.com in 192.168.1.2
ns3.example2.com in 192.168.1.3

ns1.example3.com IN 192.168.1.1
ns2.example3.com in 192.168.1.2
ns3.example3.com in 192.168.1.3

There are numerous articles explaining to use **bind **or edit /*etc/resolv.conf*, but I also read that it isn't wise to use own VPS (it is a very small one, I am using it for learning only) as DNS server and instead it's better using external DNS server. Suppose, my registrar provide free DNS server and I can simply pointing each domains onto above sets of configuration, is it enough to simply edit */etc/resolv.conf* and not using **bind**?

Or is it better to create

ns1.example1.com IN 192.168.1.1
ns2.example1.com in 192.168.1.2
ns3.example1.com in 192.168.1.3

and later point the nameservers of example1.com, example1.com, and example1.com to these (ns1.example1.com, ns2.example1.com, ns3.example1.com)

Sorry I have got a lot to learn and in the past I've used to learn by breaking things and fix it, but this time I am looking for best advices first.

Thanks,

Sigit

---

### Post by darkod on 2015-09-15
Lets separate things a little...

First important fact is whether you are talking about public domains or local private domains. If they are (real) public domains and you decide to use the provider DNS service, then you will be using its control panel to create all records. No need for your own nameserver or anything to do with /etc/resolv.conf. Just by looking up the domain it will use the nameservers specified, in this case the provider nameservers.

The recommendation to use public DNS is more from a point of view of production websites and that you can't allow sites to go down if your nameserver gets messed up. If you are using these domains only to learn right now, it is enough to play around with your own nameserver and learn things. Later you can decide if you want to continue with your nameserver or switch to using public ones.

There is no need to create ns1/ns2.exampleX.com for each domain. You create only two (or only one to start with and learn) nameserver, for example ns1.example1.com. On that nameserver you will configure different zones for example1.com, exampl2.com, etc. Nameserver serves many zones if needed. In such case in the registrar control panel (where you have the domains registered), you will configure that the nameserver(s) to use is ns1.example1.com (for all domains the same nameserver). It will serve all zones.

Whether it's better to use your own or public DNS is not easy to answer. If you use public, the only thing learning is how to create records on it, which is not much. If you use your own, you learn how to configure and manage bind, which is good experience. But from a point of view of production systems, website availability, etc, using your own nameserver while still not having much experience is risky. If you need 100% availability. That's why best practice is having a minimum of two nameserver. If one fails, the other one will still be serving requests and the websites don't go down.

---

### Post by th.sigit on 2015-09-15
Hi Darko, 

thanks for bearing with me with my ignorance. I spent hours after reading your post, try to configure things myself while looking at some information I might be missing. Maybe I had made something which is so apparent becoming so problematic, simply because of some basic things that I do not really understand.

In my case, I have several domain names, from several domain registrars. On one of my domain registrar, e.g. *domainregistrar.com*, I set the  nameservers to *ns1.domainregistrar.com*, *ns2.domainregistrar.com* and so  on, utilizing their free DNS service. There, from registrar's domain control panel, I pointed the domain names  using **A** record to my shared cpanel hosting (it is a reseller account  with its own dedicated IP).

This works well. I don't know if it is a  good practice, but it is working.

I can apply the same method to point those domain names above to my VPS (using **A** record instead of **NS** record).

Unfortunately for me, I have one domain (*.so*) registered on another domain registrar, and either *that domain registrar* or *.so* TLD doesn't provide me much control to zone files but nameservers. Therefore, I can not point this *.so* domain to my VPS, because I can not change its **A** record (only **NS** records). At this point, I have the nameservers of my IP (this VPS has four IPs). So how can I do that?

In the past, I managed to add nameservers to my desktop, and access this desktop from a domain address via browser. My desktop had dynamic IP, I was using a service from **no-ip.org**. I forgot how to do that, it was probably handled by the modem. Alternatively, I had to install something to my desktop, and this program will continuously pinging **no-ip.org** to update the nameservers they provided. However the situation is much different now, VPS has its own IP so I believe I do not need additional program to give them nameservers.

What would I do? 

**a**. Edit /etc/hosts and list each IP for each nameserver? 

192.168.1.1 ns1.example.com
192.168.1.2 ns2.example.com

**b**. Or follow this article: [http://www.cyberciti.biz/tips/linux-how-to-setup-as-dns-client.html](http://www.cyberciti.biz/tips/linux-how-to-setup-as-dns-client.html), edit /etc/resolv.conf and list different IPs for entry list nameserver?

nameserver 192.168.1.1
nameserver 192.168.1.2

(I do not really know what /etc/resolv.conf is, that's why I asked in this forum)

**c**. Or do I need another software such as **bind**?

Thank you in advance for your help.

---

### Post by darkod on 2015-09-15
First, lets discuss the dynamic dns clients. You are right, in this case your VPS has a static public IP and there is no need to use any type of DDNS client (like ddns, noip, etc). Otherwise just for information, ubuntu has packages for them and you can use them if you have dynamic IP. But that is never a very good solution for a public server, if you can have a static IP.

If that is the case with your domains, here is a suggestion: the ones that have the option to use registrars CP to create records, use it right now. The .so domain that has no option like that, configure your own bind and use it as nameserver for the .so, at the same time learning it.

Doing a basic bind is actually very easy. You need to edit one existing file and create one new file that will be the database with the records for the domain. You can read more details here, starting with the installation: [https://help.ubuntu.com/lts/serverguide/dns-installation.html](https://help.ubuntu.com/lts/serverguide/dns-installation.html)

First install the packages:
```
sudo apt-get install bind9 dnsutils
```

Then edit the /etc/bind/named.conf.local and add this zone definition (using your domain name instead of domain.so of course):
```
zone "domain.so" {
   type master;
   file "/etc/bind/db.domain.so";
};
```

It is good practice to name the db files according to domain name, that way you can find and edit them more easily in future, even if the bind serves many domains.

After that, create the file /etc/bind/db.domain.so and put this data in (lets assume your VPS public IP is 1.2.3.4 and ns1.example.com is the FQDN of the VPS):
```
;
; BIND data file for domain.so
;
$TTL 3600
@   IN   SOA   domain.so. admin.domain.so. (
                    2015091501         ; Serial
                    604800               ; Refresh
                    86400                 ; Retry
                    2419200              ; Expire
                    604800 )             ; Negative Cache TTL

@   IN   NS   ns1.example.com.
@   IN   A   1.2.3.4
www   IN   A   1.2.3.4
```

After that you restart the bind service:
```
sudo service bind9 restart
```

And that's it. In the above example I assumed ns1 will belong to one of the other domains (for example if you have a primary domain of interest). In such case you also need to create A record ns1 pointing to the public IP. In that case your VPS bind will be ns1.example.com (depending which domain you use).

If on the other hand you want ns1 to be in the domain.so domain, you also need one more A record in the above file:
```
ns1   IN   A   1.2.3.4
```

Try that and report how it went or if you have any questions.

As for your above questions. In ubuntu /etc/resolv.conf contains the nameservers that machine will use but it is dynamic and created from the network settings (either getting the nameservers from dhcp or from the manual network settings). Usually you don't edit it manually. If you use the above config you don't need to modify resolv.conf anyway.

The /etc/hosts also contains host definitions that the local machine will use. Putting into there instead of running a nameserver will work for a few local machines, but not for anyone else in the world. So it's not really a solution to dns.

---

### Post by darkod on 2015-09-15
I forgot to mention in the previous post.

If you have a firewall running on the VPS (and you should, because it's a public server), you will need to allow incoming TCP and UDP traffic on port 53 if you want to use your VPS as nameserver. That port is designated for dns.

---

### Post by MAFoElffen on 2015-09-15
Just a note for FYI to both the OP and Darko. 


If wanting to statically point to DNS... Using nameserver xxx.xxx.xxx.xxx in /etc/networks/interfaces works for just so many, is limited and sometimes fails. Editing/using etc/resolved.conf... as the OP stated, was oldschool, is changed/deprecated now. etc/resolv.conf is dynamically built, and overwritten at boot from other sources now.

Current static dns is now mainly derived from /etc/resolvconf/resolv.conf. That is were I edit mine on my primary/secondary dns server hosts own machines' static network settings, for their upstream dns servers... That loads on them as they boot and before Bind9 loads.
[http://manpages.ubuntu.com/manpages/precise/man8/resolvconf.8.html](http://manpages.ubuntu.com/manpages/precise/man8/resolvconf.8.html)
You  still need to say that in Bind9 like Darko stated... for Bind9. But as a service, Bind9 does not affect the settings of it's own host's environment. Does that make sense?

---

### Post by th.sigit on 2015-09-16
@Darko:
You are awesome! Thank you for explaining things in detail. Now I know which direction I need to go.

@MAFoElffen:
Kudos to you too! I will spend the next few hours configuring things ... **in my mind**, first :) Now I have the better idea what to do.

Thank you all, your helps are appreciated.

Sigit

---

